---
description: >-
  Mapping Account Code FX serves the same purpose as Mapping Account Code, but
  it is dedicated to Foreign Exchange (FX) transactions.
icon: sitemap
---

# Mapping Account Code FX

### Mapping Account Code FX

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                       | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                    |
| ----------------------------------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
| Fx Account Code (Search)            | Search for specific FX mapping records using the account code.     | ช่องสำหรับค้นหาข้อมูลการจับคู่บัญชี FX ด้วยรหัสบัญชี      |
| Currency (Search)                   | Filter the mapping list by a specific currency (e.g., USD, JPY).   | ช่องสำหรับกรองรายการตามสกุลเงินที่ต้องการ                 |
| Create Mapping Account Code for FX  | Open the setup to define a new GL mapping for FX transactions.     | ปุ่มสำหรับเริ่มสร้างการจับคู่รหัสบัญชี FX ใหม่เข้าสู่ระบบ |
| Fx Account Code (Table)             | Lists the registered FX account identifiers used in the system.    | รหัสอ้างอิงบัญชี FX ที่บันทึกไว้ในตารางหลัก               |
| Ccy (Currency)                      | The specific currency assigned to that FX account mapping.         | สกุลเงินที่ผูกไว้กับรหัสบัญชี FX นั้น ๆ                   |
| Proved By / Proved At               | Details of the authorized user and timestamp of approval.          | ข้อมูลผู้ตรวจสอบ/อนุมัติ และวันเวลาที่ทำการอนุมัติรายการ  |
| Preview / Edit / Delete             | Action buttons to view detailed logic, modify, or remove mappings. | ปุ่มสำหรับเรียกดู แก้ไข หรือลบรายการการจับคู่บัญชี        |
| Pending Mapping Account Code for FX | New or modified FX mappings awaiting authorized approval.          | ตารางแสดงรายการที่รอการอนุมัติก่อนที่จะมีผลบังคับใช้      |



### Create Mapping Account Code FX

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure></div>

| **Component**            | **Description (English)**                                   | **คำอธิบาย (ภาษาไทย)**                                      |
| ------------------------ | ----------------------------------------------------------- | ----------------------------------------------------------- |
| FX Account Code          | Unique identifier for this FX mapping configuration.        | รหัสเฉพาะสำหรับระบุการตั้งค่าการจับคู่บัญชี FX              |
| Currency Code            | The currency assigned to these transaction mappings.        | สกุลเงินที่ใช้สำหรับรายการธุรกรรมเหล่านี้                   |
| Remark                   | Additional notes or context regarding this mapping.         | หมายเหตุเพิ่มเติมหรือคำอธิบายประกอบ                         |
| Portfolio Available      | List of portfolios that haven't been assigned this mapping. | รายชื่อพอร์ตโฟลิโอที่สามารถเลือกนำมาจับคู่ได้               |
| Selection Button (<>)    | Move portfolios between the Available and Selected lists.   | ปุ่มสำหรับย้ายพอร์ตโฟลิโอไปมาระหว่างช่องเลือก               |
| Portfolio Selected       | Portfolios that will active use this specific GL mapping.   | รายชื่อพอร์ตโฟลิโอที่ถูกเลือกเพื่อใช้การตั้งค่านี้          |
| FX Forward Bought        | GL mapping for forward purchase transactions.               | รหัสบัญชีสำหรับการซื้อเงินตราต่างประเทศล่วงหน้า             |
| FX Forward Sold          | GL mapping for forward sale transactions.                   | รหัสบัญชีสำหรับการขายเงินตราต่างประเทศล่วงหน้า              |
| FX Spot Bought           | GL mapping for spot purchase transactions.                  | รหัสบัญชีสำหรับการซื้อเงินตราต่างประเทศทันที                |
| FX Spot Sold             | GL mapping for spot sale transactions.                      | รหัสบัญชีสำหรับการขายเงินตราต่างประเทศทันที                 |
| FX Swap Bought (1st leg) | First leg mapping for FX swap purchases.                    | รหัสบัญชีสำหรับขาที่ 1 ของการทำ FX Swap (ซื้อ)              |
| FX Swap Bought (2nd leg) | Second leg mapping for FX swap purchases.                   | รหัสบัญชีสำหรับขาที่ 2 ของการทำ FX Swap (ซื้อ)              |
| FX Swap Sold (1st leg)   | First leg mapping for FX swap sales.                        | รหัสบัญชีสำหรับขาที่ 1 ของการทำ FX Swap (ขาย)               |
| FX Swap Sold (2nd leg)   | Second leg mapping for FX swap sales.                       | รหัสบัญชีสำหรับขาที่ 2 ของการทำ FX Swap (ขาย)               |
| MTM FX Asset             | Valuation mapping for FX-related assets.                    | รหัสบัญชีสำหรับการตีมูลค่าสินทรัพย์ที่เป็นเงินตราต่างประเทศ |
| MTM FX Liab.             | Valuation mapping for FX-related liabilities.               | รหัสบัญชีสำหรับการตีมูลค่าหนี้สินที่เป็นเงินตราต่างประเทศ   |
| Unrealized FX P\&L       | Mapping for gains or losses not yet realized.               | รหัสบัญชีสำหรับกำไร/ขาดทุนที่ยังไม่เกิดขึ้นจาก FX           |
| Create Button            | Save the configuration and submit for approval.             | ปุ่มสำหรับบันทึกข้อมูลและส่งไปรอการอนุมัติ                  |
| Cancel Button            | Discard all input and return to the previous screen.        | ปุ่มสำหรับยกเลิกและกลับสู่หน้าก่อนหน้า                      |



### Don't forget to approve the action in the Pending Table to finalize the mapping setup for your FX accounts.



