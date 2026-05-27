---
description: >-
  Cash GL maps Cash Tx Type entries to their Cash GL Code so that every cash
  transaction posts to the correct ledger account.
icon: cash-register
---

# Cash GL

### Cash GL

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure></div>

| **Component**              | **Description (English)**                                                 | **คำอธิบาย (ภาษาไทย)**                                                |
| -------------------------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Cash GL Code (Search)      | Search for specific mapping records between cash accounts and GL codes.   | ช่องสำหรับค้นหาข้อมูลการจับคู่ระหว่างบัญชีเงินสดและรหัสบัญชีแยกประเภท |
| Create Cash GL Code        | Open the interface to define a new mapping for accounting integration.    | ปุ่มสำหรับเริ่มสร้างการจับคู่รหัสบัญชีใหม่เพื่อใช้ในการลงบัญชี        |
| Cash GL Code Table         | Lists all registered mappings that dictate how cash movements are booked. | ตารางแสดงรายการการจับคู่รหัสบัญชีทั้งหมดที่บันทึกไว้ในระบบ            |
| Pending Cash GL Code Table | Mapping entries that are recently created or updated and await approval.  | ตารางแสดงรายการจับคู่รหัสบัญชีที่รอการอนุมัติก่อนเริ่มใช้งานจริง      |



### Create Cash GL

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure></div>

| **Component** | **Description (English)**                                                        | **คำอธิบาย (ภาษาไทย)**                                          |
| ------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Cash Tx Type  | Select the specific cash transaction type (e.g., Supscription, Redemtionl, Fee). | เลือกประเภทรายการเงินสด (เช่น รายการฝาก, ถอน, หรือค่าธรรมเนียม) |
| Cash GL Code  | Define the General Ledger code for accounting classification.                    | กำหนดรหัสบัญชีแยกประเภทที่ใช้สำหรับจัดหมวดหมู่ทางบัญชี          |
| Create Button | Save the mapping and register it in the pending table for approval.              | ปุ่มสำหรับบันทึกการจับคู่รหัสบัญชีและส่งไปรอการอนุมัติ          |
| Cancel Button | Discard the current selection and return to the main management list.            | ปุ่มสำหรับยกเลิกสิ่งที่เลือกไว้และกลับสู่หน้ารายการหลัก         |



### Don't forget to approve the action in the Pending Table to finalize the mapping of your cash transaction types to GL codes.



