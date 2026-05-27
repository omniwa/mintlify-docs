---
icon: square-arrow-right
---

# Doc for IT (TH)

**เอกสารประกอบการนำเข้าข้อมูลและ Deploy ระบบ**

***

## Document Control (ข้อมูลควบคุมเอกสาร)

| รายการ             | รายละเอียด                                                        |
| ------------------ | ----------------------------------------------------------------- |
| **Document Title** | Pre-Injected Seed Data — IT Audit & Deployment Reference          |
| **Document ID**    | L11-IT-DEPLOY-001                                                 |
| **Project**        | poc-msth-deploy (Level 11)                                        |
| **Version**        | 1.0                                                               |
| **Status**         | Released                                                          |
| **Issue Date**     | 12 May 2026                                                       |
| **Owner**          | Development Team                                                  |
| **Audience**       | IT Department / Deployment Engineers / Internal Control Reviewers |
| **Classification** | Internal Use Only                                                 |

### Revision History (ประวัติการแก้ไข)

| Version | Date        | Author           | Change Description                         |
| ------- | ----------- | ---------------- | ------------------------------------------ |
| 1.0     | 12 May 2026 | Development Team | Initial release for IT deployment hand-off |

***

## 1. Purpose and Scope (วัตถุประสงค์และขอบเขต)

### 1.1 Purpose

เอกสารฉบับนี้จัดทำขึ้นเพื่อ:

* ระบุรายการข้อมูลเริ่มต้น (seed data) ทั้งหมดที่ถูกฉีดเข้าฐานข้อมูลโดยไฟล์ SQL ในชุด deployment
* ใช้ประกอบการนำเข้าข้อมูลและ deploy ระบบโดยฝ่าย IT
* ใช้ในการตรวจสอบและประเมินผลโดยทีม Internal Control / Audit
* ยืนยัน reference data, default codes, master records และ system accounts ที่จะปรากฏอยู่ใน first boot ก่อนจะมี business transaction ใด ๆ เกิดขึ้น

### 1.2 Scope

ครอบคลุมไฟล์ SQL จำนวน 15 ไฟล์ ที่อยู่ใน deployment folder ของระบบ `poc-msth-deploy` ทั้งส่วน DDL (schema) และ DML (data) รวมข้อมูลทั้งสิ้น **6,838 แถว** ใน **24 ตาราง**

{% hint style="info" %}
เอกสารนี้จัดทำจากการ static review ของไฟล์ SQL เท่านั้น **ไม่มีการเชื่อมต่อไปยังฐานข้อมูลที่ทำงานอยู่จริง**
{% endhint %}

***

## 2. References (เอกสารอ้างอิง)

| #   | Document                         |
| --- | -------------------------------- |
| R-1 | SQL deployment folder (15 files) |

***

## 3. Definitions and Abbreviations (คำจำกัดความและคำย่อ)

| Term      | Meaning                                                        |
| --------- | -------------------------------------------------------------- |
| DDL       | Data Definition Language — คำสั่งสร้าง/แก้ไขโครงสร้างฐานข้อมูล |
| DML       | Data Manipulation Language — คำสั่งจัดการข้อมูลในตาราง         |
| Seed Data | ข้อมูลตั้งต้นที่จำเป็นต่อการเริ่มทำงานของระบบ                  |
| COA       | Chart of Accounts (ผังบัญชี)                                   |
| NAV       | Net Asset Value                                                |
| EOD       | End-of-Day                                                     |
| FX        | Foreign Exchange                                               |
| VAT       | Value Added Tax                                                |
| WHT       | Withholding Tax                                                |
| PVD       | Provident Fund                                                 |
| BIC       | Bank Identifier Code                                           |

***

## 4. Deployment Order (ลำดับการ Deploy)

ไฟล์ SQL ทั้งหมดถูกประมวลผลเรียงตามลำดับชื่อไฟล์ ตัวเลขนำหน้า (`001-`, `010-`, ..., `999-`) เป็นตัวกำหนดลำดับ

