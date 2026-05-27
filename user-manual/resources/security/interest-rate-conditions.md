---
description: >-
  Interest Rate Conditions defines the specific range-based interest-rate
  applications.
icon: percent
---

# Interest Rate Conditions

### Interest Rate Conditions

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                          | **Description (English)**                                                | **คำอธิบาย (ภาษาไทย)**                                       |
| -------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------ |
| Int. Rate Code (Search)                | Search for specific interest rate rules using their unique code.         | ช่องสำหรับค้นหาเงื่อนไขอัตราดอกเบี้ยด้วยรหัสที่ระบุ          |
| Create Interest Rate Conditions        | Open the interface to define new interest rules or tiered rates.         | ปุ่มสำหรับเริ่มสร้างและกำหนดเงื่อนไขอัตราดอกเบี้ยใหม่        |
| Interest Rate Conditions Table         | Lists all registered interest conditions currently active in the system. | ตารางแสดงรายการเงื่อนไขอัตราดอกเบี้ยทั้งหมดที่บันทึกไว้      |
| Preview Button                         | View the full parameters and calculation logic of the condition.         | ปุ่มสำหรับเรียกดูรายละเอียดและตรรกะการคำนวณของเงื่อนไขนั้น ๆ |
| Edit Button                            | Update the spread, base rate, or rules of an existing condition.         | ปุ่มสำหรับแก้ไขหรือปรับปรุงรายละเอียดของเงื่อนไขเดิม         |
| Delete Button                          | Remove an interest rate condition record from the system.                | ปุ่มสำหรับลบข้อมูลเงื่อนไขอัตราดอกเบี้ยออกจากระบบ            |
| Pending Interest Rate Conditions Table | Conditions that have been recently configured and are awaiting approval. | ตารางแสดงเงื่อนไขที่รอการอนุมัติก่อนเริ่มใช้งานจริง          |





### Create Interest Rate Condition

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure></div>

| **Component**            | **Description (English)**                                        | **คำอธิบาย (ภาษาไทย)**                                           |
| ------------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| Int. Rate Condition Code | A unique identifier for this specific interest rate rule.        | รหัสเฉพาะสำหรับระบุเงื่อนไขอัตราดอกเบี้ยนี้                      |
| Broker Code              | Select the associated broker or counterparty for this rate.      | เลือกโบรกเกอร์หรือคู่สัญญาที่ใช้เงื่อนไขนี้                      |
| Progressive / Regressive | Defines if the rate increases or decreases as the range changes. | กำหนดรูปแบบการเปลี่ยนอัตราดอกเบี้ย (แบบก้าวหน้า หรือ แบบถอยหลัง) |
| Interest Rate            | The specific interest percentage for the defined range.          | อัตราดอกเบี้ย (เปอร์เซ็นต์) ที่กำหนดในช่วงนั้น ๆ                 |
| Range From               | The minimum value or amount starting the tier.                   | ค่าเริ่มต้นของช่วง (เช่น วงเงิน หรือ จำนวนเงินขั้นต่ำ)           |
| Range To                 | The maximum value or amount ending the tier.                     | ค่าสิ้นสุดของช่วง (เช่น วงเงิน หรือ จำนวนเงินสูงสุด)             |
| Add Detail               | Append a new row to define additional tiers or ranges.           | ปุ่มสำหรับเพิ่มแถวใหม่เพื่อกำหนดขั้นบันไดเพิ่มเติม               |
| Create Button            | Save the multi-tier configuration and submit for approval.       | ปุ่มสำหรับบันทึกเงื่อนไขทั้งหมดและส่งไปรอการอนุมัติ              |
| Cancel Button            | Discard all current input and return to the main list.           | ปุ่มสำหรับยกเลิกสิ่งที่กรอกไว้และกลับสู่หน้ารายการหลัก           |



### Don't forget to approve the action in the Pending Table to finalize the setup of your new interest rate conditions.



