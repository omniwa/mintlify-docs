---
description: >-
  App Configuration is the place where admin set the global defaults that the
  rest of SouthBridge reads — company branding, default rates, security policy,
  FX security types and other global flags.
icon: screwdriver-wrench
---

# App Configuration

### App Configuration

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure></div>

### Company & Rate

{% tabs %}
{% tab title="Company" %}
| **Field**     | **Description (English)**                 | **คำอธิบาย (ภาษาไทย)**                     |
| ------------- | ----------------------------------------- | ------------------------------------------ |
| COMPANY\_NAME | Company name printed in report headers.   | ชื่อบริษัทที่จะปรากฏบนส่วนหัวของรายงาน     |
| LOGO          | Company logo (minimum size 600 × 300 px). | โลโก้บริษัท (ขนาดขั้นต่ำ 600 × 300 พิกเซล) |
| WATERMARK     | Company watermark used in reports.        | ลายน้ำของบริษัทสำหรับใช้ในรายงาน           |


{% endtab %}

{% tab title="Rate" %}
| **Field**                 | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                           |
| ------------------------- | ------------------------------------------------------------ | ------------------------------------------------ |
| DEFAULT\_COMMISSION\_RATE | Default broker commission rate, expressed in percentage (%). | อัตราค่าธรรมเนียมโบรกเกอร์เริ่มต้น (หน่วยเป็น %) |
| DEFAULT\_VAT              | Default Value Added Tax (VAT) rate.                          | อัตราภาษีมูลค่าเพิ่มเริ่มต้น                     |
| DEFAULT\_WHT              | Default Withholding Tax (WHT) rate.                          | อัตราภาษีหัก ณ ที่จ่ายเริ่มต้น                   |

{% hint style="info" %}
Rate 1.00 = 100%
{% endhint %}
{% endtab %}
{% endtabs %}



<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure></div>

### Security & Resource

{% tabs %}
{% tab title="Security" %}
| **Field**                                 | **Description (English)**                                           | **คำอธิบาย (ภาษาไทย)**                                                              |
| ----------------------------------------- | ------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| RESET\_PASSWORD\_TOKEN\_EXPIRES\_DURATION | Number of days a reset-password token stays valid.                  | จำนวนวันที่โทเค็นสำหรับการตั้งค่ารหัสผ่านใหม่จะมีผลใช้งานได้                        |
| MAX\_SAME\_PASSWORD\_COUNT                | Max number of identical recent passwords allowed within a year.     | จำนวนครั้งสูงสุดที่อนุญาตให้ใช้รหัสผ่านซ้ำกับของเดิมภายในรอบหนึ่งปี                 |
| PASSWORD\_EXPIRES\_DURATION               | Password lifetime in days (calculated from the last update).        | อายุการใช้งานของรหัสผ่าน (หน่วยเป็นวัน) โดยคำนวณจากวันที่อัปเดตรหัสผ่านล่าสุด       |
| MAX\_AUTH\_FAILED\_COUNT                  | Max failed authentication attempts before the account is suspended. | จำนวนครั้งสูงสุดที่อนุญาตให้ระบุรหัสผ่านผิด ก่อนที่บัญชีจะถูกระงับการใช้งานชั่วคราว |
| ALLOW\_MULTIPLE\_SESSIONS\_PER\_USER      | Allow a user to have multiple active logged-in sessions.            | อนุญาตให้ผู้ใช้งานหนึ่งคนสามารถลงชื่อเข้าใช้งานพร้อมกันได้หลายอุปกรณ์หรือหลายเซสชัน |


{% endtab %}