| #  | File                     | Type            | Purpose                                       |
| -- | ------------------------ | --------------- | --------------------------------------------- |
| 0  | `table.sql`              | DDL (schema)    | สร้าง 226 tables + 1 seed (`roles`)           |
| 1  | `001-init.sql`           | DML (seed)      | System users, configs, COA, transaction types |
| 2  | `010-countries.sql`      | DML (seed)      | ISO country master                            |
| 3  | `011-calendars.sql`      | DML (seed)      | Business calendars + holidays                 |
| 4  | `012-currencies.sql`     | DML (seed)      | Currencies + currency pairs                   |
| 5  | `013-tenors.sql`         | DML (seed)      | Tenor buckets                                 |
| 6  | `020-sectors.sql`        | DML (seed)      | Industry sectors                              |
| 7  | `030-companies.sql`      | DML (seed)      | Company master                                |
| 8  | `040-custodies.sql`      | DML (seed)      | Custodian master                              |
| 9  | `050-issuers.sql`        | DML (seed)      | Issuer master                                 |
| 10 | `060-formulars.sql`      | DML (seed)      | Yield/coupon formulas                         |
| 11 | `070-guarantors.sql`     | DML (seed)      | Guarantor master                              |
| 12 | `080-counterparties.sql` | DML (seed)      | Counterparty master                           |
| 13 | `090-rp.sql`             | DML (seed)      | Regulatory reporting mappings                 |
| 14 | `999-finish.sql`         | DDL (post-load) | Reset sequences, build notify triggers        |

{% hint style="warning" %}
ห้ามสลับลำดับการรันไฟล์ เพราะตารางบางตารางมี foreign-key อ้างอิงข้ามไฟล์
{% endhint %}

***

## 5. Schema File — `table.sql`

### 5.1 Overview

* **Statements:** 226 `CREATE TABLE` ครอบคลุม application data model ทั้งระบบ (sessions, users, roles, employees, portfolios, securities, holdings, accounting/GL, compliance rules, audit-trail tables ที่ขึ้นต้นด้วย `log_*` ฯลฯ)

### 5.2 Embedded Seed Inside DDL

* **Table `roles`** — แทรก 1 แถว ด้วย `ON CONFLICT DO NOTHING`:
  * `('super_admin', '{*}')` — full-permission role สำหรับ bootstrap admin user

### 5.3 Database Extension

* `pgcrypto` — เปิดใช้งานเพื่อสร้าง UUID สำหรับตาราง `roles`, `employees`, `file_storages` ฯลฯ

### 5.4 Triggers / Functions

ไม่มีการสร้าง trigger ใน `table.sql` — mutation-notification triggers ทั้งหมดถูกสร้างภายหลังโดย `999-finish.sql`

***

## 6. Bootstrap Seed — `001-init.sql`

ไฟล์นี้บรรจุข้อมูลที่ระบบจำเป็นต้องใช้เพื่อ start ตั้งแต่ admin login, system configuration, chart of accounts จนถึง enumeration ของ transaction type และ security class

### 6.1 Table: `users` — 1 row

Bootstrap administrator (credential แรกในระบบ)

| id | username | email           | role         | active\_flag | status |
| -- | -------- | --------------- | ------------ | ------------ | ------ |
| 1  | admin    | admin@admin.com | super\_admin | A            | 1      |

* Password เก็บเป็น Argon2id hash (`argon2id$2$65536$4$16$...`)
* `password_updated_at = NULL` — ระบบจะบังคับเปลี่ยน password ตอน first login
* **Audit attention:** ต้องเปลี่ยน password และตรวจสอบ first-login activity ของ user นี้

### 6.2 Table: `global_configs` — 19 rows

System-wide configuration keys ที่สำคัญ:

