---
icon: square-arrow-right
---

# Doc for IT (ENG)

**Supporting Document for Data Import and System Deployment**

***

## Document Control

| Item               | Detail                                                            |
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

### Revision History

| Version | Date        | Author           | Change Description                         |
| ------- | ----------- | ---------------- | ------------------------------------------ |
| 1.0     | 12 May 2026 | Development Team | Initial release for IT deployment hand-off |

***

## 1. Purpose and Scope

### 1.1 Purpose

This document is prepared to:

* Inventory every seed data value pre-injected into the database by the deployment SQL files
* Support the data-import and system-deployment activities performed by the IT team
* Be used as the reference during inspection and assessment by the Internal Control / Audit team
* Confirm the reference data, default codes, master records, and system accounts that will be present at first boot — before any business transaction occurs

### 1.2 Scope

Covers the 15 SQL files located in the deployment folder of the `poc-msth-deploy` system, including both DDL (schema) and DML (data). The total seeded data is **6,838 rows** across **24 tables**.

> This document was prepared from a **static review** of the SQL files only. **No connection was made to a running database.**

***

## 2. References

| #   | Document                         |
| --- | -------------------------------- |
| R-1 | SQL deployment folder (15 files) |

***

## 3. Definitions and Abbreviations

| Term      | Meaning                                                                   |
| --------- | ------------------------------------------------------------------------- |
| DDL       | Data Definition Language — commands that create/modify database structure |
| DML       | Data Manipulation Language — commands that manage data inside tables      |
| Seed Data | Initial data required for the system to start operating                   |
| COA       | Chart of Accounts                                                         |
| NAV       | Net Asset Value                                                           |
| EOD       | End-of-Day                                                                |
| FX        | Foreign Exchange                                                          |
| VAT       | Value Added Tax                                                           |
| WHT       | Withholding Tax                                                           |
| PVD       | Provident Fund                                                            |
| BIC       | Bank Identifier Code                                                      |

***

## 4. Deployment Order

All SQL files are executed in filename order. Numerical prefixes (`001-`, `010-`, ..., `999-`) define the load sequence.

| #  | File                     | Type            | Purpose                                       |
| -- | ------------------------ | --------------- | --------------------------------------------- |
| 0  | `table.sql`              | DDL (schema)    | Creates 226 tables + 1 seed (`roles`)         |
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

> **IT Note:** Do not change the execution order. Several tables have foreign-key references that cross between files.

***

## 5. Schema File — `table.sql`

### 5.1 Overview

* **Statements:** 226 `CREATE TABLE` statements covering the entire application data model (sessions, users, roles, employees, portfolios, securities, holdings, accounting/GL, compliance rules, audit-trail tables prefixed `log_*`, etc.)

### 5.2 Embedded Seed Inside DDL

* **Table `roles`** — 1 row inserted with `ON CONFLICT DO NOTHING`:
  * `('super_admin', '{*}')` — full-permission role required by the bootstrap admin user

### 5.3 Database Extension

* `pgcrypto` — enabled to generate UUIDs for tables such as `roles`, `employees`, `file_storages`, etc.

### 5.4 Triggers / Functions

No trigger is created in `table.sql`. All mutation-notification triggers are created later by `999-finish.sql`.

***

## 6. Bootstrap Seed — `001-init.sql`

This file contains the data the application needs to start: an admin login, system configuration, the chart of accounts, and the controlled transaction-type / security-class enumerations.

### 6.1 Table: `users` — 1 row

The single bootstrap administrator (first credential present in the system).

| id | username | email           | role         | active\_flag | status |
| -- | -------- | --------------- | ------------ | ------------ | ------ |
| 1  | admin    | admin@admin.com | super\_admin | A            | 1      |

* Password is stored as an Argon2id hash (`argon2id$2$65536$4$16$...`)
* `password_updated_at = NULL` — the application will force a password reset on first login
* **Audit attention:** The password must be changed and first-login activity of this user must be reviewed.

### 6.2 Table: `global_configs` — 19 rows

System-wide configuration keys. Notable groups:

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

Investment-product reference list (used to classify holdings).

