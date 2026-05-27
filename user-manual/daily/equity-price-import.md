---
description: >-
  Equity Price Import brings closing equity prices into Level11 so that NAV and
  other valuations are always up to date.
icon: file-import
---

# Equity Price Import

### Equity Price Import

{% tabs %}
{% tab title="Import Mode" %}
### Import Mode

Mode for batch price updates using external files.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (322).png" alt=""><figcaption></figcaption></figure></div>



| **Component**            | **Description (English)**                                       | **คำอธิบาย (ภาษาไทย)**                                           |
| ------------------------ | --------------------------------------------------------------- | ---------------------------------------------------------------- |
| Click or Drag .XLSX file | Area to upload the formatted Excel price file.                  | พื้นที่สำหรับคลิกหรือลากไฟล์ Excel (.xlsx) เพื่ออัปโหลด          |
| Upload Button            | Execute the data transfer from the file to the system.          | ปุ่มสำหรับยืนยันการนำข้อมูลจากไฟล์เข้าสู่ระบบ                    |
| Download Example File    | Download the standard template with correct headers.            | ลิงก์สำหรับดาวน์โหลดไฟล์ตัวอย่างเพื่อให้กรอกข้อมูลราคาได้ถูกต้อง |
| Table Display            | Preview and verify the imported prices before final processing. | ตารางแสดงรายการราคาที่นำเข้าเพื่อตรวจสอบความถูกต้อง              |
{% endtab %}

{% tab title="Input Mode" %}
### Input Mode

Input Mode allows you to enter equity prices manually for quick day-to-day updates.

Switch to manual data entry mode for individual equity prices.

<div><figure><img src="../.gitbook/assets/image (323).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (324).png" alt=""><figcaption></figcaption></figure></div>



| **Component** | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                              |
| ------------- | ------------------------------------------------------------------ | --------------------------------------------------- |
| Date          | The specific trading date for which the price is being recorded.   | วันที่ของราคาหลักทรัพย์ที่ต้องการบันทึก             |
| Price Code    | The unique identifier or ticker for the specific asset.            | รหัสอ้างอิงราคาหรือชื่อหุ้นที่ต้องการระบุราคา       |
| Open          | The price at which the security first traded on this day.          | ราคาเปิดตลาดของวันนั้น ๆ                            |
| Close         | The final price at which the security traded for the day.          | ราคาปิดตลาด (ใช้สำหรับการประเมินมูลค่าพอร์ต)        |
| High          | The highest price the security reached during the trading session. | ราคาสูงสุดของวัน                                    |
| Low           | The lowest price the security reached during the trading session.  | ราคาต่ำสุดของวัน                                    |
| Alpha         | A measure of the security's performance relative to a benchmark.   | ค่าอัลฟา (ตัวบ่งชี้ประสิทธิภาพเทียบกับดัชนีอ้างอิง) |
| Beta          | A measure of the security's volatility relative to the market.     | ค่าเบต้า (ตัวบ่งชี้ความผันผวนเทียบกับตลาด)          |
| Volume        | The total number of shares traded during the session.              | ปริมาณการซื้อขายรวมของวันนั้น                       |
| Submit Button | Commit the manual price entry and save it to the database.         | ปุ่มสำหรับยืนยันและบันทึกข้อมูลราคาเข้าสู่ระบบ      |
{% endtab %}
{% endtabs %}



{% hint style="warning" %}
Don't forget to check the Date twice before submitting, as entering a price for the wrong day can significantly distort your historical performance charts.
{% endhint %}



