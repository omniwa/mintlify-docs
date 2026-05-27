---
description: >-
  Fee Code is used to define custodian and management fees that appear in
  portfolio reports.
icon: file-code
---

# Fee Code

### Fee Code

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (283).png" alt=""><figcaption></figcaption></figure></div>

| **Component**          | **Description (English)**                                           | **คำอธิบาย (ภาษาไทย)**                                               |
| ---------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Fee Code (Search)      | Search for an existing fee configuration by its unique code.        | ช่องสำหรับค้นหารหัสค่าธรรมเนียมที่มีอยู่แล้วในระบบ                   |
| Create Fee Code Preset | Create a template for common fee structures to speed up setup.      | การสร้างค่าตั้งต้น (Preset) เพื่อใช้เป็นแม่แบบในการกำหนดค่าธรรมเนียม |
| Create Fee Code        | Define and add a new fee calculation code to the system.            | ปุ่มสำหรับเริ่มสร้างและกำหนดรหัสค่าธรรมเนียมใหม่                     |
| Fee Code Table         | Lists all currently configured fee codes and their status.          | ตารางแสดงรายชื่อรหัสค่าธรรมเนียมทั้งหมดที่ตั้งค่าไว้ในระบบ           |
| Preview Button         | View the detailed calculation logic and rates of the fee code.      | ปุ่มสำหรับเรียกดูรายละเอียดและเกณฑ์การคำนวณของค่าธรรมเนียมนั้น ๆ     |
| Edit Button            | Modify the rates or conditions of an existing fee code.             | ปุ่มสำหรับแก้ไขอัตราหรือเงื่อนไขของรหัสค่าธรรมเนียมเดิม              |
| Delete Button          | Remove a fee code configuration from the system.                    | ปุ่มสำหรับลบรหัสค่าธรรมเนียมออกจากระบบ                               |
| Pending Fee Code Table | Fee codes that are newly created or modified and awaiting approval. | ตารางแสดงรหัสค่าธรรมเนียมที่อยู่ระหว่างรอการอนุมัติก่อนเริ่มใช้งาน   |



### Create Fee Code

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (284).png" alt=""><figcaption></figcaption></figure></div>

{% tabs %}
{% tab title="General Information" %}
#### General Information

| **Component** | **Description (English)**                                    | **คำอธิบาย (ภาษาไทย)**                                           |
| ------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| From Preset   | Choose a saved fee-code preset to auto-fill common settings. | เลือกค่าตั้งต้น (Preset) เพื่อใช้เป็นแม่แบบในการกรอกข้อมูล       |
| Fee Code      | Unique identifier for the fee configuration.                 | รหัสเฉพาะสำหรับระบุประเภทค่าธรรมเนียม                            |
| Description   | Additional details regarding the purpose of this fee.        | รายละเอียดเพิ่มเติมเกี่ยวกับค่าธรรมเนียม                         |
| Expense / Fee | Classification of the item as an expense or a fee.           | การจำแนกประเภทว่าเป็นค่าใช้จ่าย (Expense) หรือค่าธรรมเนียม (Fee) |
| Type          | Categorization of the fee type within the system.            | หมวดหมู่ของประเภทค่าธรรมเนียม                                    |


{% endtab %}

{% tab title="Entity & Applicability" %}
#### Entity & Applicability



| **Component**        | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                                |
| -------------------- | ------------------------------------------------------------- | ----------------------------------------------------- |
| Tax Payer            | The entity responsible for the tax payment.                   | ผู้ที่มีหน้าที่รับผิดชอบในการชำระภาษี                 |
| Individual / Company | Specify if the fee applies to a person or an organization.    | ระบุว่าค่าธรรมเนียมนี้ใช้กับบุคคลธรรมดาหรือนิติบุคคล  |
| Period From / To     | The date range during which this fee configuration is active. | ช่วงวันที่ที่การตั้งค่าค่าธรรมเนียมนี้มีผลบังคับใช้   |
| Portfolio            | The specific portfolio linked to this fee configuration.      | พอร์ตโฟลิโอที่เชื่อมโยงกับการเรียกเก็บค่าธรรมเนียมนี้ |
{% endtab %}

{% tab title="Calculation Logic" %}
#### Calculation Logic



| **Component**  | **Description (English)**                                   | **คำอธิบาย (ภาษาไทย)**                                 |
| -------------- | ----------------------------------------------------------- | ------------------------------------------------------ |
| Calc Method    | The mathematical method used to calculate the fee.          | วิธีการที่ใช้ในการคำนวณค่าธรรมเนียม                    |
| Fee Base       | The underlying value or basis for the fee computation.      | ฐานที่ใช้ในการคำนวณค่าธรรมเนียม (เช่น มูลค่าสินทรัพย์) |
| Calc Frequency | The frequency at which the fee is calculated.               | ความถี่ในการประมวลผลคำนวณค่าธรรมเนียม                  |
| Days Basis     | The day count convention used for the calculation.          | เกณฑ์การนับจำนวนวันในการคำนวณ                          |
| Calendar       | The predefined holiday calendar used for calculation logic. | ปฏิทินวันหยุดที่ใช้อ้างอิงสำหรับการคำนวณ               |
{% endtab %}

{% tab title="Accounting & Tax" %}
#### Accounting & Tax



| **Component**     | **Description (English)**                                | **คำอธิบาย (ภาษาไทย)**                        |
| ----------------- | -------------------------------------------------------- | --------------------------------------------- |
| Fee GL Code       | General Ledger code for accounting integration.          | รหัสบัญชีแยกประเภท (GL) สำหรับค่าธรรมเนียมนี้ |
| Fee Type (Report) | Classification used specifically for reporting purposes. | ประเภทค่าธรรมเนียมที่ใช้ในการแสดงผลในรายงาน   |
| VAT Status        | Status indicating if Value Added Tax is applicable.      | สถานะการคิดภาษีมูลค่าเพิ่ม (VAT)              |
| VAT Rate          | The applicable VAT percentage.                           | อัตราภาษีมูลค่าเพิ่ม (%)                      |
| WHT Rate          | The applicable Withholding Tax rate.                     | อัตราภาษีหัก ณ ที่จ่าย (%)                    |
{% endtab %}
{% endtabs %}

{% hint style="info" %}
### Important

The Period From / To settings are critical for system automation. If a transaction or calculation is performed outside of this specified date range, the system will not automatically apply or calculate the associated fees.
{% endhint %}

### Don't forget to approve the action in the Pending Table to finalize the creation of your new Fee Code.
