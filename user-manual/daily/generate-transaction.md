---
description: >-
  Generate Transaction creates investment transactions automatically from
  corporate actions, ensuring that XR/XE/Convert events flow into the books with
  no manual data entry.
icon: square-plus
---

# Generate Transaction

### Generate Transaction

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure></div>

| **Component**             | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                 |
| ------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------ |
| X-Type / X-Date (Filter)  | Search criteria for corporate action events (e.g., XD, XR).        | ค้นหารายการสิทธิประโยชน์ตามประเภทเครื่องหมายหรือวันที่ |
| Active Corporate Action   | Lists all pending CA events that are ready for processing.         | ตารางแสดงรายการสิทธิประโยชน์ที่กำลังดำเนินการอยู่      |
| X-Type / X-Date (Event)   | Specific type and effective date for the selected CA event.        | ประเภทและวันที่ขึ้นเครื่องหมายของรายการที่เลือก        |
| Security Code             | The specific asset providing the corporate action.                 | รหัสหลักทรัพย์ที่ให้สิทธิประโยชน์แก่ผู้ถือ             |
| Resolution / Book Closed  | Official dates for legal resolution and shareholder registry.      | วันที่มีมติคณะกรรมการและวันปิดสมุดทะเบียนผู้ถือหุ้น    |
| Dividend Type / Interval  | Defines if the payout is Cash/Stock and its frequency.             | ระบุว่าเป็นปันผลเงินสดหรือหุ้น และรอบการจ่ายปันผล      |
| Payment Period            | The designated timeframe for distributing the benefits.            | ช่วงเวลาที่ทำการจ่ายเงินปันผลหรือส่งมอบหุ้นปันผล       |
| Ratio / Price             | Numerical formula: Units held vs. Benefits received.               | อัตราส่วนที่ได้รับสิทธิและราคาอ้างอิงที่ใช้คำนวณ       |
| Portfolio Breakdown Table | List of portfolios eligible for this corporate action.             | รายชื่อพอร์ตโฟลิโอที่มีสิทธิได้รับประโยชน์ในครั้งนี้   |
| Has Tx / Tx ID            | Shows if the transaction has been created and its ID.              | สถานะตรวจสอบว่ามีการสร้างรายการไปแล้วหรือยัง           |
| Unit / Right Unit         | Current holdings vs. the calculated benefit amount.                | จำนวนหน่วยที่ถือครองเทียบกับจำนวนสิทธิที่ได้รับคำนวณ   |
| Generate Tx Button        | Triggers the creation of transactions for all selected portfolios. | ปุ่มสำหรับสั่งสร้างรายการธุรกรรมลงในพอร์ตโฟลิโอทั้งหมด |



