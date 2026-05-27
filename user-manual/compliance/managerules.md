---
description: >-
  Manage Rules is used to configure and define the rules that the system
  enforces on every investment.
icon: ruler-vertical
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

# Manage Rules

### Manage Rules

With this feature you can apply precise conditions and guidelines that keep the trading desk aligned with the fund’s policies.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (177).png" alt=""><figcaption></figcaption></figure></div>

| **Component**          | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                                  |
| ---------------------- | ------------------------------------------------------------ | ----------------------------------------------------------------------- |
| Rule Tab               | Window that lists the configured rules and their conditions. | หน้าต่างแสดงรายการกฎเกณฑ์และเงื่อนไขต่าง ๆ ที่ได้รับการตั้งค่าไว้ในระบบ |
| Create New Rule Button | Opens the form for creating a new rule.                      | ปุ่มสำหรับเปิดแบบฟอร์มเพื่อสร้างกฎเกณฑ์รายการใหม่                       |
| Search by Code         | Search for a rule by entering its unique code.               | ช่องค้นหากฎเกณฑ์โดยการระบุรหัสอ้างอิงเฉพาะ                              |
| Code                   | Unique identifier used to search and reference the rule.     | รหัสเฉพาะที่ใช้สำหรับการค้นหาและใช้อ้างอิงกฎเกณฑ์ในระบบ                 |
| Description            | Short explanation of what the rule enforces.                 | คำอธิบายสั้น ๆ เกี่ยวกับข้อกำหนดหรือสิ่งที่กฎเกณฑ์นี้บังคับใช้          |
| Created by             | User who created the Rule.                                   | ชื่อผู้ใช้งานที่เป็นผู้สร้างกฎเกณฑ์นี้                                  |
| Created At             | Date and time the rule was created.                          | วันและเวลาที่มีการสร้างกฎเกณฑ์เข้าระบบ                                  |
| Proved by              | User who proved the Rule.                                    | ชื่อผู้ใช้งานที่เป็นผู้ตรวจสอบและอนุมัติกฎเกณฑ์                         |
| Proved At              | Date and time the rule was proved.                           | วันและเวลาที่มีการอนุมัติกฎเกณฑ์                                        |
| Status                 | Current status of the rule (Active, Suspended, Expired).     | สถานะปัจจุบันของกฎเกณฑ์ (ใช้งานอยู่, ระงับชั่วคราว, หมดอายุ)            |
| View / Edit Button     | Open the rule for review or editing.                         | ปุ่มสำหรับเรียกดูรายละเอียดหรือแก้ไขข้อกำหนดของกฎเกณฑ์                  |
| Delete                 | Permanently remove the rule from the system.                 | ปุ่มสำหรับลบกฎเกณฑ์ออกจากระบบอย่างถาวร                                  |

***

### Create a New Rule

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure></div>

| **Component**           | **Description (English)**                               | **คำอธิบาย (ภาษาไทย)**                                                  |
| ----------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------- |
| Code                    | Field for entering the unique rule code.                | ช่องสำหรับกรอกรหัสอ้างอิงเฉพาะของกฎเกณฑ์                                |
| Description             | Field for providing a short description of the rule.    | ช่องสำหรับระบุคำอธิบายสั้น ๆ เกี่ยวกับตัวกฎเกณฑ์                        |
| Display Name            | The name shown to users when the rule is triggered.     | ชื่อที่ต้องการให้แสดงผลต่อผู้ใช้งานเมื่อมีการเรียกใช้กฎนี้              |
| Violation Message       | The message that will appear when the rule is breached. | ข้อความแจ้งเตือนที่จะปรากฏขึ้นเมื่อมีการละเมิดหรือทำผิดกฎเกณฑ์          |
| Approval \~ Expiry Date | Date range during which the rule is in effect.          | ช่วงวันที่ที่กฎเกณฑ์นี้มีผลบังคับใช้ (เริ่มอนุมัติ จนถึง วันหมดอายุ)    |
| Suspended               | Date when the rule's results are suspended.             | วันที่เริ่มระงับการใช้งานกฎเกณฑ์ (หากเลือกต้องระบุวันที่เริ่มระงับด้วย) |

{% tabs %}
{% tab title="Thresholds" %}
Logic block where you define the rule’s conditions.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure></div>

**Investment TX Type Limit**: Transaction type to which the rule applies. (Any, Buy, Sell)

**Left Operand**: Left-hand variable in the threshold expression.

**Operator**: Operator used in the threshold expression.

**Right Operand**: Right-hand variable or constant in the threshold expression. Notification level triggered when the conditions are met.

* Fixed Value
  * Warning
  * Approval
  * Error
