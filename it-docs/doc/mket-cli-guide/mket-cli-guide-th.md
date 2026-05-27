---
icon: calendar-lines-pen
---

# mket cli Guide (TH)

| รายการ          | รายละเอียด      |
| --------------- | --------------- |
| เวอร์ชันเอกสาร  | 1.0             |
| วันที่ออกเอกสาร | 14 พฤษภาคม 2026 |

`mket-cli` คือเครื่องมือแบบ Command-Line สำหรับ generate ไฟล์รายงาน `MKET_PF_SUMMARY_T1_YYYYMMDD.txt` ตาม spec ที่ได้รับ แล้ววางลงใน output directory ของลูกค้า (เช่น network share `\\mbketh\Reportmail\PF`)

{% hint style="info" %}
**ทำไมต้องรันที่เครื่องลูกค้า** เครื่องมือนี้ออกแบบให้รันแบบ **one-shot** (รันแล้วจบ ไม่มี daemon loop) ผ่าน Task Scheduler บน Windows หรือ cron บน Linux ที่เครื่องลูกค้า เนื่องจาก Level11 server container ไม่สามารถเขียนไฟล์ลง network share ของลูกค้าได้โดยตรง
{% endhint %}

## ภาพรวมการทำงาน

เมื่อ `mket-cli` ถูกรันในแต่ละครั้ง จะทำงานตามลำดับดังนี้:

{% stepper %}
{% step %}
### คำนวณ trigger date

สิ้นเดือนก่อนหน้า + `run_days_after_eom` วันทำการ (ข้ามวันเสาร์–อาทิตย์ และวันหยุดจาก calendar ที่ระบุ)
{% endstep %}

{% step %}
### ตรวจสอบว่าตรงวัน trigger หรือไม่

* ถ้า **ตรง** trigger → login → ดึงไฟล์ผ่าน API `/api/public/v1/report.nav.exportMket` → เขียนลง `output_dir`
* ถ้า **ไม่ตรง** trigger → จบการทำงานเงียบ ๆ (ยกเว้นเปิด `catchup: true` และไฟล์ของ value date นั้นยังไม่มี)
{% endstep %}
{% endstepper %}

## ก่อนเริ่ม

ตรวจสอบสิ่งต่อไปนี้ให้พร้อมก่อนติดตั้ง:

* ไฟล์ติดตั้ง — `mket-cli.exe` (Windows) หรือ `mket-cli` (Linux)
* ไฟล์ตัวอย่าง config — `config.example.yaml`
* บัญชีผู้ใช้ Level11 ที่มีสิทธิ์ `report.*` และ `masterfile.other.*`
* สิทธิ์เขียนไฟล์ลง output directory / network share ปลายทาง

***

## 1. ติดตั้งที่เครื่องลูกค้า

{% tabs %}
{% tab title="Windows" %}
{% stepper %}
{% step %}
### สร้างโฟลเดอร์

