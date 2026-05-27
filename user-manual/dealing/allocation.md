---
description: >-
  Allocation distributes the executed securities across portfolios. It is the
  bridge between the trade you placed and the actual books of each individual
  portfolio.
icon: ballot
---

# Allocation



## Allocation

{% tabs %}
{% tab title="Allocation" %}
### Allocation



<table data-header-hidden><thead><tr><th width="184"></th><th width="250"></th><th></th></tr></thead><tbody><tr><td><strong>Component</strong></td><td><strong>Description (English)</strong></td><td><strong>คำอธิบาย (ภาษาไทย)</strong></td></tr><tr><td>Create / Trade Date</td><td>Toggle filter between the system creation date and actual trade date.</td><td>สลับการกรองข้อมูลระหว่างวันที่สร้างรายการ หรือวันที่ทำรายการจริง</td></tr><tr><td>Date Filter</td><td>Calendar tool to specify the date for the transactions to be displayed.</td><td>เครื่องมือเลือกวันที่เพื่อแสดงรายการธุรกรรมในตาราง</td></tr><tr><td>Columns</td><td>Customize which data fields are visible in the allocation table.</td><td>ปรับแต่งการเลือกแสดงคอลัมน์ข้อมูลต่าง ๆ ในตาราง</td></tr><tr><td>Filters</td><td>Advanced tools to refine search results within the allocation list.</td><td>เครื่องมือกรองข้อมูลขั้นสูงเพื่อค้นหาคำสั่งที่ต้องการ</td></tr><tr><td>Grouping</td><td>Group allocation records by specific categories (e.g., Security, Broker).</td><td>จัดกลุ่มรายการ (เช่น ตามรหัสหลักทรัพย์ หรือโบรกเกอร์)</td></tr><tr><td>Allocation Table</td><td>Main workspace displaying all individual allocation records.</td><td>ตารางหลักที่แสดงรายการบันทึกการจัดสรรทั้งหมด</td></tr><tr><td>Status</td><td>Current processing stage of each specific allocation.</td><td>สถานะปัจจุบันของแต่ละรายการจัดสรร</td></tr><tr><td>Unconfirm Button</td><td>Revert a confirmed order back to an unconfirmed state for editing.</td><td>ปุ่มยกเลิกการยืนยัน เพื่อกลับไปแก้ไขรายการที่ Confirm ไปแล้ว</td></tr><tr><td>Export Allocation</td><td>Download the displayed allocation data into an external file.</td><td>ปุ่มสำหรับส่งออกข้อมูลรายการจัดสรรออกนอกระบบ</td></tr><tr><td>Dealing Button</td><td>Access the Dealing dialog to manage order details for a specific record.</td><td>ปุ่มสำหรับเปิดหน้าต่าง Dealing เพื่อจัดการรายละเอียดของคำสั่งนั้น ๆ</td></tr><tr><td>Allocate Button</td><td>Trigger the distribution of securities to portfolios based on set rules.</td><td>ปุ่มเริ่มกระบวนการจัดสรรหลักทรัพย์เข้าพอร์ตตามเกณฑ์ที่กำหนด</td></tr><tr><td>Confirm Button</td><td>Finalize and approve the allocation results for the selected items.</td><td>ปุ่มยืนยันและอนุมัติผลการจัดสรรในขั้นตอนสุดท้าย</td></tr><tr><td>Delete Button</td><td>Remove a selected order or allocation from the system.</td><td>ปุ่มสำหรับลบรายการที่ไม่ต้องการออกจากระบบ</td></tr></tbody></table>
{% endtab %}

{% tab title="Create Dealing" %}
### Create Dealing



