---
description: Equity is used to create and register stocks within the system.
icon: display-chart-up-circle-currency
---

# Equity

### Equity

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (291).png" alt=""><figcaption></figcaption></figure></div>

| **Component**          | **Description (English)**                                                       | **คำอธิบาย (ภาษาไทย)**                                               |
| ---------------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Code (Search)          | Search for an existing equity using its unique security code or symbol.         | ช่องสำหรับค้นหาหุ้นที่มีอยู่แล้วด้วยรหัสหลักทรัพย์หรือชื่อย่อ        |
| Security Type (Filter) | Filter the list of equities by their specific asset type or sub-category.       | ตัวกรองเพื่อเรียกดูหุ้นตามประเภทหลักทรัพย์ที่กำหนด                   |
| Create Equity          | Open the setup to register and add a new equity to the system.                  | ปุ่มสำหรับเริ่มลงทะเบียนและเพิ่มข้อมูลหุ้นตัวใหม่                    |
| Equity Table           | Lists all equities currently configured and active in the system.               | ตารางแสดงรายชื่อหุ้นทั้งหมดที่ตั้งค่าไว้ในระบบ                       |
| Preview Button         | View detailed information, pricing rules, and profile of the equity.            | ปุ่มสำหรับเรียกดูรายละเอียด ข้อมูลพื้นฐาน และการตั้งค่าของหุ้นนั้น ๆ |
| Edit Button            | Modify the settings, attributes, or pricing methods of an existing equity.      | ปุ่มสำหรับแก้ไขข้อมูลหรือการตั้งค่าต่าง ๆ ของหุ้นเดิมที่มีอยู่       |
| Delete Button          | Permanently remove the equity record from the system.                           | ปุ่มสำหรับลบข้อมูลหุ้นออกจากระบบอย่างถาวร                            |
| Pending Equity Table   | Equities that have been recently created or modified and are awaiting approval. | ตารางแสดงรายชื่อหุ้นที่อยู่ระหว่างรอการอนุมัติก่อนเริ่มใช้งานจริง    |



### Create Equity

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (292).png" alt=""><figcaption></figcaption></figure></div>

{% tabs %}
{% tab title="Identification & Classification" %}
#### Identification & Classification

| **Component**   | **Description (English)**                                      | **คำอธิบาย (ภาษาไทย)**                                 |
| --------------- | -------------------------------------------------------------- | ------------------------------------------------------ |
| Security Code   | A unique identifier for the asset (e.g., Ticker Symbol).       | รหัสเฉพาะสำหรับระบุหลักทรัพย์ (เช่น ชื่อย่อหุ้น)       |
| Export Name     | The name or code used when exporting data to external systems. | ชื่อหรือรหัสที่ใช้สำหรับการส่งออกข้อมูลไปยังระบบภายนอก |
| Description     | Full name or detailed information about the security.          | ชื่อเต็มหรือรายละเอียดเพิ่มเติมเกี่ยวกับหลักทรัพย์     |
| Security Type   | The specific classification of the asset (e.g., Common Stock). | ประเภทของตราสารทุน (เช่น หุ้นสามัญ)                    |
| Business Sector | The industry sector the security belongs to.                   | หมวดหมู่ธุรกิจของหลักทรัพย์นั้น ๆ                      |
| ISIN (Local)    | The local International Securities Identification Number.      | รหัสมาตรฐานสากลสำหรับหลักทรัพย์ (เวอร์ชันท้องถิ่น)     |
| ISIN (Foreign)  | The foreign International Securities Identification Number.    | รหัสมาตรฐานสากลสำหรับหลักทรัพย์ (เวอร์ชันต่างประเทศ)   |
{% endtab %}

{% tab title="Market & Issuer" %}
#### Market & Issuer

| **Component**   | **Description (English)**                                       | **คำอธิบาย (ภาษาไทย)**                                |
| --------------- | --------------------------------------------------------------- | ----------------------------------------------------- |
| Exchange        | The marketplace where the asset is primarily traded.            | ตลาดหลักทรัพย์ที่หลักทรัพย์นั้นจดทะเบียนซื้อขาย       |
| Issuer          | The organization that issued the security.                      | ผู้ออกตราสาร (เลือกจากรายชื่อ Issuer ที่ลงทะเบียนไว้) |
| Calendar        | The trading calendar used for settlement and calculations.      | ปฏิทินวันหยุดที่ใช้อ้างอิงสำหรับการซื้อขายและคำนวณ    |
| Tradable Date   | The first date the asset is eligible for trading in the system. | วันที่เริ่มต้นที่สามารถทำการซื้อขายได้ในระบบ          |
| Registered Date | The official date the asset was registered with the exchange.   | วันที่จดทะเบียนหลักทรัพย์อย่างเป็นทางการ              |
{% endtab %}

{% tab title="Share Capital & Rights" %}
#### Share Capital & Rights

| **Component**      | **Description (English)**                                | **คำอธิบาย (ภาษาไทย)**                     |
| ------------------ | -------------------------------------------------------- | ------------------------------------------ |
| Par Value          | The nominal or face value per share.                     | ราคาพาร์หรือมูลค่าที่ตราไว้ต่อหุ้น         |
| Lot Size           | The minimum number of units required for a single trade. | จำนวนหน่วยขั้นต่ำต่อการซื้อขาย (Board Lot) |
| Paid-Up Share      | The total number of shares that have been fully paid.    | จำนวนหุ้นที่ชำระเต็มมูลค่าแล้ว             |
| Voting Right Share | The number of shares that carry voting rights.           | จำนวนหุ้นที่มีสิทธิออกเสียง                |
| Registered Share   | The total number of shares registered by the company.    | จำนวนหุ้นจดทะเบียนทั้งหมด                  |
{% endtab %}
{% endtabs %}

| **Component** | **Description (English)**                           | **คำอธิบาย (ภาษาไทย)**                        |
| ------------- | --------------------------------------------------- | --------------------------------------------- |
| Create Button | Save the configuration and register the new equity. | ปุ่มสำหรับบันทึกข้อมูลและลงทะเบียนหุ้นใหม่    |
| Cancel Button | Discard all current input and close the setup.      | ปุ่มยกเลิกสิ่งที่กรอกไว้ทั้งหมดและปิดหน้าต่าง |



### Don't forget to approve the action in the Pending Table to finalize the registration of your new equity.