| Group             | Keys                                                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Branding          | `LOGO`, `WATERMARK`, `COMPANY_NAME`                                                                                      |
| Password Policy   | `PASSWORD_EXPIRES_DURATION`, `MAX_SAME_PASSWORD_COUNT`, `MAX_AUTH_FAILED_COUNT`, `RESET_PASSWORD_TOKEN_EXPIRES_DURATION` |
| Tax / Commission  | `DEFAULT_VAT`, `DEFAULT_WHT`, `DEFAULT_COMMISSION_RATE`                                                                  |
| EOD Batch         | `EOD_THEN_SUMPORT`, `EOD_ALLOW_NEGATIVE_BALANCE`                                                                         |
| NAV Reports       | `NAV_REPORT_DISPLAY_NAV`, `NAV_DISPLAY`                                                                                  |
| FX Security Types | `FX_SPOT_SECURITY_TYPE_ID`, `FX_FORWARD_SECURITY_TYPE_ID`, `FX_SWAP_SECURITY_TYPE_ID`                                    |
| Default Source    | `DEFAULT_PRICESOURCE_ID`                                                                                                 |

### 6.3 Table: `investments` — 24 rows

Investment-product reference list (ใช้ classify holdings)

ตัวอย่าง: `-1 FOREX (FX)`, `1 BOND-TH`, `2 COMMON STOCK`, `3 PREFERRED STOCK`, `4 WARRANT`, `5 UNIT TRUST`, `6 S/A OPERATE`, `7 BE`, `8 FD`, `9 NCD`, `10 PN`, `11 C/A OPERATE`, `12 BOND-F`, `13 CD`, `14 FCD`, `15 GOLD`, `16 DEBENTURE-TH`, `17 DEBENTURE-F`, `18 BE_Coupon`, `19 S/A INVEST`, `20 C/A INVEST`, `21 BE_Bond` และอีก 2 รายการ

### 6.4 Table: `standard_accounts` — 451 rows

Pre-built Chart of Accounts (COA) แต่ละแถวประกอบด้วย:

* `internal_code` (เช่น `CASH`, `BOND`, `EQUITY`, `UNITTRUST`)
* รหัสบัญชี 6 หลัก (เช่น `110102` สำหรับ Cash)
* `account_group` (ASSET / LIABILITY / EQUITY / INCOME / EXPENSE)
* Flags: `is_apply_tenor`, `is_realized_fx`

{% hint style="warning" %}
การเปลี่ยนรหัสบัญชีกระทบ general-ledger postings ทุก transaction
{% endhint %}

### 6.5 Table: `security_classes` — 5 rows

Top-level security taxonomy

| id | code       | description |
| -- | ---------- | ----------- |
| 1  | CA         | CASH        |
| 2  | EQ         | EQUITY      |
| 3  | BOND       | BOND        |
| 4  | DERIVATIVE | DERIVATIVES |
| 7  | FOREX      | FOREX       |

### 6.6 Table: `invest_tx_types` — 32 rows

Permitted investment transaction types (id, code)

ตัวอย่าง: `1 BUY`, `2 SELL`, `3 DEPOSIT`, `4 WITHDRAW`, `5 MATURE`, `6 ROLLOVER`, `7 RIGHT`, `8 INCREASE`, `9 SPLIT`, `10 DEFAULT`, `11 TRANSFER IN`, `12 TRANSFER OUT`, `13 CONVERT`, `14 REV-REPO`, `15 REPO`, `16 OFFSET-B`, `17 OFFSET-S`, `18 Exercise`, `19 LEND`, `21 TRANSFER FROM`, `22 TRANSFER TO`, `23 ADJUSTED`, `26 BUY/SELL`, `27 SELL/BUY`, `28 BORROW`, `29 LEND`, `30 SHORT`, `31 COVER`, `34 RIGHT-SHORT`, `35 DELIVERY`, `36 EXERCISE-D`, `37 EXERCISE-W`

{% hint style="warning" %}
IDs เหล่านี้ถูกอ้างอิงโดย `invest_transactions` — ห้ามเปลี่ยนเลข
{% endhint %}

### 6.7 Table: `cash_tx_types` — 27 rows

Permitted cash transaction types พร้อม `internal_type` และ `in_out_type` (IN / OUT / ALL)

