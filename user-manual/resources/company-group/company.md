---
description: >-
  Company holds foundational data for each registered entity. These records are
  referenced everywhere — Issuer, Equity, Broker, Custodian, Bank, etc.
icon: building
---

# Company

### Company

<figure><img src="../../.gitbook/assets/image (287).png" alt=""><figcaption></figcaption></figure>

| **Component**         | **Description (English)**                                           | **คำอธิบาย (ภาษาไทย)**                                              |
| --------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Company Code (Search) | Search for a registered company using its unique code.              | ช่องสำหรับค้นหาบริษัทที่ลงทะเบียนไว้ด้วยรหัสบริษัท                  |
| Create Company Button | Open the setup to register a new company entity.                    | ปุ่มสำหรับเริ่มลงทะเบียนและเพิ่มข้อมูลบริษัทใหม่                    |
| Company Table         | Lists all companies currently registered in the system.             | ตารางแสดงรายชื่อบริษัททั้งหมดที่ลงทะเบียนไว้ในระบบ                  |
| Preview Button        | View the complete profile and information of the company.           | ปุ่มสำหรับเรียกดูข้อมูลโดยละเอียดและโปรไฟล์ของบริษัท                |
| Edit Button           | Modify the details or settings of an existing company.              | ปุ่มสำหรับแก้ไขข้อมูลหรือการตั้งค่าของบริษัทเดิมที่มีอยู่           |
| Delete Button         | Remove a company's record from the system.                          | ปุ่มสำหรับลบข้อมูลบริษัทออกจากระบบ                                  |
| Pending Company Table | Companies that have been added or edited and are awaiting approval. | ตารางแสดงรายชื่อบริษัทที่อยู่ระหว่างรอการอนุมัติก่อนเริ่มใช้งานจริง |



### Create Company

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (288).png" alt=""><figcaption></figcaption></figure></div>

{% tabs %}
{% tab title="Identity & Classification" %}
#### Identity & Classification

| **Component**                 | **Description (English)**                                             | **คำอธิบาย (ภาษาไทย)**                                    |
| ----------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------- |
| Company Code                  | A unique identifier for the company within the system.                | รหัสเฉพาะสำหรับระบุบริษัทในระบบ                           |
| Extra Codes                   | Additional reference codes for internal tracking or external mapping. | รหัสอ้างอิงเพิ่มเติมสำหรับใช้ภายในหรือเชื่อมโยงระบบภายนอก |
| Company Name / Reporting Name | The official legal name and the name used specifically for reports.   | ชื่อจดทะเบียนอย่างเป็นทางการ และชื่อที่จะให้ปรากฏในรายงาน |
| Subsidiary Of                 | Indicates the parent company, if this entity is a subsidiary.         | ระบุชื่อบริษัทแม่ (ในกรณีที่เป็นบริษัทในเครือ)            |
| Institute                     | The associated institution or governing entity.                       | สถาบันหรือหน่วยงานที่เกี่ยวข้อง                           |
| Sector                        | The business sector the company operates in.                          | หมวดหมู่ธุรกิจของบริษัท                                   |
| Business Code                 | An industry-standard code for business classification.                | รหัสประเภทธุรกิจตามมาตรฐานสากลหรือมาตรฐานอุตสาหกรรม       |
{% endtab %}

{% tab title="Registration & Tax" %}
#### Registration & Tax

| **Component** | **Description (English)**                   | **คำอธิบาย (ภาษาไทย)**     |
| ------------- | ------------------------------------------- | -------------------------- |
| Registered ID | The official corporate registration number. | เลขทะเบียนนิติบุคคล        |
| Tax ID        | The official tax identification number.     | เลขประจำตัวผู้เสียภาษีอากร |
{% endtab %}

{% tab title="Contact Information" %}
#### Contact Information

| **Component**                   | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                             |
| ------------------------------- | ------------------------------------------------------------- | -------------------------------------------------- |
| Address / Billing Address       | The physical location and the designated address for billing. | ที่อยู่สำนักงานและที่อยู่สำหรับส่งเอกสารใบแจ้งหนี้ |
| City / State / Postal / Country | Detailed location components for the company address.         | ข้อมูลจังหวัด, รัฐ, รหัสไปรษณีย์ และประเทศ         |
| Phone Number / Fax Number       | Primary contact phone and fax lines.                          | หมายเลขโทรศัพท์และหมายเลขโทรสาร                    |
| Contact Name                    | The primary person to contact within the company.             | ชื่อผู้ติดต่อประสานงานหลัก                         |
| Email Address                   | The official contact email for correspondence.                | ที่อยู่อีเมลสำหรับการติดต่อสื่อสาร                 |
| Notes                           | Additional free-text information or internal reminders.       | หมายเหตุหรือข้อมูลเพิ่มเติมอื่น ๆ                  |
{% endtab %}
{% endtabs %}

| **Component** | **Description (English)**                               | **คำอธิบาย (ภาษาไทย)**                        |
| ------------- | ------------------------------------------------------- | --------------------------------------------- |
| Create Button | Save the company profile and register it in the system. | ปุ่มสำหรับบันทึกและลงทะเบียนโปรไฟล์บริษัท     |
| Cancel Button | Discard all current input and close the setup.          | ปุ่มยกเลิกสิ่งที่กรอกไว้ทั้งหมดและปิดหน้าต่าง |

### Don't forget to approve the action in the Pending Table to finalize the registration of your new company.





{% hint style="warning" %}
### Country Configuration for Concentration Rules

Please ensure that the Country is correctly specified in the company profile. This setting is directly used for the Concentration Rule in the Investment Matrix (Fund Manager). If the country is not set, the equity associated with this company will be categorized under 'No Country'.
{% endhint %}