เช่น `C:\mket-cli\`
{% endstep %}

{% step %}
### Copy `dist/mket-cli.exe`

Copy ไปวางในโฟลเดอร์
{% endstep %}

{% step %}
### Copy `cmd/mket-cli/config.example.yaml`

Copy ไปวางในโฟลเดอร์เดียวกัน แล้วเปลี่ยนชื่อเป็น `config.yaml`
{% endstep %}

{% step %}
### แก้ไขค่าใน `config.yaml`

แก้ไขค่าใน `config.yaml` ตามต้องการ (ดูหัวข้อ [2. การตั้งค่า Config](mket-cli-guide-th.md#2-kaartangkha-config))
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Linux" %}
{% stepper %}
{% step %}
### สร้างโฟลเดอร์

```bash
sudo mkdir -p /opt/mket-cli
```
{% endstep %}

{% step %}
### Copy `dist/mket-cli`

```bash
sudo cp dist/mket-cli /opt/mket-cli/
```
{% endstep %}

{% step %}
### Copy `cmd/mket-cli/config.example.yaml`

```bash
sudo cp cmd/mket-cli/config.example.yaml /opt/mket-cli/config.yaml
```
{% endstep %}

{% step %}
### ตั้งค่า permission ให้ไฟล์รันได้

```bash
sudo chmod +x /opt/mket-cli/mket-cli
```
{% endstep %}

{% step %}
### แก้ไขค่าใน `/opt/mket-cli/config.yaml`

จากนั้นแก้ไขค่าใน `/opt/mket-cli/config.yaml` ตามต้องการ (ดูหัวข้อ [2. การตั้งค่า Config](mket-cli-guide-th.md#2-kaartangkha-config))
{% endstep %}
{% endstepper %}
{% endtab %}
{% endtabs %}

***

## 2. การตั้งค่า Config

ดูค่าตั้งต้นทั้งหมดได้จากไฟล์ `config.example.yaml` โดย field ที่สำคัญมีดังนี้:

<table><thead><tr><th>Field</th><th width="115" align="center">จำเป็น</th><th width="393">คำอธิบาย</th></tr></thead><tbody><tr><td><code>api_base_url</code></td><td align="center">✅</td><td>URL ของ Level11 server (ห้ามใส่ <code>/</code> ปิดท้าย)</td></tr><tr><td><code>auth_type</code></td><td align="center">—</td><td><code>"password"</code> (ค่า default) หรือ <code>"token"</code> (ยังไม่รองรับฝั่ง server)</td></tr><tr><td><code>username</code> / <code>password</code></td><td align="center">✅</td><td>ต้องเป็น user ที่มีสิทธิ์ <code>report.*</code> + <code>masterfile.other.*</code> — รองรับการอ้างอิงผ่าน <code>${ENV_VAR}</code></td></tr><tr><td><code>calendar_codes</code></td><td align="center">✅</td><td>เช่น <code>["TH"]</code> — ระบบจะรวมวันหยุดแบบ distinct จากทุก code ที่ระบุ</td></tr><tr><td><code>run_days_after_eom</code></td><td align="center">✅</td><td>จำนวนวันทำการหลังสิ้นเดือนที่จะ trigger (<code>1</code> = วันทำการแรกของเดือนถัดไป) <br>// T+N วันทำการหลังสิ้นเดือนที่จะ trigger</td></tr><tr><td><code>output_dir</code></td><td align="center">✅</td><td>ตำแหน่งวางไฟล์ผลลัพธ์ — ดูหัวข้อ <a href="mket-cli-guide-th.md#output-path">Output path</a></td></tr><tr><td><code>filename_pattern</code></td><td align="center">—</td><td>ค่า default คือ <code>MKET_PF_SUMMARY_T1_${DATE}.txt</code> รองรับ <code>${DATE}</code> และ <code>${DATE:&#x3C;go-layout>}</code></td></tr><tr><td><code>timezone</code></td><td align="center">—</td><td>IANA time zone เช่น <code>Asia/Bangkok</code> (default)<br><strong>ตั้งให้ชัดเจน</strong> อย่าพึ่ง locale ของเครื่อง</td></tr><tr><td><code>catchup</code></td><td align="center">—</td><td><code>true</code> = ถ้าวันนี้เลย trigger date ไปแล้วและไฟล์ของ value date นั้นยังไม่มี ให้ generate ย้อนหลัง</td></tr><tr><td><code>log_file</code></td><td align="center">—</td><td>path ของ log file (relative อิงจาก [working dir] working directory)</td></tr><tr><td><code>timeout_seconds</code></td><td align="center">—</td><td>HTTP timeout หน่วยวินาที (default <code>60</code>)</td></tr></tbody></table>



{% hint style="warning" %}
**ตั้งค่า `timezone` ให้ชัดเจนเสมอ** อย่าพึ่งพา locale ของเครื่อง — หากไม่ระบุ `timezone` หรือเครื่องตั้งเป็น UTC อาจทำให้ trigger date คลาดเคลื่อนไป 1 วัน
{% endhint %}

### Output path

บน **Windows** รองรับ 3 รูปแบบ:

```yaml
output_dir: "\\\\mbketh\\Reportmail\\PF"   # UNC + escape backslash
output_dir: '\\mbketh\Reportmail\PF'       # UNC + single quote
output_dir: "C:/mket-out"                  # drive + forward slash
```

บน **Linux** ใช้ absolute path ตามปกติ เช่น `/mnt/mket-out`

### Credential

{% hint style="danger" %}
**ห้ามใส่ password เป็น plain text ในไฟล์ YAML** ให้ใช้ `${ENV_VAR}` ในไฟล์ config แล้วตั้งค่า env (environment variable) ที่ Task Scheduler / systemd / cron แทน
{% endhint %}

{% tabs %}
{% tab title="Windows" %}
ตั้งค่า environment variable ระดับ Machine ผ่าน PowerShell:

```powershell
[Environment]::SetEnvironmentVariable("MKET_CLI_PASSWORD", "xxxx", "Machine")
```
{% endtab %}

{% tab title="Linux" %}
ใส่ค่าใน systemd unit ผ่าน `Environment=` หรือใช้ wrapper script (ดูตัวอย่างการตั้ง cron)
{% endtab %}
{% endtabs %}

***

## 3. CLI flags

```
mket-cli [-config PATH] [-date YYYY-MM-DD] [-dry-run] [-verbose]
```

รัน `mket-cli -help` จะแสดงผลดังนี้:

```
Usage of mket-cli:
  -config string
        Path to YAML config file (default "config.yaml")
  -date string
        Override value date (YYYY-MM-DD). If set, skip the trigger-day check
  -dry-run
        Do everything except the final API call and file write
  -verbose
        Verbose logging
