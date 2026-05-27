---
description: >-
  Cash In / Out lets you deposit money into a portfolio (Cash In) or withdraw
  money from it (Cash Out).
icon: money-from-bracket
---

# Cash In/Out

The Daily module groups every operational task that the back office runs each business day — cash deposits and withdrawals, posting and closing transactions, importing prices, processing the End-of-Day, and adjusting fees, NAV and available units. The chapter ends with the full Investment Step walkthrough that ties Investment, Dealing and Daily together.



### Cash In / Out

Cash In / Out lets you deposit money into a portfolio (Cash In) or withdraw money from it (Cash Out). The form supports two modes — Input Mode for single transactions and Import Mode for bulk Excel uploads.

### Input Mode

{% tabs %}
{% tab title="Input Mode — Deposit" %}
### Input Mode — Deposit

Mode for single-row deposit data entry.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure></div>



| **Component**       | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                            |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------- |
| TX Type — Deposit   | Marks the transaction specifically as a deposit.             | ระบุประเภทรายการว่าเป็นรายการ "ฝากเงิน"           |
| Trade Date          | The official date when the transaction is initiated.         | วันที่ทำรายการ (Trade Date)                       |
| Settle Date         | The date when the funds are actually moved/settled.          | วันที่ชำระเงินหรือเงินเข้าบัญชีจริง (Settle Date) |
| Portfolio           | The client or internal portfolio receiving the deposit.      | พอร์ตโฟลิโอที่รับรายการฝากเงิน                    |
| Cash Security       | The specific cash account or asset linked to the entry.      | บัญชีเงินสดหรือหลักทรัพย์เงินสดที่ผูกกับรายการนี้ |
| Reference Rate      | The applicable exchange rate for the transaction.            | อัตราแลกเปลี่ยนที่ใช้อ้างอิง (กรณีต่างสกุลเงิน)   |
| Effective Date      | The date the transaction officially takes effect.            | วันที่มีผลบังคับใช้ในระบบ                         |
| Deposit Info ---    | --- Section Header ---                                       | ------------------                                |
| Cash TX Type        | The specific category of cash movement (e.g., Contribution). | ประเภทปลีกย่อยของรายการเงินสด (เช่น เงินสมทบ)     |
| Amount              | The gross deposit amount before taxes or fees.               | จำนวนเงินฝาก (ยอดก่อนหักภาษีหรือค่าธรรมเนียม)     |
| VAT & VAT Amount    | VAT rate and the calculated VAT value.                       | อัตราภาษีมูลค่าเพิ่มและจำนวนเงิน VAT ที่คำนวณได้  |
| TAX & TAX Amount    | Other tax rates and their calculated values.                 | อัตราภาษีอื่น ๆ และจำนวนเงินภาษีที่คำนวณได้       |
| Calc. Settle Amount | The net amount computed by the system.                       | ยอดชำระสุทธิที่ระบบคำนวณให้เบื้องต้น              |
| Settle Amount       | The final confirmed amount after all deductions.             | ยอดชำระสุทธิสุดท้ายที่จะบันทึกเข้าสู่ระบบ         |
| Remark              | Free-text area for additional notes or references.           | ช่องสำหรับกรอกหมายเหตุหรือข้อมูลอ้างอิงเพิ่มเติม  |
| Pin                 | Indicator to pin or flag this transaction for priority.      | สัญลักษณ์ปักหมุดเพื่อทำเครื่องหมายรายการสำคัญ     |
| Reset Button        | Clear all input fields and start over.                       | ปุ่มสำหรับล้างข้อมูลที่กรอกไว้ทั้งหมด             |
| Create Button       | Confirm and submit the deposit to the pending table.         | ปุ่มสำหรับยืนยันการสร้างรายการฝากเงิน             |
{% endtab %}

{% tab title="Input Mode — Withdraw" %}
#### Input Mode — Withdraw

Marks the transaction specifically as a withdrawal.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure></div>



