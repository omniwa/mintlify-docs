---
description: >-
  Bank Account adds a bank account into the system to support portfolio
  management and financial transactions.
icon: clipboard-user
---

# Bank Account

### Bank Account

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure></div>

| **Component**              | **Description (English)**                                                     | **คำอธิบาย (ภาษาไทย)**                                           |
| -------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Bank Code (Search)         | Search for accounts associated with a specific bank using its code.           | ช่องสำหรับค้นหาบัญชีธนาคารตามรหัสธนาคาร                          |
| Account Number (Search)    | Search for a specific bank account using its account number.                  | ช่องสำหรับค้นหาด้วยหมายเลขบัญชีธนาคาร                            |
| Bank Account Preset        | Quickly apply or view predefined bank account templates.                      | ปุ่มสำหรับเรียกใช้หรือดูพรีเซ็ตของบัญชีธนาคารที่ตั้งค่าไว้       |
| Create Bank Account        | Open the setup to register and add a new bank account to the system.          | ปุ่มสำหรับเริ่มลงทะเบียนและเพิ่มบัญชีธนาคารใหม่                  |
| Bank Account Table         | Lists all registered bank accounts, including branch and type details.        | ตารางแสดงรายชื่อบัญชีธนาคารทั้งหมด พร้อมข้อมูลสาขาและประเภทบัญชี |
| Preview Button             | View the complete details and historical logs of the account.                 | ปุ่มสำหรับเรียกดูรายละเอียดและประวัติของบัญชีธนาคาร              |
| Edit Button                | Modify the settings, branch info, or type of an existing account.             | ปุ่มสำหรับแก้ไขข้อมูลหรือการตั้งค่าของบัญชีธนาคารเดิม            |
| Delete Button              | Remove a bank account record from the system.                                 | ปุ่มสำหรับลบข้อมูลบัญชีธนาคารออกจากระบบ                          |
| Pending Bank Account Table | Accounts that have been recently created or edited and are awaiting approval. | ตารางแสดงรายชื่อบัญชีธนาคารที่รอการอนุมัติก่อนเริ่มใช้งานจริง    |



### Create Bank Account

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure></div>

| **Component**     | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                              |
| ----------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------- |
| From Preset       | Select a pre-configured template to auto-fill common bank details. | เลือกเทมเพลตที่ตั้งค่าไว้ล่วงหน้าเพื่อกรอกข้อมูลพื้นฐานโดยอัตโนมัติ |
| Bank Account No   | Enter the official bank account number (Required).                 | กรอกหมายเลขบัญชีธนาคาร (จำเป็นต้องระบุ)                             |
| Bank Code         | Select the banking institution associated with this account.       | เลือกธนาคารเจ้าของบัญชี                                             |
| Bank Branch       | Select the specific branch where the account was opened.           | เลือกสาขาของธนาคารที่เปิดบัญชี                                      |
| Bank Account Type | Define the type of account (e.g., Current, Savings, Fixed).        | กำหนดประเภทบัญชี (เช่น บัญชีกระแสรายวัน, ออมทรัพย์)                 |
| Open Date         | The official date when the bank account was activated.             | วันที่เริ่มเปิดใช้งานบัญชีธนาคาร                                    |
| Close Date        | The date the account was closed or deactivated (if applicable).    | วันที่ปิดบัญชีหรือยกเลิกการใช้งาน (ถ้ามี)                           |
| Clear Button      | Reset all fields in the form to their default empty state.         | ปุ่มสำหรับล้างข้อมูลที่กรอกไว้ทั้งหมดในฟอร์ม                        |
| Create Button     | Save the account details and submit for approval.                  | ปุ่มสำหรับบันทึกข้อมูลบัญชีและส่งไปรอการอนุมัติ                     |
| Cancel Button     | Close the window without saving any changes.                       | ปุ่มสำหรับยกเลิกและปิดหน้าต่างโดยไม่บันทึกข้อมูล                    |



### Bank Account Preset

Bank Account Preset stores reusable bank-account templates so creating new accounts is faster.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure></div>

### Create Bank Account Preset

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure></div>

| **Component**     | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                              |
| ----------------- | ------------------------------------------------------------- | --------------------------------------------------- |
| Preset Name       | A descriptive name for the preset (e.g., "Main Savings SCB"). | ชื่อเรียกสำหรับพรีเซ็ต (เช่น "ออมทรัพย์หลัก SCB")   |
| Bank Account No   | The default bank account number for this preset.              | หมายเลขบัญชีธนาคารที่ต้องการผูกไว้กับพรีเซ็ตนี้     |
| Bank              | Select the banking institution associated with this preset.   | เลือกธนาคารเจ้าของบัญชี                             |
| Bank Branch       | Select the specific branch for this preset.                   | เลือกสาขาของธนาคาร                                  |
| Bank Account Type | Define the account category (e.g., Savings, Current).         | ระบุประเภทของบัญชีธนาคาร                            |
| Open Date         | The default activation date for accounts using this preset.   | วันที่เริ่มเปิดใช้งานบัญชี (ค่าเริ่มต้น)            |
| Close Date        | The expiration or closing date (if applicable).               | วันที่ปิดบัญชีหรือยกเลิกการใช้งาน (ถ้ามี)           |
| Create Button     | Save the preset configuration for future use.                 | ปุ่มสำหรับบันทึกการตั้งค่าพรีเซ็ตเพื่อนำไปใช้งานต่อ |
| Cancel Button     | Discard the current setup and return to the previous page.    | ปุ่มสำหรับยกเลิกและกลับสู่หน้าก่อนหน้า              |



### Don't forget to approve the action in the Pending Table to finalize the creation of your new bank account.



