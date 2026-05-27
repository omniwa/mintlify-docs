---
icon: resolving
---

# Corporate Action

### Corporate Action

Corporate Action is used to update stock information when securities are marked with corporate events such as XD, XR, XE, Convert, XN or stock splits. These marks affect shareholder rights and trading conditions.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (293).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                  | **Description (English)**                                                | **คำอธิบาย (ภาษาไทย)**                                            |
| ------------------------------ | ------------------------------------------------------------------------ | ----------------------------------------------------------------- |
| Search                         | Search for an existing corporate action by security code or action type. | ช่องสำหรับค้นหารายการสิทธิประโยชน์ที่มีอยู่แล้วในระบบ             |
| Create Corporate Action        | Register a new corporate action event (e.g., Dividend, Stock Split).     | ปุ่มสำหรับเริ่มลงทะเบียนกิจกรรมสิทธิประโยชน์ใหม่                  |
| Corporate Action Table         | Lists all currently configured corporate actions in the system.          | ตารางแสดงรายการสิทธิประโยชน์ทั้งหมดที่บันทึกไว้ในระบบ             |
| Preview Button                 | View the detailed calculation and schedule of the corporate action.      | ปุ่มสำหรับเรียกดูรายละเอียด เงื่อนไข และตารางเวลาของสิทธิประโยชน์ |
| Edit Button                    | Modify the details, dates, or ratios of an existing action.              | ปุ่มสำหรับแก้ไขข้อมูล วันที่ หรือสัดส่วนของรายการเดิม             |
| Delete Button                  | Remove the corporate action record from the system.                      | ปุ่มสำหรับลบรายการสิทธิประโยชน์ออกจากระบบ                         |
| Pending Corporate Action Table | Actions that are newly created or modified and awaiting approval.        | ตารางแสดงรายการสิทธิประโยชน์ที่รอการอนุมัติก่อนจะมีผลในพอร์ต      |



### Create Corporate Action



{% tabs %}
{% tab title="XR" %}
#### XR

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure></div>

| **Component**    | **Description (English)**                                              | **คำอธิบาย (ภาษาไทย)**                                        |
| ---------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| X-Type           | The type of corporate action or entitlement (e.g., XD, XR, XW).        | ประเภทของสิทธิประโยชน์ (เช่น ปันผล, สิทธิจองซื้อหุ้นเพิ่มทุน) |
| Security Code    | Select the parent security that is providing the entitlement.          | เลือกหลักทรัพย์หลักที่ให้สิทธิประโยชน์                        |
| Remark           | Additional internal notes or details about this action.                | หมายเหตุหรือคำอธิบายเพิ่มเติมเกี่ยวกับรายการนี้               |
| X-Date           | The date on which the buyer is no longer entitled to the benefit.      | วันแรกที่ผู้ซื้อหลักทรัพย์จะไม่ได้สิทธิประโยชน์นั้น ๆ         |
| Resolution Date  | The official date when the board/meeting approved the action.          | วันที่คณะกรรมการมีมติอนุมัติการให้สิทธิประโยชน์               |
| Book Closed Date | The date when the registry is closed to determine eligible holders.    | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิ       |
| Payment Period   | The start and end dates for the benefit distribution or exercise.      | ช่วงเวลาเริ่มต้นและสิ้นสุดของการจ่ายผลประโยชน์หรือการใช้สิทธิ |
| Right Rounding   | Define how fractional shares or rights are handled (e.g., Round down). | วิธีการจัดการกับสิทธิที่เป็นเศษทศนิยม (เช่น ปัดลง)            |

#### Entitlement Details

| **Column**    | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                           |
| ------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| Security Code | The resulting security or asset from this action.            | หลักทรัพย์ที่จะได้รับ (เช่น หุ้นเดิม หรือ Warrant ตัวใหม่)       |
| Tradable Date | The date when the new shares or rights become tradable.      | วันที่หลักทรัพย์ที่ได้รับใหม่เริ่มซื้อขายได้ในตลาด               |
| Ratio         | The entitlement ratio (Existing Shares : New Shares/Rights). | สัดส่วนการให้สิทธิ (จำนวนหุ้นเดิม : จำนวนหุ้นหรือสิทธิที่ได้รับ) |
| Price         | The exercise price or subscription price (if applicable).    | ราคาใช้สิทธิหรือราคาจองซื้อ (ถ้ามี)                              |
{% endtab %}

{% tab title="XE" %}
#### XE

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure></div>