* Dynamic Value (Percentage of)
  * Warning
  * Approval
  * Error
  * Percentage of: Percentage value used by the rule when the right operand is dynamic.
{% endtab %}

{% tab title="Match Portfolios" %}
Portfolios where the rule is applied or enforced.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure></div>

#### _**Tab Top Left**_

**Inverted Matching Box**: When enabled, the rule does NOT apply to the items selected.

**Include Targets**: Selected items grouped into customised collections (Portfolio Targets).

**Include**: Items where the rule is enforced.

**Exclude**: Items where the rule does NOT apply.

#### _Include Portfolios, Portfolio Groups, Portfolio Models_

**Left Table**: The list of available portfolios (and etc.) to choose from.

**Add Selected Button**: Button to add the highlighted items (Selected items) to the Included box.

**Right Table**: Items that have already been Included/selected.

**Sort**: Organises the Portfolio list in alphabetical order.
{% endtab %}

{% tab title="Match Securities" %}
<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure></div>

#### _**Tab Top Left**_

**Inverted Matching Box**: When enabled, the rule does NOT apply to the items selected.

**Include Targets**: Selected items grouped into customised collections (Security Targets).

**Include**: Items where the rule is enforced.

**Exclude**: Items where the rule does NOT apply.

#### _Include Security, Sector, Security Type, Security Class, Issuer Company, Company's code or name, Exchange Country_

**Left Table**: The list of available securities to choose from.

**Add Selected Button**: Button to add highlighted items to the Included box.

**Right Table**: Items that have already been Included/selected.

**Sort**: Organises the security list in alphabetical order.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Noted

* <mark style="background-color:$warning;">Warning:</mark> Notify only, investment allowed

Purpose: To prompt early awareness and allow preemptive adjustments.

* <mark style="background-color:violet;">Approval</mark>: Requires Risk team approval

Purpose: To ensure oversight for borderline or exceptional cases.

* <mark style="background-color:red;">Error:</mark> Blocked, investment not allowed

Purpose: To enforce hard limits and prevent non-compliant transactions.
{% endhint %}

***

### **Example Rule**

{% columns %}
{% column width="33.33333333333333%" %}
<details>

<summary>Cash Buffer</summary>

Total cash in Portfolio at least 3% of NAV

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Currency Concentration Limit</summary>

Each Cash Currency in Portfolio at least 10% of NAV

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Country Concentration w/ Cash</summary>

Country Concentration w/ Cash not more than 25%

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Exchange Country Concentration w/ Cash</summary>

Exchange Country Concentration w/ Cash not more than 20%

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure></div>

</details>
{% endcolumn %}

{% column width="33.33333333333333%" %}
<details>

<summary>Thai Stock Universe</summary>

Thai-listed equities in SET only

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>ASEAN Stock Universe</summary>

Equities in ASEAN only

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Stock Concentration Limit</summary>

Warn/Error if single security is more than #% of portfolio NAV

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Not Buy some Equity (AOT)</summary>

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (193).png" alt=""><figcaption></figcaption></figure></div>

</details>
{% endcolumn %}

{% column %}
<details>

<summary>Sector Concentration Rule</summary>

Limit investment allocation in each industry sector

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Country Concentration Rule</summary>

Limit investment allocation by country (geographic)

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure></div>

</details>

<details>

<summary>Exchange Country Concentration Rule</summary>

Limit investment allocation by Exchange country

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure></div>

</details>


{% endcolumn %}
{% endcolumns %}

***

### Portfolio Target

Portfolio Target groups portfolios so that rules can be applied to many portfolios at once. It is the easiest way to maintain consistent compliance across a related set of accounts.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                      | **Description (English)**                       | **คำอธิบาย (ภาษาไทย)**                               |
| ---------------------------------- | ----------------------------------------------- | ---------------------------------------------------- |
| Search by Name Search Box          | Search for a Portfolio Target by name.          | ช่องค้นหาสำหรับระบุชื่อเป้าหมายพอร์ตโฟลิโอที่ต้องการ |
| Create New Portfolio Target Button | Open the form to create a new Portfolio Target. | ปุ่มสำหรับเปิดหน้าต่างสร้างเป้าหมายพอร์ตโฟลิโอใหม่   |
| Name                               | Name of the Portfolio Target.                   | ชื่อของเป้าหมายพอร์ตโฟลิโอ                           |
| Description                        | Description of the Portfolio Target.            | รายละเอียดหรือคำอธิบายเกี่ยวกับเป้าหมายพอร์ตโฟลิโอ   |
| Edit Button                        | Modify the Portfolio Target.                    | ปุ่มสำหรับแก้ไขข้อมูลเป้าหมายพอร์ตโฟลิโอ             |

