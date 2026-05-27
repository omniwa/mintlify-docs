---
description: >-
  Churning measures excessive or frequent buying and selling of securities. The
  report helps compliance teams detect over-trading patterns that may not be in
  the client’s best interest.
icon: file-lines
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Churning

### Churning

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (134).png" alt=""><figcaption></figcaption></figure></div>

| **Component**         | **Description (English)**                            | **คำอธิบาย (ภาษาไทย)**                                    |
| --------------------- | ---------------------------------------------------- | --------------------------------------------------------- |
| Dates                 | Reporting date.                                      | วันที่ที่ต้องการใช้ในการออกรายงาน                         |
| Portfolio Group       | Portfolio Group filter.                              | ตัวกรองสำหรับเลือกกลุ่มของพอร์ตโฟลิโอ                     |
| Show Closed Portfolio | Include closed portfolios in the list.               | ตัวเลือกสำหรับรวมพอร์ตโฟลิโอที่ปิดไปแล้วเข้ามาในรายการ    |
| Portfolio Available   | Available portfolios that can be selected.           | รายชื่อพอร์ตโฟลิโอทั้งหมดที่สามารถเลือกมาออกรายงานได้     |
| Button >              | Move the highlighted portfolio to the Selected list. | ปุ่มสำหรับย้ายพอร์ตโฟลิโอที่ต้องการไปยังรายการ "Selected" |
| Portfolio Selected    | Portfolios that will be reported on.                 | รายชื่อพอร์ตโฟลิโอที่จะถูกนำมาแสดงผลในรายงาน              |
| Title                 | Main heading of the report.                          | หัวข้อหลักที่จะปรากฏบนหัวรายงาน                           |
| Check Value           | Verify or review computed values.                    | ส่วนสำหรับการตรวจสอบหรือทบทวนค่าที่คำนวณได้               |
| Search Button         | Run the search based on selected filters.            | ปุ่มสำหรับกดเพื่อเริ่มค้นหาและสร้างรายงานตามเงื่อนไข      |
| Export Excel Button   | Download the report to Excel.                        | ปุ่มสำหรับดาวน์โหลดรายงานในรูปแบบไฟล์ Excel               |
| Data Table            | Table that displays the search results.              | ตารางที่แสดงผลลัพธ์ของข้อมูลจากการค้นหา                   |



### **Formula**

Churning (turnover ratio) = Cost Amount ÷ Average NAV.

<figure><img src="../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

### **Cost Amount calculation**

{% stepper %}
{% step %}
#### Navigate to Enquiry ▸ History Transaction.


{% endstep %}

{% step %}
#### Set the Trade Date to the same date used in the Churning report.


{% endstep %}

{% step %}
#### Select the desired Portfolios and set the Security Class to "Equity".


{% endstep %}

{% step %}
#### Sum the values in the Cost column. The total is the Cost Amount.


{% endstep %}
{% endstepper %}

### **Average NAV calculation**

{% stepper %}
{% step %}
#### &#x20;Navigate to Report ▸ NAV Summary.


{% endstep %}

{% step %}
#### Select the date that matches the Churning date and click the search button.


{% endstep %}

{% step %}
#### Download the Excel file.


{% endstep %}

{% step %}
#### In Excel, apply the AVERAGE function to the NAV column to obtain the Average NAV.


{% endstep %}
{% endstepper %}