| **Component**    | **Description (English)**                                              | **คำอธิบาย (ภาษาไทย)**                                        |
| ---------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| X-Type           | The type of corporate action or entitlement (e.g., XD, XR, XW).        | ประเภทของสิทธิประโยชน์ (เช่น ปันผล, สิทธิจองซื้อหุ้นเพิ่มทุน) |
| Security Code    | Select the parent security that is providing the entitlement.          | เลือกหลักทรัพย์หลักที่ให้สิทธิประโยชน์                        |
| Remark           | Additional internal notes or details about this action.                | หมายเหตุหรือคำอธิบายเพิ่มเติมเกี่ยวกับรายการนี้               |
| X-Date           | The date on which the buyer is no longer entitled to the benefit.      | วันแรกที่ผู้ซื้อหลักทรัพย์จะไม่ได้สิทธิประโยชน์นั้น ๆ         |
| Resolution Date  | The official date when the board/meeting approved the action.          | วันที่คณะกรรมการมีมติอนุมัติการให้สิทธิประโยชน์               |
| Book Closed Date | The date when the registry is closed to determine eligible holders.    | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิ       |
| Payment Period   | The start and end dates for the benefit distribution or exercise.      | ช่วงเวลาเริ่มต้นและสิ้นสุดของการจ่ายผลประโยชน์หรือการใช้สิทธิ |
| Right Rounding   | Define how fractional shares or rights are handled (e.g., Round down). | วิธีการจัดการกับสิทธิที่เป็นเศษทศนิยม (เช่น ปัดลง)            |

#### Entitlement Details

| **Column**    | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                           |
| ------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| Security Code | The resulting security or asset from this action.            | หลักทรัพย์ที่จะได้รับ (เช่น หุ้นเดิม หรือ Warrant ตัวใหม่)       |
| Tradable Date | The date when the new shares or rights become tradable.      | วันที่หลักทรัพย์ที่ได้รับใหม่เริ่มซื้อขายได้ในตลาด               |
| Ratio         | The entitlement ratio (Existing Shares : New Shares/Rights). | สัดส่วนการให้สิทธิ (จำนวนหุ้นเดิม : จำนวนหุ้นหรือสิทธิที่ได้รับ) |
| Price         | The exercise price or subscription price (if applicable).    | ราคาใช้สิทธิหรือราคาจองซื้อ (ถ้ามี)                              |
{% endtab %}

{% tab title="XD" %}
#### XD

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (296).png" alt=""><figcaption></figcaption></figure></div>

| **Component**     | **Description (English)**                                                   | **คำอธิบาย (ภาษาไทย)**                                          |
| ----------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------- |
| X-Type            | The entitlement type (set to XD for Ex-Dividend).                           | ประเภทสิทธิประโยชน์ (เลือกเป็น XD สำหรับการจ่ายปันผล)           |
| Security Code     | Select the security that is distributing the dividend.                      | เลือกหลักทรัพย์ที่ทำการจ่ายเงินปันผล                            |
| Remark            | Additional notes regarding this dividend announcement.                      | หมายเหตุหรือข้อมูลเพิ่มเติมเกี่ยวกับรายการปันผลนี้              |
| X-Date            | The date on which the stock begins trading without the dividend.            | วันแรกที่ผู้ซื้อหุ้นจะไม่ได้สิทธิรับเงินปันผล                   |
| Resolution Date   | The date the board of directors approved the dividend payment.              | วันที่คณะกรรมการบริษัทมีมติอนุมัติการจ่ายปันผล                  |
| Book Closed Date  | The date on which the company closes its register to identify shareholders. | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิรับปันผล |
| Dividend Type     | Choose between CASH (monetary) or STOCK (shares).                           | รูปแบบการจ่ายปันผล (เลือกเป็น เงินสด หรือ หุ้นปันผล)            |
| Dividend Interval | The frequency/period of the dividend (e.g., Interim, Annual).               | งวดการจ่ายเงินปันผล (เช่น ระหว่างกาล, ประจำปี)                  |
{% endtab %}

{% tab title="XN" %}
#### XN

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure></div>

| **Component**               | **Description (English)**                                                                   | **คำอธิบาย (ภาษาไทย)**                                            |
| --------------------------- | ------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| X-Type                      | The entitlement type (set to XN for Capital Reduction).                                     | ประเภทสิทธิประโยชน์ (เลือกเป็น XN สำหรับการลดทุน)                 |
| Security Code               | Select the security that is undergoing capital reduction.                                   | เลือกหลักทรัพย์ที่ทำการลดทุน                                      |
| Remark                      | Additional internal notes or details about this capital reduction.                          | หมายเหตุหรือคำอธิบายเพิ่มเติมเกี่ยวกับรายการลดทุนนี้              |
| X-Date                      | The date on which the stock begins trading without the right to receive the capital return. | วันแรกที่ผู้ซื้อหุ้นจะไม่ได้สิทธิรับเงินคืนจากการลดทุน            |
| Resolution Date             | The date the board or shareholders approved the capital reduction.                          | วันที่มีมติอนุมัติการลดทุนอย่างเป็นทางการ                         |
| Book Closed Date            | The date when the registry is closed to determine shareholders eligible for capital return. | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิรับเงินคืน |
| Capital Decreasing Per Unit | The amount of capital returned to shareholders per share/unit.                              | จำนวนเงินที่ลดทุนและคืนให้ผู้ถือหุ้นต่อ 1 หน่วย                   |
| Dividend Interval           | The specific period or interval associated with this distribution.                          | งวดการดำเนินงานที่เกี่ยวข้องกับการจ่ายคืนครั้งนี้                 |
| Receive Date                | The official date when shareholders will receive the cash from capital reduction.           | วันที่ผู้ถือหุ้นจะได้รับเงินคืนจากการลดทุนเข้าบัญชี               |
{% endtab %}