{% hint style="warning" %}
_Important: If portfolios are added to or removed from a Portfolio Target, any rule that uses that Target will NOT update automatically. You must re-match the rule with the modified Portfolio Target to apply the new list._
{% endhint %}

#### Create Portfolio Target

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure></div>

| **Component**           | **Description (English)**                  | **คำอธิบาย (ภาษาไทย)**                                              |
| ----------------------- | ------------------------------------------ | ------------------------------------------------------------------- |
| Target Name             | Name of the new Target.                    | ชื่อของเป้าหมายพอร์ตโฟลิโอใหม่                                      |
| Description             | Description of the new Target.             | รายละเอียดหรือคำอธิบายเกี่ยวกับเป้าหมายพอร์ตโฟลิโอ                  |
| Include                 | Items to add to the Target.                | ส่วนสำหรับเลือกรายการที่ต้องการ "รวมเข้า" ในเป้าหมายนี้             |
| Exclude                 | Items to keep out of the Target.           | ส่วนสำหรับเลือกรายการที่ต้องการ "ยกเว้น" ออกจากเป้าหมายนี้          |
| Portfolios              | Available portfolios that can be selected. | รายชื่อพอร์ตโฟลิโอทั้งหมดที่สามารถเลือกได้                          |
| Add Selected / Add Item | Move highlighted items to the chosen list. | ปุ่มสำหรับย้ายรายการที่เลือกไปยังรายการที่ต้องการ (Include/Exclude) |
| Included                | Items that have already been chosen.       | รายชื่อรายการที่ถูกเลือกไว้เรียบร้อยแล้ว                            |
| Create Button           | Save the new Portfolio Target.             | ปุ่มสำหรับกดบันทึกการสร้างเป้าหมายพอร์ตโฟลิโอ                       |



***

### Security Target

Security Target groups securities so that rules can be applied to many securities at once. Use it to standardise the rules applied to similar instruments (for example all SET100 stocks or all government bonds).

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure></div>

| **Component**                     | **Description (English)**                      | **คำอธิบาย (ภาษาไทย)**                              |
| --------------------------------- | ---------------------------------------------- | --------------------------------------------------- |
| Search by Name Search Box         | Search for a Security Target by name.          | ช่องค้นหาสำหรับระบุชื่อเป้าหมายหลักทรัพย์ที่ต้องการ |
| Create New Security Target Button | Open the form to create a new Security Target. | ปุ่มสำหรับเปิดหน้าต่างสร้างเป้าหมายหลักทรัพย์ใหม่   |
| Name                              | Name of the Security Target.                   | ชื่อของเป้าหมายหลักทรัพย์                           |
| Description                       | Description of the Security Target.            | รายละเอียดหรือคำอธิบายเกี่ยวกับเป้าหมายหลักทรัพย์   |
| Edit Button                       | Modify the Security Target.                    | ปุ่มสำหรับแก้ไขข้อมูลเป้าหมายหลักทรัพย์             |



{% hint style="warning" %}
_Important: If securities are added to or removed from a Security Target, any rule that uses that Target will NOT update automatically. You must re-match the rule with the modified Security Target to apply the new list._
{% endhint %}

#### Create Security Target

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure></div>

| **Component**           | **Description (English)**                  | **คำอธิบาย (ภาษาไทย)**                                                  |
| ----------------------- | ------------------------------------------ | ----------------------------------------------------------------------- |
| Target Name             | Name of the new Target.                    | ชื่อของเป้าหมายหลักทรัพย์ใหม่                                           |
| Description             | Description of the new Target.             | รายละเอียดหรือคำอธิบายเกี่ยวกับเป้าหมายหลักทรัพย์                       |
| Include                 | Items to add to the Target.                | ส่วนสำหรับเลือกหลักทรัพย์ที่ต้องการ "รวมเข้า" ในเป้าหมายนี้             |
| Exclude                 | Items to keep out of the Target.           | ส่วนสำหรับเลือกหลักทรัพย์ที่ต้องการ "ยกเว้น" ออกจากเป้าหมายนี้          |
| Security                | Available securities that can be selected. | รายชื่อหลักทรัพย์ทั้งหมดที่สามารถเลือกได้ในระบบ                         |
| Add Selected / Add Item | Move highlighted items to the chosen list. | ปุ่มสำหรับย้ายหลักทรัพย์ที่เลือกไปยังรายการที่ต้องการ (Include/Exclude) |
| Included                | Items that have already been chosen.       | รายชื่อหลักทรัพย์ที่ถูกเลือกไว้เรียบร้อยแล้ว                            |
| Create Button           | Save the new Security Target.              | ปุ่มสำหรับกดบันทึกการสร้างเป้าหมายหลักทรัพย์                            |