Examples: `-1 FOREX (FX)`, `1 BOND-TH`, `2 COMMON STOCK`, `3 PREFERRED STOCK`, `4 WARRANT`, `5 UNIT TRUST`, `6 S/A OPERATE`, `7 BE`, `8 FD`, `9 NCD`, `10 PN`, `11 C/A OPERATE`, `12 BOND-F`, `13 CD`, `14 FCD`, `15 GOLD`, `16 DEBENTURE-TH`, `17 DEBENTURE-F`, `18 BE_Coupon`, `19 S/A INVEST`, `20 C/A INVEST`, `21 BE_Bond`, plus 2 more.

### 6.4 Table: `standard_accounts` — 451 rows

The pre-built Chart of Accounts (COA). Every row carries:

* `internal_code` (e.g. `CASH`, `BOND`, `EQUITY`, `UNITTRUST`)
* A 6-digit account code (e.g. `110102` for Cash)
* `account_group` (ASSET / LIABILITY / EQUITY / INCOME / EXPENSE)
* Flags: `is_apply_tenor`, `is_realized_fx`

> **Audit attention:** Any change to these account codes affects every general-ledger posting.

### 6.5 Table: `security_classes` — 5 rows

Top-level security taxonomy.

| id | code       | description |
| -- | ---------- | ----------- |
| 1  | CA         | CASH        |
| 2  | EQ         | EQUITY      |
| 3  | BOND       | BOND        |
| 4  | DERIVATIVE | DERIVATIVES |
| 7  | FOREX      | FOREX       |

### 6.6 Table: `invest_tx_types` — 32 rows

Permitted investment transaction types (id, code).

Examples: `1 BUY`, `2 SELL`, `3 DEPOSIT`, `4 WITHDRAW`, `5 MATURE`, `6 ROLLOVER`, `7 RIGHT`, `8 INCREASE`, `9 SPLIT`, `10 DEFAULT`, `11 TRANSFER IN`, `12 TRANSFER OUT`, `13 CONVERT`, `14 REV-REPO`, `15 REPO`, `16 OFFSET-B`, `17 OFFSET-S`, `18 Exercise`, `19 LEND`, `21 TRANSFER FROM`, `22 TRANSFER TO`, `23 ADJUSTED`, `26 BUY/SELL`, `27 SELL/BUY`, `28 BORROW`, `29 LEND`, `30 SHORT`, `31 COVER`, `34 RIGHT-SHORT`, `35 DELIVERY`, `36 EXERCISE-D`, `37 EXERCISE-W`.

> **Audit attention:** These IDs are referenced in `invest_transactions` and must not be renumbered.

### 6.7 Table: `cash_tx_types` — 27 rows

Permitted cash transaction types with `internal_type` and `in_out_type` (IN / OUT / ALL).

Examples: Other Expense (OUT), Contribution (IN), Other Income (IN), Dividend (IN), Interest (ALL), Distribution (OUT), Investment (ALL), Subscription (IN), Switch In/Out, Redemption (OUT), Fee (OUT), Principal Repay (IN), Withholding TAX (OUT), Cash from MTM (ALL), Accrued AR/AP, Reverse Accrued AR/AP, Capital Decreasing, etc.

***

## 7. Reference Data Seeds — `010-` to `080-`

### 7.1 `010-countries.sql` — 239 rows

Full ISO country list. Each row carries `id`, `name`, `printable_name`, `iso_code` (alpha-2), `iso3_code` (alpha-3), `num_code` (ISO 3166-1 numeric).

**Default tax rates:** Every country is seeded with `vat_rate = 0.07` and `wh_tax_rate = 0.03` (Thai default rates).

### 7.2 `011-calendars.sql` — 9 calendars + 787 holidays

**Calendars** (all are 5-working-day weeks):

| id | code     | Description    |
| -- | -------- | -------------- |
| 1  | THAILAND | Thailand       |
| 2  | USA      | United States  |
| 3  | JPY      | Japan          |
| 4  | EUR      | Eurozone       |
| 5  | CHF      | Switzerland    |
| 6  | GBP      | United Kingdom |
| 7  | HKD      | Hong Kong      |
| 8  | NBIM     | Norges Bank    |
| 9  | CNY      | China          |