ตัวอย่าง: Other Expense (OUT), Contribution (IN), Other Income (IN), Dividend (IN), Interest (ALL), Distribution (OUT), Investment (ALL), Subscription (IN), Switch In/Out, Redemption (OUT), Fee (OUT), Principal Repay (IN), Withholding TAX (OUT), Cash from MTM (ALL), Accrued AR/AP, Reverse Accrued AR/AP, Capital Decreasing ฯลฯ

***

## 7. Reference Data Seeds — `010-` to `080-`

### 7.1 `010-countries.sql` — 239 rows

Full ISO country list แต่ละแถวประกอบด้วย: `id`, `name`, `printable_name`, `iso_code` (alpha-2), `iso3_code` (alpha-3), `num_code` (ISO 3166-1 numeric)

**Default tax rates:** ทุกประเทศถูก seed ด้วย `vat_rate = 0.07` และ `wh_tax_rate = 0.03` (อัตราภาษีไทย)

### 7.2 `011-calendars.sql` — 9 calendars + 787 holidays

**Calendars** (5-working-day week ทั้งหมด):

| id | code     | Description    |
| -- | -------- | -------------- |
| 1  | THAILAND | ปฏิทินไทย      |
| 2  | USA      | สหรัฐอเมริกา   |
| 3  | JPY      | ญี่ปุ่น        |
| 4  | EUR      | ยุโรป          |
| 5  | CHF      | สวิตเซอร์แลนด์ |
| 6  | GBP      | สหราชอาณาจักร  |
| 7  | HKD      | ฮ่องกง         |
| 8  | NBIM     | Norges Bank    |
| 9  | CNY      | จีน            |

**Holidays:** 787 รายการ ครอบคลุม 2011-01-03 ถึง 2024-12-31

{% hint style="warning" %}
วันหยุดหลัง 2024-12-31 **ยังไม่ได้** preload — ทีม Operations ต้องเพิ่มข้อมูลปี 2025 เป็นต้นไปก่อนที่ settlement-date logic จะถูกใช้งาน
{% endhint %}

### 7.3 `012-currencies.sql` — 9 currencies + 23 currency pairs

**Currencies:** THB, USD, JPY, EUR, CHF, GBP, HKD, USN (USD-NBIM), CNY

* THB ใช้ฐาน 365 วัน
* สกุลอื่นทั้งหมดใช้ฐาน 360 วัน

**Currency pairs:** 23 คู่ pre-built — ทุกคู่ denominate กับ THB หรือ USD (เช่น THB/USD, USD/THB, GBP/THB, EUR/THB, JPY/THB, HKD/THB, CHF/THB, USD/GBP, USD/EUR, USD/JPY, USD/HKD, USD/CHF, EUR/USD, HKD/USD R inactive, USN/THB, USD/USN, GBP/USD, JPY/EUR, EUR/JPY, EUR/HKD, CNY/THB, USD/CNY, JPY/USD)

### 7.4 `013-tenors.sql` — 144 rows

Pre-defined tenor buckets สำหรับ fixed-income / duration grouping

ตัวอย่าง: `AT_CALL`, `O/N`, `0–3 M`, `3–6 M`, `6–12 M`, `1–3 Y`, `3–5 Y`, `5–7 Y`, `7–10 YRS`, `10–15 Y`, `15 up` พร้อม monthly buckets (`4 MO`, `5 MO`, ...) และ granular ranges อื่น ๆ

### 7.5 `020-sectors.sql` — 44 rows

Industry sector taxonomy (English + Thai labels)

ตัวอย่าง: HEALTHCARE, INSURANCE, MINING, PACKAGING, PROFESSIONAL, NPG (Non-Performing Group), FASHION, HOME & OFFICE PRODUCT ฯลฯ

### 7.6 `030-companies.sql` — 457 rows

Company master (legal entities สำหรับใช้เป็น issuer / counterparty / custodian / guarantor reference)

แต่ละแถวประกอบด้วย: Thai name, English name, base currency, country, sector, registered ID, BIC code

