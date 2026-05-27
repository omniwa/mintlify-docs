---
description: Broker Commission defines the commission rate to apply for each broker.
icon: house-crack
---

# Broker Commission

### Broker Commission

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (304).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                   | **Description (English)**                                                  | **คำอธิบาย (ภาษาไทย)**                                       |
| ------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Broker Code (Search)            | Search for a specific broker's commission structure or historical records. | ช่องสำหรับค้นหาโครงสร้างค่าธรรมเนียมตามรหัสโบรกเกอร์         |
| Create Broker Commission        | Define and register a new commission rate or fee structure.                | ปุ่มสำหรับเริ่มสร้างและตั้งค่าอัตราค่าธรรมเนียมใหม่          |
| Broker Commission Table         | Lists all currently configured commission structures in the system.        | ตารางแสดงรายการโครงสร้างค่าธรรมเนียมทั้งหมดที่มีในระบบ       |
| Preview Button                  | View the specific details, tiers, and effective dates of the commission.   | ปุ่มสำหรับเรียกดูรายละเอียดเชิงลึกและเงื่อนไขของค่าธรรมเนียม |
| Edit Button                     | Modify the rates, calculation methods, or rules of an existing entry.      | ปุ่มสำหรับแก้ไขอัตราหรือเงื่อนไขของค่าธรรมเนียมเดิมที่มีอยู่ |
| Delete Button                   | Remove a commission structure from the system database.                    | ปุ่มสำหรับลบโครงสร้างค่าธรรมเนียมออกจากระบบ                  |
| Pending Broker Commission Table | Commission structures recently added or edited that await approval.        | ตารางแสดงรายการค่าธรรมเนียมที่รอการอนุมัติก่อนเริ่มใช้งาน    |



### Create Broker Commission

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (305).png" alt=""><figcaption></figcaption></figure></div>

| **Component**   | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                             |
| --------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| Broker Code     | Select the unique identifier for the broker.                       | เลือกรหัสโบรกเกอร์ที่ต้องการตั้งค่าค่าธรรมเนียม                    |
| Description     | A brief note describing this commission structure.                 | คำอธิบายสั้น ๆ เกี่ยวกับโครงสร้างค่าธรรมเนียมนี้                   |
| Effective Date  | The official date from which this commission rate starts to apply. | วันที่เริ่มมีผลบังคับใช้อัตราค่าธรรมเนียมนี้                       |
| Range From      | The starting trade value for this specific commission tier.        | มูลค่าการซื้อขายเริ่มต้นของช่วงค่าธรรมเนียมนี้                     |
| Range To        | The upper limit trade value for this specific commission tier.     | มูลค่าการซื้อขายสูงสุดของช่วงค่าธรรมเนียมนี้                       |
| Commission Rate | The percentage or fixed fee charged for trades within this range.  | อัตราค่าธรรมเนียม (เปอร์เซ็นต์หรือค่าธรรมเนียมคงที่) สำหรับช่วงนี้ |
| Add Detail      | Button to include an additional row for another price range.       | ปุ่มสำหรับเพิ่มแถวเพื่อกำหนดช่วงราคาและอัตราค่าธรรมเนียมเพิ่มเติม  |
| Create Button   | Save the commission structure and register it in the system.       | ปุ่มสำหรับบันทึกและลงทะเบียนโครงสร้างค่าธรรมเนียมในระบบ            |
| Cancel Button   | Discard the current input and return to the main list.             | ปุ่มสำหรับยกเลิกสิ่งที่กรอกไว้และกลับไปยังหน้ารายการหลัก           |

### Don't forget to approve the action in the Pending Table to finalize the setup of your new commission rates.



