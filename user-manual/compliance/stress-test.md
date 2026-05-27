---
icon: file-lines
---

# Stress Test

### Stress Test

The Stress Test simulates a market downturn (Test Value of −X%) and evaluates the percentage of loss for the selected portfolios.

{% hint style="info" %}
_Related data: Beta Report._
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (198).png" alt=""><figcaption></figcaption></figure></div>

| **Component**         | **Description (English)**                                      | **คำอธิบาย (ภาษาไทย)**                                      |
| --------------------- | -------------------------------------------------------------- | ----------------------------------------------------------- |
| Dates                 | Reporting date for the analysis.                               | วันที่ที่ต้องการใช้เป็นฐานในการจำลองสถานการณ์               |
| Portfolio Group       | Filter to select a specific group of portfolios.               | ตัวกรองสำหรับเลือกกลุ่มของพอร์ตโฟลิโอ                       |
| Show Closed Portfolio | Include portfolios that have been closed in the analysis.      | ตัวเลือกสำหรับรวมพอร์ตโฟลิโอที่ปิดไปแล้วเข้ามาในการทดสอบ    |
| Portfolio Available   | List of portfolios available for selection.                    | รายชื่อพอร์ตโฟลิโอทั้งหมดที่สามารถเลือกมาทำ Stress Test ได้ |
| Button >              | Move the highlighted portfolios to the Selected list.          | ปุ่มสำหรับย้ายพอร์ตโฟลิโอที่เลือกไปยังรายการ "Selected"     |
| Portfolio Selected    | Portfolios chosen for the scenario analysis.                   | รายชื่อพอร์ตโฟลิโอที่จะถูกนำไปคำนวณผลกระทบ                  |
| Assumption            | Title or name of the simulated scenario.                       | ชื่อของสมมติฐานหรือเหตุการณ์จำลอง (เช่น Market Crash)       |
| Test Value            | Defines the market test condition (e.g., negative percentage). | ค่าที่ใช้ทดสอบ (เช่น ระบุค่าติดลบเพื่อจำลองสภาวะตลาดขาลง)   |
| Search Button         | Run the scenario analysis based on the settings.               | ปุ่มสำหรับเริ่มการคำนวณผลกระทบตามสมมติฐานที่ตั้งไว้         |
| Export Excel Button   | Download the analysis results to an Excel file.                | ปุ่มสำหรับดาวน์โหลดรายงานการจำลองสถานการณ์ในรูปแบบ Excel    |



### Example Downloaded File

{% tabs %}
{% tab title="Portfolio Data" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (199).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}

{% tab title="Raw Data" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (200).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}

{% tab title="Stress Test" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (201).png" alt=""><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}