**Holidays:** 787 date entries spanning 2011-01-03 through 2024-12-31.

> **Audit attention:** Holidays beyond 2024-12-31 are **NOT** preloaded. The Operations team must add 2025+ entries before any settlement-date logic is exercised.

### 7.3 `012-currencies.sql` — 9 currencies + 23 currency pairs

**Currencies:** THB, USD, JPY, EUR, CHF, GBP, HKD, USN (USD-NBIM), CNY

* THB uses a 365-day basis
* All other currencies use a 360-day basis

**Currency pairs:** 23 pre-built pairs — every pair is denominated against THB or USD (e.g. THB/USD, USD/THB, GBP/THB, EUR/THB, JPY/THB, HKD/THB, CHF/THB, USD/GBP, USD/EUR, USD/JPY, USD/HKD, USD/CHF, EUR/USD, HKD/USD R inactive, USN/THB, USD/USN, GBP/USD, JPY/EUR, EUR/JPY, EUR/HKD, CNY/THB, USD/CNY, JPY/USD).

### 7.4 `013-tenors.sql` — 144 rows

Pre-defined tenor buckets used for fixed-income / duration grouping.

Examples: `AT_CALL`, `O/N`, `0–3 M`, `3–6 M`, `6–12 M`, `1–3 Y`, `3–5 Y`, `5–7 Y`, `7–10 YRS`, `10–15 Y`, `15 up`, plus monthly buckets (`4 MO`, `5 MO`, ...) and additional granular ranges.

### 7.5 `020-sectors.sql` — 44 rows

Industry sector taxonomy (English + Thai labels).

Examples: HEALTHCARE, INSURANCE, MINING, PACKAGING, PROFESSIONAL, NPG (Non-Performing Group), FASHION, HOME & OFFICE PRODUCT, etc.

### 7.6 `030-companies.sql` — 457 rows

Company master (legal entities used as issuer / counterparty / custodian / guarantor references).

Each row carries: Thai name, English name, base currency, country, sector, registered ID, BIC code.

* Row #1 = DHANA SIAM FINANCE COMPANY LIMITED

### 7.7 `040-custodies.sql` — 16 rows

Custodian banks.

Examples: KBANK (Kasikornbank), SCIB (Siam City Bank), HSBC, TMB, BBL (Bangkok Bank), BAY (Bank of Ayudhya).

> Each row references a `company_id` from the company master.

### 7.8 `050-issuers.sql` — 4,240 rows

Securities issuers — **the largest reference table**.

* Includes Thai and foreign corporate issuers
* Every row links to a `company_id`

> **Audit attention:** Issuer IDs are referenced by every fixed-income and equity security record.

### 7.9 `060-formulars.sql` — 6 rows

Yield and coupon calculation formulas.