* Row #1 = DHANA SIAM FINANCE COMPANY LIMITED

### 7.7 `040-custodies.sql` — 16 rows

Custodian banks

ตัวอย่าง: KBANK (Kasikornbank), SCIB (Siam City Bank), HSBC, TMB, BBL (Bangkok Bank), BAY (Bank of Ayudhya)

> แต่ละแถวอ้างอิง `company_id` จาก company master

### 7.8 `050-issuers.sql` — 4,240 rows

Securities issuers — **largest reference table**

* รวม Thai และ foreign corporate issuers
* ทุกแถว link กับ `company_id`

{% hint style="warning" %}
issuer IDs ถูกอ้างอิงโดยทุก fixed-income และ equity security record
{% endhint %}

### 7.9 `060-formulars.sql` — 6 rows

Yield และ coupon calculation formulas

| id | code              | description                          | internal |
| -- | ----------------- | ------------------------------------ | -------- |
| 2  | Act Yld/Cpn (CPF) | Actual Yield and Coupon (CPF#1 type) | ACT/ACT  |
| 3  | PN KTT, NCD KTB   | PN KTT and NCD KTB                   | PNKTT    |
| 4  | Avg yld/ Act cpn  | Average Yield and Actual Coupon      | AVG/ACT  |
| 11 | Inter Bond1       | Inter Bond 1                         | AUD      |
| 13 | Inter Bond2       | Inter Bond 2                         | KRW      |
| 14 | FRN BIBOR BOND    | Floating Rate Note BIBOR Bond        | BIBOR    |

### 7.10 `070-guarantors.sql` — 22 rows

Guarantor master

ตัวอย่าง: KBANK, KTT (Krung Thai Thanakit), MOF (Ministry of Finance), SCB (Siam Commercial Bank), BOT (Bank of Thailand), REGCO (Rayong Electricity Generating)

### 7.11 `080-counterparties.sql` — 129 rows

Trading counterparties (banks, securities firms)

ตัวอย่าง: ABN, KBANK, SCB, KTB, ZMICO, CA-CIB, CITIGROUP (R inactive), CIMBT

> แต่ละแถวมี `reference_id` link กลับไปยัง company master

***

## 8. Regulatory Reporting Seeds — `090-rp.sql`

ไฟล์นี้ populate ข้อมูลที่ใช้สร้างรายงานกำกับดูแล (NAV / PF1000-style)

<table><thead><tr><th width="255">Table</th><th width="124">Rows</th><th>Purpose</th></tr></thead><tbody><tr><td><code>rp_holding_asset_mappings</code></td><td>96</td><td>Map short asset codes (เช่น <code>223-xxx</code> BE Call, <code>109-xxx</code> Unit Trust-FI, <code>213-xxx</code> Bond, <code>216-xxx</code> Saving Account, Tier I (2), Tier II (1), <code>PVD12-23_*</code>, <code>PVD27-8-9_*</code>, <code>PVD28_*</code>) ไปยัง <code>liab_code</code> และคำอธิบายไทย/อังกฤษ รวม Provident-Fund (PVD) และ Tier-classified instruments</td></tr><tr><td><code>rp_asset_groups</code></td><td>10</td><td>Top-level reporting groupings: GOV_ASSET (sovereign), FIN_ASSET (bank-issued), GRADE_ASSET (investment grade), UNDERGRADE_ASSET (sub-investment grade), FD-PN-DR-NCD-BE, EQ, BOND-TB, UT, NVDR, WARRANT</td></tr><tr><td><code>rp_holding_asset_reports</code></td><td>47</td><td>Join mappings ไปยัง 2 reports คือ NAV_REPORT (7 แถว) และ PF1000 (40 แถว) พร้อม sequence number และ flags <code>is_calc_duration</code>, <code>is_calc_yield</code>, <code>is_use_internal_ut</code> (default = false)</td></tr></tbody></table>

{% hint style="warning" %}
report definitions ที่นี่กำหนดวิธีการ aggregate holdings สำหรับการส่งรายงานต่อหน่วยงานกำกับ — การเปลี่ยน mapping ID, sequence หรือ flag ใด ๆ ต้องผ่าน controlled-change process
{% endhint %}

***

## 9. Post-Load Script — `999-finish.sql`

ไม่มีการแทรก business data — สคริปต์นี้ทำ 3 อย่าง:

1. **Sequence reset:** loop ทุก sequence ในฐานข้อมูล และรัน `SETVAL(seq, MAX(column)+1, false)` เพื่อให้ auto-generated IDs ทำงานต่อจากค่าที่ seed ไว้อย่างปลอดภัย
2. **Trigger cleanup:** drop trigger `*_mutation_notify` เดิมทั้งหมดในทุกตารางของ public schema
3. **Notify trigger install:** สร้าง `mutation_notify_trigger()` function และ attach `AFTER INSERT/UPDATE/DELETE` trigger ชื่อ `<table>_mutation_notify` ทุกตารางใน public schema **ยกเว้น** `roles`, `sessions`, `activities`, `tokens` และทุก `log_*` table โดย trigger จะส่ง `pg_notify('event', ...)` payload เพื่อให้ application รับฟังสำหรับ cache invalidation / real-time updates

{% hint style="warning" %}
เนื่องจาก `roles`, `sessions`, `tokens` และ `log_*` ถูกยกเว้นโดยเจตนา — การเปลี่ยนแปลงในตารางเหล่านี้จะ**ไม่**ปรากฏใน application event channel ต้องตรวจสอบว่ามีกลไกอื่นทำ audit logging แยกไว้
{% endhint %}

***

## 10. Total Rows Pre-Injected (สรุปข้อมูลทั้งหมด)

| Group                | Files            | Tables Affected                                                                                                                                                             | Total Rows     |
| -------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Schema bootstrap     | `table.sql`      | `roles`                                                                                                                                                                     | 1              |
| System bootstrap     | `001-init.sql`   | `users`, `global_configs`, `investments`, `standard_accounts`, `security_classes`, `invest_tx_types`, `cash_tx_types`                                                       | 559            |
| Reference data       | `010-` … `080-`  | `countries`, `calendars`, `holidays`, `currencies`, `currency_pairs`, `tenors`, `sectors`, `companies`, `custodies`, `issuers`, `formulars`, `guarantors`, `counterparties` | 6,125          |
| Regulatory reporting | `090-rp.sql`     | `rp_holding_asset_mappings`, `rp_asset_groups`, `rp_holding_asset_reports`                                                                                                  | 153            |
| Post-load (no data)  | `999-finish.sql` | sequences + triggers only                                                                                                                                                   | 0              |
| **Grand Total**      | **15 files**     | **24 distinct seeded tables**                                                                                                                                               | **6,838 rows** |

***

## 11. Audit Checklist (รายการตรวจสอบสำหรับ Audit)

<table><thead><tr><th width="45">#</th><th width="500">Item</th><th width="99">Status</th><th>Note</th></tr></thead><tbody><tr><td>1</td><td><strong>Default credentials</strong> — ยืนยันว่า user <code>admin / admin@admin.com</code> ได้เปลี่ยน password แล้ว และตั้งค่า <code>MAX_AUTH_FAILED_COUNT</code>, <code>PASSWORD_EXPIRES_DURATION</code>, <code>MAX_SAME_PASSWORD_COUNT</code> ตาม policy</td><td>☐</td><td></td></tr><tr><td>2</td><td><strong>Default tax rates</strong> — ทุกประเทศใน <code>countries</code> seed ด้วย VAT 7% / WHT 3% ต้องยืนยันว่าตรงกับ tax policy หรือปรับแก้ตามแต่ละประเทศก่อน go-live</td><td>☐</td><td></td></tr><tr><td>3</td><td><strong>Holiday calendar coverage</strong> — <code>holidays</code> ครอบคลุมถึง 2024-12-31 เท่านั้น ต้องเพิ่มข้อมูลปี 2025 เป็นต้นไปก่อนใช้ settlement / accrual logic</td><td>☐</td><td></td></tr><tr><td>4</td><td><strong>Chart of accounts</strong> — 451 codes ใน <code>standard_accounts</code> ถูกอ้างอิงโดยทุก GL posting การเปลี่ยนต้องผ่าน change-management</td><td>☐</td><td></td></tr><tr><td>5</td><td><strong>Transaction-type &#x26; security-class IDs</strong> — <code>invest_tx_types</code> (32), <code>cash_tx_types</code> (27), <code>security_classes</code> (5) เป็น immutable contract กับ application ห้าม renumber</td><td>☐</td><td></td></tr><tr><td>6</td><td><strong>Reporting mappings</strong> — NAV_REPORT (7 lines) และ PF1000 (40 lines) ใน <code>rp_holding_asset_reports</code> กำหนดว่าจะส่งอะไรให้หน่วยงานกำกับ</td><td>☐</td><td></td></tr><tr><td>7</td><td><strong>Notify-trigger exclusions</strong> — <code>roles</code>, <code>sessions</code>, <code>activities</code>, <code>tokens</code> และ <code>log_*</code> ถูกยกเว้นจาก real-time notify trigger โดยเจตนา</td><td>☐</td><td></td></tr><tr><td>8</td><td><strong>Roles</strong> — มี application role เดียวที่ seed (<code>super_admin</code>) ต้องสร้าง role อื่นสำหรับ segregation-of-duties หลัง deploy</td><td>☐</td><td></td></tr></tbody></table>

***

## 12. IT Deployment Notes (หมายเหตุสำหรับฝ่าย IT)

### 12.1 Pre-Deployment Checklist

* [ ] ตรวจสอบ PostgreSQL version และ extension `pgcrypto` พร้อมใช้งาน
* [ ] เตรียม empty database (UTF-8 encoding, timezone Asia/Bangkok)
* [ ] Backup ฐานข้อมูลปัจจุบัน (กรณี re-deploy)
* [ ] ตรวจสอบสิทธิ์ของ database user ที่จะรัน script (ต้องมี CREATE TABLE, INSERT, CREATE TRIGGER, CREATE EXTENSION)

### 12.2 Deployment Steps

1. รัน `table.sql` (DDL) — สร้าง schema 226 tables + seed `roles`
2. รัน `001-init.sql` (system bootstrap) — admin user, configs, COA, tx types
3. รัน `010-countries.sql` ถึง `080-counterparties.sql` (reference data — 11 ไฟล์)
4. รัน `090-rp.sql` (regulatory reporting mappings)
5. รัน `999-finish.sql` (sequence reset + notify triggers)

### 12.3 Post-Deployment Verification

* [ ] ยืนยันจำนวนแถวรวม = **6,838 rows** ใน 24 ตาราง
* [ ] Login ด้วย `admin / admin@admin.com` และเปลี่ยน password ทันที
* [ ] ตรวจสอบ trigger `*_mutation_notify` ถูกสร้างในตารางที่ควรมี (ยกเว้น `roles`, `sessions`, `activities`, `tokens`, `log_*`)
* [ ] ทดสอบ `pg_notify` channel `event` รับ payload ได้จริง
* [ ] เพิ่มข้อมูลวันหยุดปี 2025+ (กรณีจะใช้งานข้าม 2024-12-31)
* [ ] ปรับ default VAT / WHT rate ตามประเทศที่ไม่ใช่ไทย (ถ้าจำเป็น)

### 12.4 Rollback Plan

* กรณี deploy ไม่สำเร็จ: drop database แล้ว restore จาก backup
* ไม่แนะนำให้รัน partial script เพราะมี FK ข้ามไฟล์
* หากต้องการรันใหม่ ให้ drop database ก่อนทุกครั้ง

***

**— จบเอกสาร —**

> Document generated from a static review of the SQL files in the deployment folder. No connection was made to a running database.