```

| Flag       | ค่า Default   | ใช้เมื่อ                                                                     |
| ---------- | ------------- | ---------------------------------------------------------------------------- |
| `-config`  | `config.yaml` | ระบุ path ของไฟล์ config                                                     |
| `-date`    | —             | บังคับ value date (ข้ามการเช็ค trigger-day) — สำหรับ rerun ย้อนหลังหรือทดสอบ |
| `-dry-run` | `false`       | ทำทุกขั้นตอนยกเว้นการ call export API จริงและการเขียนไฟล์                    |
| `-verbose` | `false`       | แสดง log แบบละเอียด                                                          |

{% hint style="info" %}
**Exit code** `0` = ทำงานปกติ (รวมถึงกรณีที่ไม่ใช่วัน trigger) — `1` = เมื่อเกิด error
{% endhint %}

***

## 4. Smoke test ก่อนตั้ง schedule

ก่อนตั้ง schedule จริง แนะนำให้ทดสอบด้วย `-dry-run` ก่อน:

{% tabs %}
{% tab title="Windows" %}
```bash
C:\mket-cli\mket-cli.exe -config C:\mket-cli\config.yaml -verbose -dry-run
```
{% endtab %}

{% tab title="Linux" %}
```bash
/opt/mket-cli/mket-cli -config /opt/mket-cli/config.yaml -verbose -dry-run
```
{% endtab %}
{% endtabs %}

ตรวจสอบจาก log ว่า:

* login ผ่าน
* ดึงข้อมูลวันหยุด (holiday) ได้
* คำนวณ trigger date ถูกต้อง

จากนั้นทดสอบรันจริงโดยบังคับ value date:

```bash
mket-cli -config config.yaml -date 2026-01-31 -verbose
```

แล้วเปิดดูไฟล์ที่ `output_dir` เพื่อยืนยันว่าเขียนสำเร็จ

***

## 5. การแก้ปัญหา (Troubleshooting)

| อาการ                                | สาเหตุที่พบบ่อยและวิธีแก้                                                                                                     |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **Exit 0 แต่ไม่มีไฟล์**              | ไม่ใช่วัน trigger — ตรวจสอบด้วย `-verbose -date YYYY-MM-DD`                                                                   |
| **`auth failed`**                    | username/password ผิด หรือ environment variable ไม่ถูก expand (บน Windows ต้องตั้งระดับ Machine ไม่ใช่ User session ปัจจุบัน) |
| **`permission denied` ขณะเขียน UNC** | Task รันด้วย account ที่ไม่มีสิทธิ์เข้า share — เปลี่ยน "Run as" ใน Task Scheduler                                            |
| **Trigger date เพี้ยนไป 1 วัน**      | ไม่ได้ตั้ง `timezone` หรือเครื่องเป็น UTC — ระบุ `timezone: "Asia/Bangkok"` ให้ชัดเจน                                         |
| **Missed run (เครื่องดับ)**          | เปิด `catchup: true` ร่วมกับตัวเลือก "Run as soon as possible after missed start" ใน Task Scheduler                           |
| **`holidays empty`**                 | `calendar_codes` ผิด หรือ user ไม่มีสิทธิ์ `masterfile.other.*`                                                               |

{% hint style="success" %}
หากตรวจสอบตามตารางด้านบนแล้วยังไม่สามารถแก้ไขได้ กรุณาติดต่อทีมงาน Level11 พร้อมแนบ log file (รันด้วย `-verbose`) เพื่อให้ตรวจสอบได้รวดเร็วยิ่งขึ้น
{% endhint %}