| id | code              | description                          | internal |
| -- | ----------------- | ------------------------------------ | -------- |
| 2  | Act Yld/Cpn (CPF) | Actual Yield and Coupon (CPF#1 type) | ACT/ACT  |
| 3  | PN KTT, NCD KTB   | PN KTT and NCD KTB                   | PNKTT    |
| 4  | Avg yld/ Act cpn  | Average Yield and Actual Coupon      | AVG/ACT  |
| 11 | Inter Bond1       | Inter Bond 1                         | AUD      |
| 13 | Inter Bond2       | Inter Bond 2                         | KRW      |
| 14 | FRN BIBOR BOND    | Floating Rate Note BIBOR Bond        | BIBOR    |

### 7.10 `070-guarantors.sql` — 22 rows

Guarantor master.

Examples: KBANK, KTT (Krung Thai Thanakit), MOF (Ministry of Finance), SCB (Siam Commercial Bank), BOT (Bank of Thailand), REGCO (Rayong Electricity Generating).

### 7.11 `080-counterparties.sql` — 129 rows

Trading counterparties (banks, securities firms).

Examples: ABN, KBANK, SCB, KTB, ZMICO, CA-CIB, CITIGROUP (R inactive), CIMBT.

> Each row carries a `reference_id` linking back to the company master.

***

## 8. Regulatory Reporting Seeds — `090-rp.sql`

This file populates the data used to build regulatory NAV / PF1000-style reports.

<table><thead><tr><th width="264">Table</th><th width="111">Rows</th><th>Purpose</th></tr></thead><tbody><tr><td><code>rp_holding_asset_mappings</code></td><td>96</td><td>Maps short asset codes (e.g. <code>223-xxx</code> BE Call, <code>109-xxx</code> Unit Trust-FI, <code>213-xxx</code> Bond, <code>216-xxx</code> Saving Account, Tier I (2), Tier II (1), <code>PVD12-23_*</code>, <code>PVD27-8-9_*</code>, <code>PVD28_*</code>) to <code>liab_code</code> plus Thai/English descriptions. Includes Provident-Fund (PVD) and Tier-classified instruments.</td></tr><tr><td><code>rp_asset_groups</code></td><td>10</td><td>Top-level reporting groupings: GOV_ASSET (sovereign), FIN_ASSET (bank-issued), GRADE_ASSET (investment grade), UNDERGRADE_ASSET (sub-investment grade), FD-PN-DR-NCD-BE, EQ, BOND-TB, UT, NVDR, WARRANT.</td></tr><tr><td><code>rp_holding_asset_reports</code></td><td>47</td><td>Joins mappings to the two reports — NAV_REPORT (7 rows) and PF1000 (40 rows) — with a sequence number and flags <code>is_calc_duration</code>, <code>is_calc_yield</code>, <code>is_use_internal_ut</code> (default = false).</td></tr></tbody></table>

> **Audit attention:** The report definitions here determine how holdings are aggregated for regulatory submission. Any change to mapping IDs, sequence, or flags must follow the controlled-change process.

***

## 9. Post-Load Script — `999-finish.sql`

No business data is inserted. The script performs three actions:

1. **Sequence reset:** iterates every sequence in the database and runs `SETVAL(seq, MAX(column)+1, false)` so that auto-generated IDs continue safely beyond the seeded values.
2. **Trigger cleanup:** drops any pre-existing `*_mutation_notify` trigger on every public-schema table.
3. **Notify trigger install:** creates `mutation_notify_trigger()` and attaches an `AFTER INSERT/UPDATE/DELETE` trigger named `<table>_mutation_notify` to every public-schema table **except** `roles`, `sessions`, `activities`, `tokens`, and any `log_*` table. The trigger emits a `pg_notify('event', ...)` payload describing the change, which the application listens to for cache invalidation / real-time updates.

> **Audit attention:** Because `roles`, `sessions`, `tokens`, and the `log_*` audit-trail tables are deliberately excluded from the notify trigger, changes to those tables will **not** appear on the application event channel. Verify that audit logging for these tables relies on a separate mechanism.

***

## 10. Total Rows Pre-Injected

| Group                | Files            | Tables Affected                                                                                                                                                             | Total Rows     |
| -------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Schema bootstrap     | `table.sql`      | `roles`                                                                                                                                                                     | 1              |
| System bootstrap     | `001-init.sql`   | `users`, `global_configs`, `investments`, `standard_accounts`, `security_classes`, `invest_tx_types`, `cash_tx_types`                                                       | 559            |
| Reference data       | `010-` … `080-`  | `countries`, `calendars`, `holidays`, `currencies`, `currency_pairs`, `tenors`, `sectors`, `companies`, `custodies`, `issuers`, `formulars`, `guarantors`, `counterparties` | 6,125          |
| Regulatory reporting | `090-rp.sql`     | `rp_holding_asset_mappings`, `rp_asset_groups`, `rp_holding_asset_reports`                                                                                                  | 153            |
| Post-load (no data)  | `999-finish.sql` | sequences + triggers only                                                                                                                                                   | 0              |
| **Grand Total**      | **15 files**     | **24 distinct seeded tables**                                                                                                                                               | **6,838 rows** |

***

## 11. Audit Checklist

<table><thead><tr><th width="45">#</th><th width="500">Item</th><th width="99">Status</th><th>Note</th></tr></thead><tbody><tr><td>1</td><td><strong>Default credentials</strong> — confirm the <code>admin / admin@admin.com</code> user has had its password changed and <code>MAX_AUTH_FAILED_COUNT</code>, <code>PASSWORD_EXPIRES_DURATION</code>, and <code>MAX_SAME_PASSWORD_COUNT</code> are set to policy</td><td>☐</td><td></td></tr><tr><td>2</td><td><strong>Default tax rates</strong> — every country in <code>countries</code> is seeded with VAT 7% / WHT 3%. Verify these match the entity's tax policy or adjust per country before go-live</td><td>☐</td><td></td></tr><tr><td>3</td><td><strong>Holiday calendar coverage</strong> — <code>holidays</code> only runs through 2024-12-31; any settlement / accrual logic in 2025+ requires additional rows</td><td>☐</td><td></td></tr><tr><td>4</td><td><strong>Chart of accounts</strong> — the 451 pre-built <code>standard_accounts</code> codes are referenced by every general-ledger posting; changes must follow the change-management process</td><td>☐</td><td></td></tr><tr><td>5</td><td><strong>Transaction-type &#x26; security-class IDs</strong> — <code>invest_tx_types</code> (32), <code>cash_tx_types</code> (27), and <code>security_classes</code> (5) IDs are immutable contracts with the application — do not renumber</td><td>☐</td><td></td></tr><tr><td>6</td><td><strong>Reporting mappings</strong> — the NAV_REPORT (7 lines) and PF1000 (40 lines) report assemblies in <code>rp_holding_asset_reports</code> define what is filed with regulators</td><td>☐</td><td></td></tr><tr><td>7</td><td><strong>Notify-trigger exclusions</strong> — <code>roles</code>, <code>sessions</code>, <code>activities</code>, <code>tokens</code>, and <code>log_*</code> tables are intentionally excluded from real-time notification triggers</td><td>☐</td><td></td></tr><tr><td>8</td><td><strong>Roles</strong> — only one application role (<code>super_admin</code>) is seeded — additional segregation-of-duties roles must be created post-deployment</td><td>☐</td><td></td></tr></tbody></table>

***

## 12. IT Deployment Notes

### 12.1 Pre-Deployment Checklist

* [ ] Verify PostgreSQL version and confirm extension `pgcrypto` is available
* [ ] Prepare an empty database (UTF-8 encoding, timezone Asia/Bangkok)
* [ ] Back up the current database (for the re-deploy scenario)
* [ ] Verify the database user running the scripts has the required privileges (CREATE TABLE, INSERT, CREATE TRIGGER, CREATE EXTENSION)

### 12.2 Deployment Steps

{% stepper %}
{% step %}
### Run `table.sql`

DDL creates 226 tables + seeds `roles`.
{% endstep %}

{% step %}
### Run `001-init.sql`

System bootstrap: admin user, configs, COA, tx types.
{% endstep %}

{% step %}
### Run `010-countries.sql` through `080-counterparties.sql`

Reference data — 11 files.
{% endstep %}

{% step %}
### Run `090-rp.sql`

Regulatory reporting mappings.
{% endstep %}

{% step %}
### Run `999-finish.sql`

Sequence reset + notify triggers.
{% endstep %}
{% endstepper %}

### 12.3 Post-Deployment Verification

* [ ] Confirm total row count = **6,838 rows** across 24 tables
* [ ] Log in with `admin / admin@admin.com` and change the password immediately
* [ ] Verify that `*_mutation_notify` triggers exist on the expected tables (excluding `roles`, `sessions`, `activities`, `tokens`, `log_*`)
* [ ] Test that the `pg_notify` channel `event` receives payloads correctly
* [ ] Add 2025+ holiday data (if operating beyond 2024-12-31)
* [ ] Adjust default VAT / WHT rate for non-Thai countries (if applicable)

### 12.4 Rollback Plan

* If deployment fails: drop the database and restore from backup
* Running partial scripts is **not** recommended due to cross-file foreign keys
* For any re-run, drop the database first

***

**— End of Document —**

> Document generated from a static review of the SQL files in the deployment folder. No connection was made to a running database.
