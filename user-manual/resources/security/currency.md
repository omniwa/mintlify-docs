---
description: >-
  Currency adds and manages monetary units within the system, enabling accurate
  financial transactions, exchange-rate tracking and portfolio valuation.
icon: circle-cent
---

# Currency

### Currency

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure></div>

| **Component**          | **Description (English)**                                              | **คำอธิบาย (ภาษาไทย)**                                                 |
| ---------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Currency Code (Search) | Search for a specific currency using its ISO code (e.g., THB, USD).    | ช่องสำหรับค้นหาสกุลเงินด้วยรหัสสกุลเงิน (เช่น THB, USD)                |
| Create Currency        | Open the interface to add a new currency to the system.                | ปุ่มสำหรับเริ่มเพิ่มสกุลเงินใหม่เข้าสู่ระบบ                            |
| Currency Table         | Lists all active currencies, including their names and audit details.  | ตารางแสดงรายชื่อสกุลเงินทั้งหมด พร้อมชื่อและข้อมูลผู้บันทึก/ผู้อนุมัติ |
| Created By / At        | Displays the user who created the record and the timestamp.            | แสดงชื่อผู้ใช้งานที่สร้างรายการและวันเวลาที่สร้าง                      |
| Proved By / At         | Displays the authorized user who approved the currency record.         | แสดงชื่อผู้อนุมัติและวันเวลาที่ทำการอนุมัติรายการ                      |
| Preview Button         | View the detailed settings and properties of the currency.             | ปุ่มสำหรับเรียกดูรายละเอียดและการตั้งค่าของสกุลเงินนั้น ๆ              |
| Edit Button            | Modify the name or attributes of an existing currency.                 | ปุ่มสำหรับแก้ไขชื่อหรือคุณลักษณะของสกุลเงินเดิม                        |
| Delete Button          | Remove a currency from the system database.                            | ปุ่มสำหรับลบสกุลเงินออกจากระบบ                                         |
| Pending Currency Table | Currencies that have been added or modified and are awaiting approval. | ตารางแสดงรายชื่อสกุลเงินที่รอการอนุมัติก่อนเริ่มใช้งานจริง             |



### Create Currency

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure></div>

| **Component**         | **Description (English)**                                                            | **คำอธิบาย (ภาษาไทย)**                                                                      |
| --------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| Currency Code         | A unique identification code (ISO 4217) for the currency.                            | รหัสเฉพาะสำหรับระบุสกุลเงินตามมาตรฐานสากล                                                   |
| Currency Symbol       | The graphical symbol representing the currency (e.g., $, £, ฿).                      | สัญลักษณ์ที่ใช้แทนสกุลเงิน                                                                  |
| Currency Name         | The full official name of the currency.                                              | ชื่อเต็มของสกุลเงินอย่างเป็นทางการ                                                          |
| Day Basis             | The day-count convention for interest and yield calculations. _(in Future)_          | วิธีการนับจำนวนวันเพื่อใช้ในการคำนวณดอกเบี้ยและผลตอบแทน _(in Future)_                       |
| Price Scale           | Decimal precision and rounding rules for EOD processing.                             | จำนวนทศนิยมและเกณฑ์การปัดเศษสำหรับ (EOD)                                                    |
| Used to calculate ZDF | Flag to include this currency in Zero Discount Factor (ZDF) for Bonds. _(in Future)_ | ระบุว่าต้องการใช้สกุลเงินนี้ในการคำนวณค่าลดส่วน (ZDF) สำหรับตราสารหนี้หรือไม่ _(in Future)_ |
| Calendar              | Select the financial holiday calendar associated with the currency.                  | เลือกปฏิทินวันหยุดทางการเงินที่ผูกกับสกุลเงินนี้                                            |
| Create Button         | Save the configuration and register the currency in the system.                      | ปุ่มสำหรับบันทึกข้อมูลและลงทะเบียนสกุลเงินใหม่                                              |
| Cancel Button         | Discard all current input and return to the main list.                               | ปุ่มสำหรับยกเลิกสิ่งที่กรอกไว้และกลับสู่หน้ารายการหลัก                                      |

For more Details [Definitions #SouthBridge System](https://app.gitbook.com/s/5gU1vMFynoerZN6qaJVE/getting-started/quickstart#southbridge-system "mention")

### Don't forget to approve the action in the Pending Table to finalize the setup of your new currency.
