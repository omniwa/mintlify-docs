---
description: >-
  Post Allocation is the gate where the back office reviews each allocation,
  fixes any leftover detail and finally confirms it for posting to the books.
icon: ballot-check
---

# Post Allocation

### Post Allocation



| **Component**  | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                           |
| -------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| Date Options   | Toggle filter between Create Date or Trade Date.             | เลือกกรองข้อมูลตามวันที่สร้างรายการ หรือวันที่ทำรายการซื้อขาย    |
| Date Selection | Calendar tool to specify the date range for orders.          | เครื่องมือปฏิทินสำหรับระบุช่วงวันที่ที่ต้องการตรวจสอบ            |
| Columns        | Customize and adjust visible data columns in the table.      | ปรับแต่งการแสดงผลคอลัมน์ข้อมูลในตารางตามความต้องการ              |
| Filters        | Advanced tools to refine and search specific displayed data. | เครื่องมือกรองข้อมูลขั้นสูงเพื่อค้นหาธุรกรรมที่เจาะจง            |
| Grouping       | Categorize transactions (e.g., by Portfolio or Security).    | การจัดกลุ่มรายการ (เช่น จัดกลุ่มตามพอร์ต หรือตามรหัสหลักทรัพย์)  |
| Order Table    | Main list displaying all processed investment orders.        | ตารางหลักที่แสดงรายการคำสั่งซื้อขายทั้งหมดที่ผ่านการประมวลผลแล้ว |
| Status \[YES]  | Green indicator showing the order is fully Confirmed.        | สัญลักษณ์สีเขียวแสดงว่ารายการได้รับการยืนยันเรียบร้อยแล้ว        |
| Delete Button  | Remove a transaction from the list (if permitted).           | ปุ่มสำหรับลบรายการออกจากระบบ                                     |
| Preview Button | View full transaction details without entering edit mode.    | ปุ่มสำหรับดูรายละเอียดของรายการโดยรวม                            |
| Status \[NO]   | Red indicator showing the order is Unconfirmed.              | สัญลักษณ์สีแดงแสดงว่ารายการยังไม่ได้รับการยืนยัน                 |
| Confirm Button | Finalize and lock the order for further processing.          | ปุ่มสำหรับกดยืนยันรายการให้เสร็จสมบูรณ์                          |
| Edit Button    | Modify order details before the final confirmation.          | ปุ่มสำหรับแก้ไขรายละเอียดข้อมูลก่อนการยืนยัน                     |





### Edit TX in Post Allocation



| **Component**    | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                       |
| ---------------- | ------------------------------------------------------------------ | ------------------------------------------------------------ |
| Allocation ID    | A unique system-generated identifier for the specific transaction. | รหัสอ้างอิงเฉพาะของรายการจัดสรรนั้น ๆ ในระบบ                 |
| Type             | The nature of the transaction, such as Buy or Sell.                | ประเภทของรายการ (ซื้อ หรือ ขาย)                              |
| Security Code    | The ticker symbol or code of the security being traded.            | รหัสหรือชื่อย่อของหลักทรัพย์ที่มีการซื้อขาย                  |
| Broker           | The brokerage firm that executed the trade.                        | ชื่อบริษัทหลักทรัพย์ (โบรกเกอร์) ที่ทำรายการ                 |
| Portfolio        | The specific investment portfolio linked to this allocation.       | พอร์ตโฟลิโอการลงทุนที่ผูกติดกับรายการจัดสรรนี้               |
| Cash Security    | The associated cash account or security for funding/proceeds.      | บัญชีเงินสดหรือหลักทรัพย์เงินสดที่เกี่ยวข้องกับรายการ        |
| Key Dates        | Includes Trade Date, Settle Date, and Tradable Date.               | วันที่สำคัญ: วันที่เทรด, วันที่ชำระราคา และวันที่เริ่มขายได้ |
| Cost Per Unit    | The execution price or cost per single unit of the security.       | ราคาหรือต้นทุนต่อหนึ่งหน่วยของหลักทรัพย์                     |
| Units & Cost     | The quantity of units traded and the total gross cost.             | จำนวนหน่วยที่ซื้อขายและรวมยอดต้นทุนเบื้องต้น                 |
| Commission & VAT | Brokerage fees and Value Added Tax applied to the trade.           | ค่าธรรมเนียมการซื้อขาย (ค่าคอมมิชชั่น) และภาษีมูลค่าเพิ่ม    |
| Settle Amount    | The final amount required for settlement (Gross Cost + Fees).      | ยอดเงินรวมที่ต้องชำระราคา (รวมค่าธรรมเนียมต่าง ๆ)            |
| WHT Rate / Amt   | Withholding Tax percentage and the calculated tax amount.          | อัตราและจำนวนเงินภาษีหัก ณ ที่จ่าย (ถ้ามี)                   |
| Net Amount       | The final net value of the transaction after all deductions.       | ยอดเงินสุทธิสุดท้ายของรายการหลังจากหัก/รวมทุกอย่างแล้ว       |
| Cost Transferred | The specific cost amount transferred for accounting purposes.      | จำนวนต้นทุนที่มีการโอนย้ายเพื่อบันทึกทางบัญชี                |
| Cancel / Edit    | Action buttons to discard changes or save modifications.           | ปุ่มสำหรับยกเลิกการแก้ไข หรือบันทึกการเปลี่ยนแปลง            |



