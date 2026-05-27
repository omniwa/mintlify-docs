---
description: Reference Rate defines a benchmark interest rate for financial instruments.
icon: percent
---

# Reference Rate

### Reference Rate

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                | **Description (English)**                                                         | **คำอธิบาย (ภาษาไทย)**                                         |
| ---------------------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Reference Rate Code (Search) | Search for a specific reference rate using its unique identifier code.            | ช่องสำหรับค้นหาอัตราอ้างอิงที่มีอยู่ในระบบด้วยรหัสอ้างอิง      |
| Create Reference Rate        | Open the interface to define and add a new reference rate to the system.          | ปุ่มสำหรับเริ่มตั้งค่าและเพิ่มอัตราอ้างอิงใหม่เข้าสู่ระบบ      |
| Reference Rate Table         | Lists all registered reference rates used for valuation and interest calculation. | ตารางแสดงรายชื่ออัตราอ้างอิงทั้งหมดที่บันทึกไว้ในระบบ          |
| Preview Button               | View the detailed configuration and benchmark settings of the rate.               | ปุ่มสำหรับเรียกดูรายละเอียดและการตั้งค่าของอัตราอ้างอิงนั้น ๆ  |
| Edit Button                  | Modify the attributes or source mapping of an existing reference rate.            | ปุ่มสำหรับแก้ไขคุณลักษณะหรือข้อมูลของอัตราอ้างอิงเดิม          |
| Delete Button                | Remove the reference rate record from the system database.                        | ปุ่มสำหรับลบข้อมูลอัตราอ้างอิงออกจากระบบ                       |
| Pending Reference Rate Table | Rates that have been recently created or modified and are awaiting approval.      | ตารางแสดงรายชื่ออัตราอ้างอิงที่รอการอนุมัติก่อนเริ่มใช้งานจริง |



### Create Reference Rate

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure></div>

| **Component**       | **Description (English)**                                                  | **คำอธิบาย (ภาษาไทย)**                                         |
| ------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Reference Rate Code | A unique identification code for the reference rate (e.g., THBFIX, LIBOR). | รหัสเฉพาะสำหรับระบุอัตราอ้างอิง                                |
| Value Date          | The effective date for the specific interest rate value.                   | วันที่มีผลบังคับใช้สำหรับค่าอัตราดอกเบี้ยนั้น ๆ                |
| Interest Rate       | The percentage value of the reference rate on the specified value date.    | ค่าอัตราดอกเบี้ย (เปอร์เซ็นต์) ณ วันที่ระบุ                    |
| Delete Button       | Remove a specific rate/date row from the entry list.                       | ปุ่มสำหรับลบแถวข้อมูลที่ไม่ต้องการออกจากรายการ                 |
| Add Detail          | Append a new row to input additional rate values for different dates.      | ปุ่มสำหรับเพิ่มแถวใหม่เพื่อกรอกข้อมูลอัตราดอกเบี้ยของวันอื่น ๆ |
| Create Button       | Save the entire rate series and submit it for approval.                    | ปุ่มสำหรับบันทึกชุดข้อมูลทั้งหมดและส่งไปรอการอนุมัติ           |
| Cancel Button       | Discard all current input and return to the previous page.                 | ปุ่มสำหรับยกเลิกสิ่งที่กรอกไว้ทั้งหมดและกลับสู่หน้าก่อนหน้า    |





### Don't forget to approve the action in the Pending Table to finalize the updates to your reference rate data.



