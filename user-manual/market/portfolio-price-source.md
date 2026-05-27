---
description: >-
  Portfolio Price Source links portfolios to a Price Source so that the system
  can retrieve accurate asset prices for valuation and reporting.
icon: file-brackets-curly
---

# Portfolio Price Source

### Portfolio Price Source

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure></div>

| **Component**      | **Description (English)**                 | **คำอธิบาย (ภาษาไทย)**                                                    |
| ------------------ | ----------------------------------------- | ------------------------------------------------------------------------- |
| Search Box         | Search for an existing record.            | ช่องค้นหาข้อมูลสำหรับรายการที่มีอยู่ในระบบแล้ว                            |
| Create Button      | Add a new Portfolio Price Source.         | ปุ่มสำหรับเพิ่มแหล่งที่มาของราคาพอร์ตโฟลิโอ (Portfolio Price Source) ใหม่ |
| Price Source Table | Lists registered Portfolio Price Source.  | ตารางแสดงรายการแหล่งที่มาของราคาที่ลงทะเบียนเสร็จสมบูรณ์แล้ว              |
| Pending Table      | Portfolio Price Source awaiting approval. | ตารางแสดงรายการแหล่งที่มาของราคาที่อยู่ระหว่างรอการอนุมัติ                |



### Create Portfolio Price Source

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure></div>

| **Field / Button**          | **Description (English)**                                  | **คำอธิบาย (ภาษาไทย)**                                               |
| --------------------------- | ---------------------------------------------------------- | -------------------------------------------------------------------- |
| Portfolio Price Source Code | Unique identifier for the price source setup.              | รหัสอ้างอิงเฉพาะสำหรับการตั้งค่าแหล่งที่มาของราคา                    |
| Description                 | Detailed description of the configuration.                 | รายละเอียดคำอธิบายของการตั้งค่านี้                                   |
| Portfolio Available         | List of portfolios that are available to be linked.        | รายชื่อพอร์ตโฟลิโอที่สามารถนำมาเชื่อมโยงได้                          |
| Move Button ( > )           | Move selected portfolios from "Available" to "Selected".   | ปุ่มสำหรับย้ายพอร์ตโฟลิโอที่เลือกไปยังช่อง "Selected"                |
| Portfolio Selected          | Portfolios currently mapped to this price source.          | รายชื่อพอร์ตโฟลิโอที่ถูกเลือกและจับคู่กับแหล่งที่มาของราคานี้แล้ว    |
| Equity                      | Asset price data associated with the portfolio.            | ข้อมูลราคาของสินทรัพย์ (หุ้น) ที่เกี่ยวข้องกับพอร์ตโฟลิโอ            |
| Price Source                | Reference source used for asset pricing.                   | แหล่งข้อมูลอ้างอิงที่ใช้สำหรับดึงราคาของสินทรัพย์                    |
| Add Source Button           | Add additional price reference sources.                    | ปุ่มสำหรับเพิ่มแหล่งอ้างอิงราคาเพิ่มเติม                             |
| FX Rate & Zero Rate         | Settings for Foreign Exchange and risk-free rates.         | การตั้งค่าอัตราแลกเปลี่ยนเงินตราและอัตราดอกเบี้ยที่ปราศจากความเสี่ยง |
| Create Button               | Save the current mapping and configuration.                | ปุ่มสำหรับบันทึกการจับคู่และการตั้งค่าทั้งหมดลงในระบบ                |
| Cancel Button               | Discard the current entry and return to the previous page. | ปุ่มสำหรับยกเลิกการกรอกข้อมูลและกลับไปยังหน้าก่อนหน้า                |



### Example

{% tabs %}
{% tab title="Equity Tab" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}

{% tab title="FX Rate & Zero Rate Tab" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
#### Tips: Portfolio Management & Price Sources

* Centralized Price Sourcing: Create a primary Portfolio Price Source to serve as your master configuration.
* Scalable Integration: When launching a new portfolio, simply Edit the existing master Price Source and Add the new portfolio to it.
{% endhint %}