| **Component**       | **Description (English)**                                        | **คำอธิบาย (ภาษาไทย)**                                |
| ------------------- | ---------------------------------------------------------------- | ----------------------------------------------------- |
| Trade Date          | The official date when the withdrawal request is made.           | วันที่ทำรายการถอนเงิน (Trade Date)                    |
| Settle Date         | The date when the funds are actually deducted/settled.           | วันที่เงินถูกหักออกจากบัญชีจริง (Settle Date)         |
| Portfolio           | The client or internal portfolio from which funds are withdrawn. | พอร์ตโฟลิโอต้นทางที่ต้องการถอนเงินออก                 |
| Cash Security       | The specific cash account associated with this withdrawal.       | บัญชีเงินสดที่ผูกกับรายการถอนนี้                      |
| Reference Rate      | The applicable exchange rate for the transaction.                | อัตราแลกเปลี่ยนที่ใช้อ้างอิง (กรณีถอนเงินต่างสกุล)    |
| Effective Date      | The date the transaction officially takes effect in the system.  | วันที่มีผลบังคับใช้ในระบบ                             |
| Withdrawal Info --- | --- Section Header ---                                           | ------------------                                    |
| Cash TX Type        | The specific category of cash outflow (e.g., Fee, Distribution). | ประเภทปลีกย่อยของรายการเงินสด (เช่น จ่ายค่าธรรมเนียม) |
| Amount              | The gross withdrawal amount before taxes or fees.                | จำนวนเงินที่ต้องการถอน (ยอดก่อนหักภาษี)               |
| VAT & VAT Amount    | VAT rate and the calculated VAT value to be included.            | อัตราภาษีมูลค่าเพิ่มและยอดเงิน VAT ที่คำนวณได้        |
| TAX & TAX Amount    | Other applicable tax rates and their calculated values.          | อัตราภาษีอื่น ๆ และยอดเงินภาษีที่คำนวณได้             |
| Calc. Settle Amount | The net deduction amount computed by the system.                 | ยอดเงินหักสุทธิที่ระบบคำนวณให้เบื้องต้น               |
| Settle Amount       | The final confirmed amount to be deducted from the account.      | ยอดหักสุทธิสุดท้ายที่จะบันทึกเข้าสู่ระบบ              |
| Remark              | Free-text area for additional notes or references.               | ช่องสำหรับกรอกหมายเหตุหรือข้อมูลอ้างอิงเพิ่มเติม      |
| Pin                 | Indicator to pin or flag this transaction for priority.          | สัญลักษณ์ปักหมุดเพื่อทำเครื่องหมายรายการสำคัญ         |
| Reset Button        | Clear all input fields and start over.                           | ปุ่มสำหรับล้างข้อมูลที่กรอกไว้ทั้งหมด                 |
| Create Button       | Confirm and submit the withdrawal to the pending table.          | ปุ่มสำหรับยืนยันการสร้างรายการถอนเงิน                 |
{% endtab %}
{% endtabs %}





### Import Mode

Import Mode is used to process Cash In / Out transactions in bulk by uploading an Excel file.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (318).png" alt=""><figcaption></figcaption></figure></div>

| **Component**            | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                            |
| ------------------------ | ------------------------------------------------------------ | ----------------------------------------------------------------- |
| Click or Drag .XLSX file | Area to upload the formatted Excel transaction file.         | พื้นที่สำหรับคลิกหรือลากไฟล์ Excel (.xlsx) เพื่ออัปโหลด           |
| Upload All Valid Rows    | Command to import only the rows that pass system validation. | ปุ่มสำหรับสั่งนำเข้าเฉพาะแถวที่ข้อมูลถูกต้องตามเงื่อนไขระบบ       |
| Download Example File    | Download a template with the correct column headers.         | ลิงก์สำหรับดาวน์โหลดไฟล์ตัวอย่างเพื่อให้กรอกข้อมูลได้ถูกโครงสร้าง |
| Status                   | Real-time tracking of validation and upload progress.        | สถานะการตรวจสอบข้อมูลและความคืบหน้าในการนำเข้า                    |
| Pending Import           | Status indicating the file is in the queue for processing.   | สถานะที่ระบุว่าไฟล์กำลังรอการประมวลผลจากระบบ                      |
| Successful Import        | Confirmation that all valid data has been registered.        | สถานะยืนยันว่าการนำเข้าข้อมูลเสร็จสมบูรณ์                         |





