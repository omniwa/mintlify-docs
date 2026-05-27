---
description: >-
  Portfolio is used to create and manage customer investment portfolios within
  the system.
icon: briefcase
---

# Portfolio

### Portfolio

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (277).png" alt=""><figcaption></figcaption></figure></div>

| **Component**           | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                                    |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------- |
| Portfolio Code (Search) | Search for an existing portfolio by its unique code.         | ช่องสำหรับค้นหาพอร์ตโฟลิโอที่มีอยู่แล้วด้วยรหัสพอร์ต                      |
| Create Portfolio Preset | Create a preset configuration to standardize new portfolios. | การสร้างค่าตั้งต้น (Preset) เพื่อใช้เป็นแม่แบบในการสร้างพอร์ตใหม่         |
| Create Portfolio        | Generate and register a new portfolio in the system.         | ปุ่มสำหรับสร้างและลงทะเบียนพอร์ตโฟลิโอใหม่เข้าระบบ                        |
| Portfolio Table         | Lists all active and existing portfolios.                    | ตารางแสดงรายชื่อพอร์ตโฟลิโอทั้งหมดที่มีอยู่ในปัจจุบัน                     |
| Preview Button          | View detailed portfolio information in read-only mode.       | ปุ่มสำหรับเรียกดูรายละเอียดข้อมูลพอร์ตโฟลิโอ (ก่อนการแก้ไข)               |
| Edit Button             | Modify settings or details of an existing portfolio.         | ปุ่มสำหรับแก้ไขการตั้งค่าหรือข้อมูลของพอร์ตโฟลิโอเดิมที่มีอยู่            |
| Delete Button           | Remove a selected portfolio from the system.                 | ปุ่มสำหรับลบพอร์ตโฟลิโอออกจากระบบ                                         |
| Pending Portfolio Table | Lists portfolios awaiting approval or final completion.      | ตารางแสดงพอร์ตโฟลิโอที่อยู่ระหว่างรอการอนุมัติหรือยังสร้างไม่เสร็จสมบูรณ์ |



### Create Portfolio

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (278).png" alt=""><figcaption></figcaption></figure></div>

#### Identification

| **Component**        | **Description (English)**                                          | **คำอธิบาย (ภาษาไทย)**                                     |
| -------------------- | ------------------------------------------------------------------ | ---------------------------------------------------------- |
| From Preset          | Choose a predefined portfolio configuration as a starting point.   | เลือกค่าตั้งต้น (Preset) เพื่อใช้เป็นแม่แบบในการกรอกข้อมูล |
| Portfolio Code       | Unique identifier used to track the portfolio.                     | รหัสพอร์ตโฟลิโอสำหรับใช้ระบุและติดตามข้อมูลในระบบ          |
| Description          | Additional descriptive notes about the portfolio.                  | รายละเอียดเพิ่มเติมเกี่ยวกับพอร์ตโฟลิโอ                    |
| Tax ID               | Official taxpayer identification number.                           | เลขประจำตัวผู้เสียภาษีอากร                                 |
| Owner                | Select the entity that owns the portfolio.                         | รายชื่อเจ้าของพอร์ตโฟลิโอ                                  |
| Individual / Company | Mark whether the portfolio belongs to a person or an organization. | ระบุประเภทเจ้าของพอร์ต (บุคคลธรรมดา หรือ นิติบุคคล)        |
| EQ W/H Tax Rate      | Withholding tax rate for equity transactions.                      | อัตราภาษีหัก ณ ที่จ่าย สำหรับการทำธุรกรรมหุ้น              |
| Custodian            | Entity responsible for asset safekeeping.                          | ผู้ดูแลรักษาทรัพย์สินของพอร์ต                              |
| Registrar            | Entity that maintains portfolio records.                           | นายทะเบียนผู้ถือหน่วยหรือผู้ดูแลทะเบียนพอร์ต               |
| Trustee              | Oversees compliance and fund management.                           | ทรัสตีหรือผู้ดูแลผลประโยชน์                                |
| Auditor              | Entity that conducts financial reviews.                            | ผู้สอบบัญชีของพอร์ตโฟลิโอ                                  |

#### Investment Configuration

| **Component**       | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                                 |
| ------------------- | ------------------------------------------------------------- | ------------------------------------------------------ |
| Portfolio Type      | Investment strategy or asset-allocation category.             | ประเภทของพอร์ต (เช่น Private Fund)                     |
| Issue Par           | Initial asset pricing (typically set to 10.00).               | ราคาพาร์เริ่มต้นของหน่วยลงทุน                          |
| Start Date          | Official portfolio commencement date.                         | วันที่เริ่มต้นจัดตั้งพอร์ตโฟลิโอ                       |
| End Date            | Date when the portfolio is closed or finalized.               | วันที่สิ้นสุดหรือปิดพอร์ตโฟลิโอ                        |
| Selling Rule        | Conditions or method used for selling assets (e.g., Average). | กฎการเลือกต้นทุนในการขายสินทรัพย์                      |
| Amortized           | Method for calculating amortized cost over time.              | วิธีการคำนวณราคาแบบตัดจำหน่าย (Amortized)              |
| Cost Calculation    | Method used to compute total portfolio costs.                 | วิธีการคำนวณต้นทุน (เช่น รวมค่าธรรมเนียมและ VAT)       |
| Starting Fund       | Initial capital amount allocated to the portfolio.            | จำนวนเงินทุนเริ่มต้นของพอร์ตโฟลิโอ                     |
| Equalization Calc   | Formula to ensure balanced distribution across holdings.      | วิธีการคำนวณส่วนเฉลี่ยเงินรับจ่าย (Equalization)       |
| Base Currency       | Primary currency the portfolio operates in.                   | สกุลเงินหลักที่ใช้ดำเนินงานในพอร์ต                     |
| Cross Currency      | Currency used for transaction conversions.                    | สกุลเงินที่ใช้ในการแลกเปลี่ยนหรือเทียบเคียง            |
| Report NAV Currency | Official currency used for NAV reporting.                     | สกุลเงินที่ใช้แสดงผลในรายงานมูลค่าทรัพย์สินสุทธิ (NAV) |
| Account Std.        | Standardized accounting framework for tracking.               | <p></p><p>มาตรฐานการบัญชีที่ใช้ในการบันทึกข้อมูล</p>   |

| **Component** | **Description (English)**                       | **คำอธิบาย (ภาษาไทย)**             |
| ------------- | ----------------------------------------------- | ---------------------------------- |
| Create Button | Confirm and register the new portfolio.         | ปุ่มยืนยันการสร้างพอร์ตโฟลิโอใหม่  |
| Cancel Button | Discard the current setup and close the window. | ปุ่มยกเลิกการตั้งค่าและปิดหน้าต่าง |

{% hint style="info" %}
## Currency Consistency

It is highly recommended to set the Base, Cross, and Report NAV Currency to the **same currency** (matching the primary currency used for actual reporting). This ensures data consistency and prevents calculation confusion within Performance Reports.
{% endhint %}

### Don't forget to approve the actions in the Pending Table to finalize the process.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure></div>