{% tab title="Split & Increase" %}
#### Split & Increase

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure></div>

| **Component**  | **Description (English)**                                                     | **คำอธิบาย (ภาษาไทย)**                                            |
| -------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| X-Type         | The entitlement type (set to Split & Increase).                               | ประเภทสิทธิประโยชน์ (เลือกเป็น Split & Increase สำหรับการแตกหุ้น) |
| Security Code  | Select the security that is undergoing the stock split.                       | เลือกหลักทรัพย์ที่ทำการแตกหุ้น                                    |
| Remark         | Additional internal notes or details about this stock split.                  | หมายเหตุหรือคำอธิบายเพิ่มเติมเกี่ยวกับรายการแตกหุ้นนี้            |
| Effective Date | The date when the stock split takes effect and the share balance is adjusted. | วันที่มีผลบังคับใช้ ซึ่งระบบจะปรับจำนวนหุ้นในพอร์ตตามสัดส่วนใหม่  |
| Old Par        | The original nominal value per share before the split.                        | มูลค่าพาร์เดิมก่อนการเปลี่ยนแปลง                                  |
| New Par        | The new nominal value per share after the split.                              | มูลค่าพาร์ใหม่หลังการเปลี่ยนแปลง                                  |

{% hint style="info" %}
#### Par Value Accuracy

Ensure the Old Par and New Par are entered correctly. These values are the primary drivers for recalculating the total number of shares and the adjusted cost basis across all portfolios holding this security.
{% endhint %}
{% endtab %}

{% tab title="Convert" %}
#### Convert

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure></div>

| **Component**    | **Description (English)**                                              | **คำอธิบาย (ภาษาไทย)**                                        |
| ---------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
| X-Type           | The type of corporate action or entitlement (e.g., XD, XR, XW).        | ประเภทของสิทธิประโยชน์ (เช่น ปันผล, สิทธิจองซื้อหุ้นเพิ่มทุน) |
| Security Code    | Select the parent security that is providing the entitlement.          | เลือกหลักทรัพย์หลักที่ให้สิทธิประโยชน์                        |
| Remark           | Additional internal notes or details about this action.                | หมายเหตุหรือคำอธิบายเพิ่มเติมเกี่ยวกับรายการนี้               |
| X-Date           | The date on which the buyer is no longer entitled to the benefit.      | วันแรกที่ผู้ซื้อหลักทรัพย์จะไม่ได้สิทธิประโยชน์นั้น ๆ         |
| Resolution Date  | The official date when the board/meeting approved the action.          | วันที่คณะกรรมการมีมติอนุมัติการให้สิทธิประโยชน์               |
| Book Closed Date | The date when the registry is closed to determine eligible holders.    | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิ       |
| Right Rounding   | Define how fractional shares or rights are handled (e.g., Round down). | วิธีการจัดการกับสิทธิที่เป็นเศษทศนิยม (เช่น ปัดลง)            |

#### Conversion Details

| **Column**    | **Description (English)**                                              | **คำอธิบาย (ภาษาไทย)**                                                    |
| ------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Security Code | The resulting security obtained after conversion (e.g., Common Stock). | หลักทรัพย์ปลายทางที่จะได้รับหลังการแปลงสภาพ (เช่น หุ้นสามัญ)              |
| Tradable Date | The date when the newly converted shares can be traded in the market.  | วันที่หลักทรัพย์ใหม่ที่ได้จากการแปลงสภาพเริ่มซื้อขายได้                   |
| Ratio         | The conversion ratio (Source Units : Resulting Units).                 | สัดส่วนการแปลงสภาพ (จำนวนหลักทรัพย์เดิม : จำนวนหลักทรัพย์ใหม่ที่จะได้รับ) |
| Price         | The conversion price or exercise price per unit (if any).              | ราคาที่ต้องจ่ายเพิ่มในการแปลงสภาพต่อหน่วย (ถ้ามี)                         |
{% endtab %}
{% endtabs %}

### Don't forget to approve the action in the Pending Table to finalize the setup.



