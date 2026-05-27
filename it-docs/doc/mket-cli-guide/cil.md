---
hidden: true
---

# cil

## mket-cli

CLI สำหรับ generate ไฟล์รายงาน `MKET_PF_SUMMARY_T1_YYYYMMDD.txt` ตาม spec MSTH แล้ววางลง output directory ของลูกค้า (เช่น network share `\\mbketh\Reportmail\PF`)

ออกแบบให้รันแบบ **one-shot** (รันแล้วจบ ไม่มี daemon loop) ผ่าน Task Scheduler บน Windows หรือ cron บน Linux ที่เครื่องลูกค้า — เพราะ Level11 server container เขียนไฟล์ลง share ของลูกค้าโดยตรงไม่ได้

หลักการทำงานสั้นๆ:

1. คำนวณ trigger date = สิ้นเดือนก่อน + `run_days_after_eom` วันทำการ (ข้ามเสาร์-อาทิตย์และวันหยุดจาก calendar ที่ระบุ)
2. ถ้าวันนี้ตรง trigger → login → ดึงไฟล์ผ่าน `/api/public/v1/report.nav.exportMket` → เขียนลง `output_dir`
3. ถ้าไม่ตรง trigger → exit เงียบๆ (ยกเว้นเปิด `catchup: true` แล้วไฟล์ value date นั้นยังไม่มี)

### 1. ติดตั้งที่เครื่องลูกค้า

#### Windows

1. สร้างโฟลเดอร์ เช่น `C:\mket-cli\`
2. Copy `dist/mket-cli.exe` ไปวาง
3. Copy `cmd/mket-cli/config.example.yaml` ไปวางในโฟลเดอร์เดียวกัน เปลี่ยนชื่อเป็น `config.yaml`
4. แก้ค่า config ตามต้องการ

#### Linux

```bash
sudo mkdir -p /opt/mket-cli
sudo cp dist/mket-cli /opt/mket-cli/
sudo cp cmd/mket-cli/config.example.yaml /opt/mket-cli/config.yaml
sudo chmod +x /opt/mket-cli/mket-cli
```

***

### 2. Config

ดูตัวเต็มที่ `config.example.yaml` field สำคัญ:

| Field                   | Required | คำอธิบาย                                                                              |
| ----------------------- | -------- | ------------------------------------------------------------------------------------- |
| `api_base_url`          | ✅        | URL Level11 server (ไม่ใส่ `/` ปิดท้าย)                                               |
| `auth_type`             | —        | `"password"` (default) หรือ `"token"` (ยังไม่รองรับฝั่ง server)                       |
| `username` / `password` | ✅\*      | ต้องเป็น user ที่มี perm `report.*` + `masterfile.other.*` — รองรับ `${ENV_VAR}`      |
| `calendar_codes`        | ✅        | เช่น `["TH"]` — รวม holiday แบบ distinct จากทุก code                                  |
| `run_days_after_eom`    | ✅        | T+N วันทำการหลังสิ้นเดือนที่จะ trigger (1 = วันทำการแรกของเดือนถัดไป)                 |
| `output_dir`            | ✅        | ดู Output path                                                                        |
| `filename_pattern`      | —        | default `MKET_PF_SUMMARY_T1_${DATE}.txt` รองรับ `${DATE}` และ `${DATE:<go-layout>}`   |
| `timezone`              | —        | IANA เช่น `Asia/Bangkok` (default) — **ตั้งให้ชัดเจน** อย่าพึ่ง locale ของเครื่อง     |
| `catchup`               | —        | `true` = ถ้าวันนี้เลย trigger ไปแล้วและไฟล์ value date นั้นยังไม่มี ให้ generate ย้อน |
| `log_file`              | —        | path log file (relative อิง working dir)                                              |
| `timeout_seconds`       | —        | HTTP timeout, default 60                                                              |

#### Output path

Windows รับได้ 3 แบบ:

```yaml
output_dir: "\\\\mbketh\\Reportmail\\PF"   # UNC + escape backslash
output_dir: '\\mbketh\Reportmail\PF'       # UNC + single quote
output_dir: "C:/mket-out"                  # drive + forward slash
```

Linux ใช้ absolute path ปกติ เช่น `/mnt/mket-out`

#### Credential

อย่าใส่ password แบบ plain text ใน yaml — ใช้ `${ENV_VAR}` แล้วตั้ง env ที่ Task Scheduler / systemd / cron แทน

**Windows (PowerShell, ตั้งระดับ Machine):**

```powershell
[Environment]::SetEnvironmentVariable("MKET_CLI_PASSWORD", "xxxx", "Machine")
```

**Linux:** ใส่ใน systemd unit `Environment=` หรือ wrapper script (ดูตัวอย่าง cron ด้านล่าง)

***

### 3. CLI flags

```
mket-cli [-config PATH] [-date YYYY-MM-DD] [-dry-run] [-verbose]
```

รัน `mket-cli -help` จะได้:

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

| Flag       | Default       | ใช้เมื่อ                                                                 |
| ---------- | ------------- | ------------------------------------------------------------------------ |
| `-config`  | `config.yaml` | path config file                                                         |
| `-date`    | —             | force value date (skip trigger-day check) — สำหรับ rerun ย้อนหลัง / test |
| `-dry-run` | false         | ทำทุกขั้นยกเว้น call export API จริง + เขียนไฟล์                         |
| `-verbose` | false         | log ละเอียด                                                              |

Exit code: `0` ปกติ (รวมถึงกรณีไม่ใช่วัน trigger), `1` เมื่อมี error

***

### 4. Smoke test ก่อน schedule

```bash
# Windows
C:\mket-cli\mket-cli.exe -config C:\mket-cli\config.yaml -verbose -dry-run

# Linux
/opt/mket-cli/mket-cli -config /opt/mket-cli/config.yaml -verbose -dry-run
```

ตรวจ log ว่า login ผ่าน, holiday ดึงได้, trigger date คำนวณถูก แล้วลองรันจริงโดย force date:

```bash
mket-cli -config config.yaml -date 2026-01-31 -verbose
```

เปิดดูไฟล์ที่ `output_dir` ว่าเขียนสำเร็จ

***

### 5. Troubleshoot

| อาการ                         | สาเหตุที่พบบ่อย                                                                                                  |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Exit 0 แต่ไม่มีไฟล์           | ไม่ใช่วัน trigger — เช็คด้วย `-verbose -date YYYY-MM-DD`                                                         |
| `auth failed`                 | username/password ผิด หรือ env var ไม่ถูก expand (PowerShell ต้องตั้งระดับ Machine ไม่ใช่ User session ปัจจุบัน) |
| `permission denied` เขียน UNC | Task รันใน account ที่ไม่มีสิทธิ์ share → เปลี่ยน "Run as" ใน Task Scheduler                                     |
| Trigger date เพี้ยน 1 วัน     | `timezone` ไม่ได้ตั้ง / เครื่องเป็น UTC → ระบุ `timezone: "Asia/Bangkok"` ชัดๆ                                   |
| Missed run (เครื่องดับ)       | เปิด `catchup: true` + Task Scheduler "Run as soon as possible after missed start"                               |
| `holidays empty`              | `calendar_codes` ผิด หรือ user ไม่มี perm `masterfile.other.*`                                                   |