{% tab title="Resource" %}
| **Field**                       | **Description (English)**                                                 | **คำอธิบาย (ภาษาไทย)**                                                                     |
| ------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| FX\_SPOT\_SECURITY\_TYPE\_ID    | Security Type ID used for FX spot transactions.                           | รหัสประเภทหลักทรัพย์ที่ใช้สำหรับรายการอัตราแลกเปลี่ยนทันที (FX Spot)                       |
| FX\_FORWARD\_SECURITY\_TYPE\_ID | Security Type ID used for FX forward transactions.                        | รหัสประเภทหลักทรัพย์ที่ใช้สำหรับรายการสัญญาซื้อขายเงินตราต่างประเทศล่วงหน้า (FX Forward)   |
| FX\_SWAP\_SECURITY\_TYPE\_ID    | Security Type ID used for FX swap transactions.                           | รหัสประเภทหลักทรัพย์ที่ใช้สำหรับรายการสัญญาแลกเปลี่ยนเงินตราต่างประเทศ (FX Swap)           |
| DEFAULT\_PRICESOURCE\_ID        | Price Source ID used to auto-create the Price Code after equity approval. | รหัสแหล่งข้อมูลราคาเริ่มต้นสำหรับสร้าง Price Code อัตโนมัติเมื่อหลักทรัพย์ได้รับการอนุมัติ |
| DEFAULT\_CURRENCY\_ID           | The default currency ID for the system.                                   | รหัสสกุลเงินหลักที่ใช้เป็นค่าเริ่มต้นของระบบ                                               |
| THB\_CURRENCY\_ID               | Thai Baht currency ID.                                                    | รหัสสำหรับสกุลเงินบาทไทย (THB)                                                             |


{% endtab %}
{% endtabs %}



<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (147).png" alt=""><figcaption></figcaption></figure></div>

### Transaction & Other

{% tabs %}
{% tab title="Transaction" %}
| **Field**                        | **Description (English)**                     | **คำอธิบาย (ภาษาไทย)**                                                          |
| -------------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------- |
| CHECK\_CROSS\_ROLE\_TX\_MUTATION | Enable cross-role transaction mutation check. | เปิดใช้งานการตรวจสอบสิทธิ์ข้ามบทบาท (Role) ในการสร้าง แก้ไข หรือลบรายการธุรกรรม |
{% endtab %}

{% tab title="Other" %}
| **Field**                           | **Description (English)**                                                 | **คำอธิบาย (ภาษาไทย)**                                                                 |
| ----------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| FUND\_FACT\_SHEET\_DISPLAY\_NAV     | Toggles NAV-related display in the Fund Fact Sheet.                       | เปิด/ปิด การแสดงผลข้อมูลที่เกี่ยวข้องกับ NAV ในรายงาน Fund Fact Sheet                  |
| EOD\_THEN\_SUMPORT                  | Internal flag related to the EOD report flow.                             | ตัวบ่งชี้ภายในระบบที่เกี่ยวข้องกับขั้นตอนการจัดทำรายงานสรุปพอร์ตหลังสิ้นวัน (EOD)      |
| NAV\_REPORT\_DISPLAY\_NAV           | Toggles NAV display in the NAV Report.                                    | เปิด/ปิด การแสดงค่า NAV ในรายงาน NAV Report                                            |
| NAV\_DISPLAY                        | Toggles NAV display.                                                      | เปิด/ปิด การแสดงผลค่า NAV ในส่วนต่าง ๆ ของระบบ                                         |
| FIXED\_PERFORMANCE\_CALENDAR\_QUERY | Fixed calendar query for performance calculation (uses default if empty). | คำสั่งดึงข้อมูลปฏิทินแบบคงที่เพื่อใช้คำนวณผลการดำเนินงาน (หากว่างไว้จะใช้ค่าเริ่มต้น)  |
| ENABLE\_PERFORMANCE\_SD             | Enable performance Standard Deviation (SD) calculation.                   | เปิดใช้งานการคำนวณค่าเบี่ยงเบนมาตรฐาน (SD) ของผลการดำเนินงาน                           |
| REPORT\_INSTRUCTION\_SIGNER         | List of report instruction signers (comma-separated usernames).           | รายชื่อผู้ลงนามในคำสั่งรายงาน โดยระบุเป็นชื่อผู้ใช้งานและคั่นด้วยเครื่องหมายจุลภาค (,) |


{% endtab %}
{% endtabs %}



**Save Button**: Save the configuration changes.

