---
description: >-
  Value at Risk (VaR) simulates how much a portfolio might lose under adverse
  market conditions. Portfolios shown in bold are eligible for VaR report
  generation.
icon: rectangle-history
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

# VaR

### VaR

{% hint style="info" %}
_Related data: Equity Price — used as the key input because it reflects the value and volatility of equities held in the portfolio._
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                    | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                                                    |
| -------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Dates                            | Reporting date.                                               | วันที่ที่ต้องการสรุปข้อมูลรายงาน                                          |
| (Union) Calendar                 | Show only common business days across all selected countries. | ปฏิทินรวม: แสดงเฉพาะวันที่เป็นวันทำการร่วมกันของทุกประเทศที่เลือก         |
| Portfolio Group                  | Group of portfolios for risk analysis.                        | กลุ่มของพอร์ตโฟลิโอที่ต้องการนำมาวิเคราะห์ความเสี่ยง                      |
| Show Closed Portfolio            | Include closed portfolios in the analysis.                    | ตัวเลือกสำหรับรวมพอร์ตโฟลิโอที่ปิดไปแล้วเข้ามาในการคำนวณ                  |
| Portfolio Available              | Available portfolios. (Click to download list)                | รายชื่อพอร์ตโฟลิโอที่สามารถเลือกได้ (ตัวหนา: สามารถกดดาวน์โหลดรายชื่อได้) |
| Button >                         | Move the highlighted portfolio to the Selected list.          | ปุ่มสำหรับย้ายพอร์ตโฟลิโอที่เลือกไปยังรายการ "Selected"                   |
| Portfolio Selected               | Portfolios that will be included in the VaR report.           | รายชื่อพอร์ตโฟลิโอที่จะถูกนำไปคำนวณค่า VaR                                |
| Confidence Level                 | Confidence level — typically 99%.                             | ระดับความเชื่อมั่นในการวัดความเสี่ยง (โดยทั่วไปคือ 99%)                   |
| Observation Days                 | Historical days used in the VaR calculation.                  | จำนวนวันย้อนหลัง (Look-back period) ที่ใช้ในการคำนวณ                      |
| Price Sources                    | Data providers for closing prices.                            | แหล่งข้อมูลราคาปิด (Data Providers) ที่ใช้เป็นฐานข้อมูล                   |
| Asset Types                      | Classification of securities (e.g., Equity).                  | ประเภทของสินทรัพย์ที่นำมาวิเคราะห์ (เช่น หุ้นทุน)                         |
| Download Excel Button            | Download the final VaR report.                                | ปุ่มสำหรับดาวน์โหลดรายงาน VaR ในรูปแบบไฟล์ Excel                          |
| Download Fillable Price Template | Excel template for manual price input for VaR calculation.    | เทมเพลตสำหรับกรอกราคาด้วยตนเอง (ส่งผลเฉพาะการคำนวณ VaR เท่านั้น)          |

***

### VaR Backtesting

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure></div>

| **Component**      | **Description (English)**                                                                    | **คำอธิบาย (ภาษาไทย)**                                                                                           |
| ------------------ | -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| P\&L Type (Clean)  | Calculates Profit and Loss without any cash component.                                       | ประเภทกำไร/ขาดทุน (Clean): คำนวณเฉพาะผลกำไรขาดทุนจากการเปลี่ยนแปลงของราคา โดยไม่รวมรายการเงินสด                  |
| Backtest Statistic | “Basel” is selectable only when both Backtesting Window and Observation Days are ≥ 250 days. | สถิติการทดสอบย้อนหลัง: สามารถเลือก “Basel” ได้ก็ต่อเมื่อกำหนดช่วงเวลาการทดสอบและวันย้อนหลังตั้งแต่ 250 วันขึ้นไป |
| Backtesting Window | Number of historical days used to evaluate the accuracy of the VaR model.                    | ช่วงเวลาการทดสอบย้อนหลัง: จำนวนวันย้อนหลังที่ใช้ในการประเมินความแม่นยำของโมเดล VaR                               |

***

### Import

For import '**Fillable Price Template**' Excel.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (174).png" alt=""><figcaption></figcaption></figure></div>

{% hint style="info" %}
#### **Note** **The** **equity prices** uploaded via the **Fillable Price Template** (Excel) are exclusively designated for the **VaR** menu. This data is used solely for risk assessment calculations and will **not affect** portfolio valuations, EOD settlements, or any other reporting modules within the SouthBridge system.
{% endhint %}
