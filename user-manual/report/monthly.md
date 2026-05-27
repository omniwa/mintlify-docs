---
description: >-
  The Monthly Report consolidates end-of-month portfolio data for client
  reporting, providing a comprehensive overview of performance.
icon: file-chart-column
---

# Monthly

### Monthly

{% hint style="info" %}
_**Key data sources:**_&#x20;

* _Daily Performance Report (daily portfolio movements)_
* _End-of-Day (closing balances for month-end valuation) and_
* _The Trial Balance (financial accuracy)._
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                                           | **Description (English)**                                        | **คำอธิบาย (ภาษาไทย)**                                                       |
| ------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Select Date                                             | Reporting date for the monthly data.                             | วันที่ที่ต้องการเรียกดูรายงานประจำเดือน                                      |
| Portfolio Search                                        | Search for a specific portfolio by name.                         | ช่องค้นหาชื่อพอร์ตโฟลิโอที่ต้องการ                                           |
| <p>Indicator<br>(hover mouse over for more details)</p> | Display the status of relevant financial metrics or processes.   | ตัวบ่งชี้สถานะความพร้อมของข้อมูลหรือกระบวนการทางบัญชี                        |
| Clear Filter                                            | Reset all selected indicators and search criteria.               | ปุ่มสำหรับล้างการตั้งค่าตัวกรองทั้งหมดให้กลับเป็นค่าเริ่มต้น                 |
| Download All PDF Button                                 | Export every report in the list as PDF (without password).       | ปุ่มดาวน์โหลดรายงานทั้งหมดในรายการเป็นไฟล์ PDF (แบบไม่ใส่รหัสผ่าน)           |
| Data Table                                              | Lists portfolio details and processing status.                   | ตารางแสดงรายชื่อพอร์ตโฟลิโอและสถานะการประมวลผล                               |
| No Performance Data                                     | Orange icon indicating a missing End-of-Day (EOD) process.       | ไอคอนสีส้ม: บ่งบอกว่ายังไม่มีข้อมูลผลการดำเนินงาน (เนื่องจากยังไม่ได้ทำ EOD) |
| Request Upload TB                                       | Orange paper icon: Submit a request or notify for Trial Balance. | ไอคอนรูปกระดาษสีส้ม: บ่งบอกว่าต้องมีการอัปโหลดไฟล์งบทดลอง (Trial Balance)    |
| Preview Button                                          | Preview the report content on-screen.                            | ปุ่มสำหรับเรียกดูตัวอย่างเนื้อหาในรายงานบนหน้าจอ                             |
| Complete Data                                           | Green checkmark: All required details are present and verified.  | เครื่องหมายถูกสีเขียว: ข้อมูลครบถ้วนสมบูรณ์พร้อมสำหรับการออกรายงาน           |

{% hint style="warning" %}
"No Performance Data"&#x20;

indicates that the End-of-Day (EOD) process has not yet been completed for the selected portfolio on that specific date. Consequently, the system cannot calculate or display performance metrics until the EOD sequence is finalized.
{% endhint %}



### Settings tab

The Settings tab customises which portfolio details are shown in the monthly report. You can toggle Total Investment, Benchmark, High Watermark, Net Investment, Portfolio Detail and Forward Date — independently per portfolio.

<div><figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure></div>



### Paper Settings tab

The Paper Settings tab customises report formatting and adjusts financial details. All calculations reference the Trial Balance (TB) files for accuracy.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure></div>



### Upload TB tab

Upload Trial Balance (TB) file: Use the Upload TB tab to import the Trial Balance file used for monthly reporting.

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
### **TB Template Files**

[Monthly: Trial Balance (TB) Template files](https://app.gitbook.com/s/5gU1vMFynoerZN6qaJVE/info/monthly-trial-balance-tb-template-files "mention")

The system matches data based on the Date and Portfolio Name within the Excel sheet.
{% endhint %}

### Preview TB Tab

Preview Trial Balance (TB) Data

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure></div>



### Example Monthly

{% tabs %}
{% tab title="Page: 1" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}

{% tab title="Page: 2" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}

{% tab title="Page: 3" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}