<table data-header-hidden><thead><tr><th width="191"></th><th width="236"></th><th></th></tr></thead><tbody><tr><td><strong>Field / Action Name</strong></td><td><strong>Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Type</td><td>Selection</td><td>Order type (BUY / SELL).</td></tr><tr><td>Security Code</td><td>Text / Alpha-numeric</td><td>Security identifier being traded.</td></tr><tr><td>Broker</td><td>Dropdown / Text</td><td>Broker that handles the transaction.</td></tr><tr><td>Members</td><td>Multi-select / Array</td><td>Portfolios involved in the order.</td></tr><tr><td>Trade Date</td><td>Date</td><td>Trade execution date.</td></tr><tr><td>Settle Date</td><td>Date</td><td>Settlement date.</td></tr><tr><td>Cost Per Unit</td><td>Numeric (Decimal)</td><td>Price per unit.</td></tr><tr><td>Units</td><td>Numeric (Integer/Decimal)</td><td>Number of units in the order.</td></tr><tr><td>Cost</td><td>Numeric (Calculated)</td><td>Total transaction value.</td></tr><tr><td>Commission Rate</td><td>Percentage</td><td>Commission percentage.</td></tr><tr><td>Commission (excl. VAT &#x26; WHT)</td><td>Numeric (Calculated)</td><td>Commission value before tax.</td></tr><tr><td>VAT Rate</td><td>Percentage</td><td>Applicable Value Added Tax percentage.</td></tr><tr><td>Withholding Tax Rate</td><td>Percentage</td><td>Withholding tax percentage.</td></tr><tr><td>Cancel Button</td><td>Action (Button)</td><td>Cancels the transaction.</td></tr><tr><td>Deal Button</td><td>Action (Button)</td><td>Confirms/executes the transaction.</td></tr></tbody></table>
{% endtab %}

{% tab title="Create Allocating" %}
### Create Allocating



<table data-header-hidden><thead><tr><th width="191"></th><th width="227"></th><th></th></tr></thead><tbody><tr><td><strong>Field / Action Name</strong></td><td><strong>Type</strong></td><td><strong>Description</strong></td></tr><tr><td>Type</td><td>Selection</td><td>Order type (BUY / SELL).</td></tr><tr><td>Security Code</td><td>Text / Alpha-numeric</td><td>Security identifier being traded.</td></tr><tr><td>Broker</td><td>Dropdown / Text</td><td>Brokerage firm handling the transaction.</td></tr><tr><td>Trade Date</td><td>Date</td><td>Date of execution.</td></tr><tr><td>Settle Date</td><td>Date</td><td>Settlement date.</td></tr><tr><td>Cost Per Unit</td><td>Numeric (Decimal)</td><td>Price per unit.</td></tr><tr><td>Units</td><td>Numeric (Integer/Decimal)</td><td>Number of securities.</td></tr><tr><td>Cost</td><td>Numeric (Calculated)</td><td>Total transaction amount.</td></tr><tr><td>Commission Rate</td><td>Percentage</td><td>Brokerage commission percentage.</td></tr><tr><td>Commission (excl. VAT &#x26; WHT)</td><td>Numeric (Calculated)</td><td>Commission before tax.</td></tr><tr><td>VAT Rate</td><td>Percentage</td><td>Applicable Value Added Tax.</td></tr><tr><td>Withholding Tax Rate</td><td>Percentage</td><td>Withholding tax percentage.</td></tr><tr><td>Allocation Summary Table</td><td>Data Component (Table)</td><td>Overview of allocated assets across portfolios/funds.</td></tr><tr><td>Allocation Button</td><td>Action (Button)</td><td>Initiates or modifies the security allocation process.</td></tr><tr><td>Cancel Button</td><td>Action (Button)</td><td>Discards the current allocation.</td></tr><tr><td>Allocate Button</td><td>Action (Button)</td><td>Confirms and finalizes the allocation.</td></tr></tbody></table>
{% endtab %}
{% endtabs %}





***



## Order Allocation Scenarios (Dealing ▸ Allocation)

When the total units filled by a broker do not perfectly match the original total ordered units, the system applies a pro-rata allocation logic based on the **Ordered %** of each sub-portfolio.

Due to decimal rounding conventions (e.g., matching board lot sizes or system limits), a minimal fraction of units may be left over. The system surfaces these as **Remaining Units**, which require manual distribution adjustments by the Fund Manager.

***

### **Scenario 1: Remaining Management Balance:** **300 Units**

* **Original Total Order:** 102,000 Units
* **Total Filled by Broker:** 100,200 Units
* **System Pro-Rata Allocation:** 99,900 Units
* **Remaining Management Balance:** **300 Units** (Requires Fund Manager manual adjustment)

**Allocation Summary Status:**&#x20;

<p align="right"><code>Allocated: 99,900 / 100,200</code> | <code>Remaining: </code><mark style="background-color:cyan;"><code>300</code></mark> </p>

<table><thead><tr><th width="105">Portfolio</th><th width="104" align="center">Ordered Unit</th><th width="104" align="center">Ordered %</th><th width="111" align="center">Allocated Unit</th><th width="111" align="center">Rounding</th><th width="117" align="center">Auto Calc. Allocation</th><th align="right">Adjust</th></tr></thead><tbody><tr><td><strong>TH_001</strong></td><td align="center">9,000</td><td align="center">0.88%</td><td align="center">800</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:cyan;">800</mark></td></tr><tr><td><strong>TH_002</strong></td><td align="center">5,000</td><td align="center">0.49%</td><td align="center">400</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:cyan;">400</mark></td></tr><tr><td><strong>TH_003</strong></td><td align="center">9,900</td><td align="center">9.71%</td><td align="center">9,700</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:cyan;">9,700</mark></td></tr><tr><td><strong>TH_004</strong></td><td align="center">90,700</td><td align="center">88.92%</td><td align="center">89,000</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:cyan;">89,000</mark></td></tr></tbody></table>

***

### **Scenario 2: Remaining Management Balance:** **200 Units**

* **Original Total Order:** 102,000 Units
* **Total Filled by Broker:** 90,000 Units
* **System Pro-Rata Allocation:** 89,800 Units
* **Remaining Management Balance:** **200 Units** (Requires Fund Manager manual adjustment)

**Allocation Summary Status:**&#x20;

<p align="right"> <code>Allocated: 89,800 / 90,000</code> | <code>Remaining: </code><mark style="background-color:green;"><code>200</code></mark></p>

<table><thead><tr><th width="104">Portfolio</th><th width="102" align="center">Ordered Unit</th><th width="105" align="center">Ordered %</th><th width="110" align="center">Allocated Unit</th><th width="110" align="center">Rounding</th><th width="118" align="center">Auto Calc. Allocation</th><th align="right">Adjust</th></tr></thead><tbody><tr><td><strong>TH_001</strong></td><td align="center">9,000</td><td align="center">0.88%</td><td align="center">700</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:green;">700</mark></td></tr><tr><td><strong>TH_002</strong></td><td align="center">5,000</td><td align="center">0.49%</td><td align="center">400</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:green;">400</mark></td></tr><tr><td><strong>TH_003</strong></td><td align="center">9,900</td><td align="center">9.71%</td><td align="center">8,700</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:green;">8,700</mark></td></tr><tr><td><strong>TH_004</strong></td><td align="center">90,700</td><td align="center">88.92%</td><td align="center">80,000</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:green;">80,000</mark></td></tr></tbody></table>

***

### **Scenario 3: Remaining Management Balance:** **100 Units**

* **Original Total Order:** 102,000 Units
* **Total Filled by Broker:** 46,600 Units
* **System Pro-Rata Allocation:** 46,500 Units
* **Remaining Management Balance:** **100 Units** (Requires Fund Manager manual adjustment)

**Allocation Summary Status:**&#x20;

<p align="right"> <code>Allocated: 46,500 / 46,600</code> | <code>Remaining: </code><mark style="color:blue;background-color:blue;"><code>100</code></mark></p>

<table><thead><tr><th width="104">Portfolio</th><th width="103" align="center">Ordered Unit</th><th width="103" align="center">Ordered %</th><th width="112" align="center">Allocated Unit</th><th width="110" align="center">Rounding</th><th width="117" align="center">Auto Calc. Allocation</th><th align="right">Adjust</th></tr></thead><tbody><tr><td><strong>TH_001</strong></td><td align="center">9,000</td><td align="center">0.88%</td><td align="center">400</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:blue;">400</mark></td></tr><tr><td><strong>TH_002</strong></td><td align="center">5,000</td><td align="center">0.49%</td><td align="center">200</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:blue;">200</mark></td></tr><tr><td><strong>TH_003</strong></td><td align="center">9,900</td><td align="center">9.71%</td><td align="center">4,500</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:blue;">4,500</mark></td></tr><tr><td><strong>TH_004</strong></td><td align="center">90,700</td><td align="center">88.92%</td><td align="center">41,400</td><td align="center">0</td><td align="center">100</td><td align="right"><mark style="color:blue;">41,400</mark></td></tr></tbody></table>

***

> 💡 **User Interface Operations Guide:**
>
> 1. **Auto Calc. Allocation:** The system processes initial calculations using the weight percentage of total placements.
> 2. **Adjust Column:** Fund Managers must manually input specific unit modifications inside the **Adjust** input field to distribute the **Remaining** balance down to zero (`0`) before final execution confirmation can be processed.
