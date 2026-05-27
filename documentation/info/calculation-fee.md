---
icon: calculator
---

# Calculation: Fee

<details>

<summary>ref Google Sheet <a href="https://docs.google.com/spreadsheets/d/172n9k1_AwhCTsOo-LV835Z18upqcCw3gfcLnRRSF7OU/edit?gid=1793016328#gid=1793016328">Fee Calc.</a></summary>

{% embed url="https://docs.google.com/spreadsheets/d/172n9k1_AwhCTsOo-LV835Z18upqcCw3gfcLnRRSF7OU/edit?usp=sharing" %}



</details>



## Fee Calculation Logic (Ver. Eng)

The system calculates daily operational fees (such as Management Fees and Custodian Fees) on Date $T$ using the **NAV Before Fee** of Date $T$.

$$\text{NAV Before Fee} = \text{Total Assets} - \text{Total Liabilities}$$

_(Liability = Total Liability - Today Fee)_

***

#### **1. Fee Calculation Parameters**

<table><thead><tr><th width="166">Parameter</th><th width="177">Technical Term</th><th>Description</th></tr></thead><tbody><tr><td><strong>Base</strong></td><td><code>nav_before_fee</code></td><td>The initial valuation amount used for calculation (NAV Before Fee).</td></tr><tr><td><strong>Fee Rate</strong></td><td><code>fee_rate</code></td><td>The percentage fee rate expressed in decimals (e.g., <code>0.03% = 0.0003</code>).</td></tr><tr><td><strong>Basis Day</strong></td><td><code>basis_day</code></td><td>Total days in the year convention (e.g., 360, 365, or 366).</td></tr><tr><td><strong>Accumulate Day</strong></td><td><code>accumulate_day</code></td><td>Number of accrued days (Defaults to 1 on regular business days).</td></tr></tbody></table>

#### **Calculation Formula**

$$\text{Daily Fee} = \left( \frac{\text{Base} \times \text{Fee Rate}}{\text{Basis Day}} \right) \times \text{Accumulate Day}$$

***

#### **2. Fee Specification & Calculation Examples**

<table><thead><tr><th width="128">Fee Type</th><th width="79" align="center">Rate (%)</th><th width="127" align="center">Base Value</th><th width="85" align="center">Basis</th><th width="81" align="center">Days</th><th width="213">Calculation Formula / Example</th><th width="91" align="center">Daily Fee</th></tr></thead><tbody><tr><td><strong>Management Fee</strong></td><td align="center">0.03%</td><td align="center">4,911,557.81</td><td align="center">366</td><td align="center">1</td><td><code>(4,911,557.81 * 0.0003 / 366) * 1</code></td><td align="center"><strong>4.03</strong></td></tr><tr><td><strong>Custodian Fee</strong></td><td align="center">0.01%</td><td align="center">4,911,557.81</td><td align="center">366</td><td align="center">1</td><td><code>(4,911,557.81 * 0.0001 / 366) * 1</code></td><td align="center"><strong>1.34</strong></td></tr></tbody></table>

> ⚠️ **Important Note on Weekends & Holidays (The Monday Rule):**
>
> * On Mondays, the **Accumulate Day** dynamically equals **3** (representing Saturday, Sunday, and Monday combined).
> * The system pulls the **Monday closing prices** to calculate the `Base`, then multiplies the result by 3 to accrue the entire weekend block.





***

***





## หลักการคำนวณค่าธรรมเนียม (Ver. ไทย)

การคำนวณค่าธรรมเนียมรายวัน (เช่น Management Fee และ Custodian Fee) ณ วันที่ $T$ ระบบจะใช้มูลค่า **NAV ก่อนหักค่าธรรมเนียม (NAV Before Fee)** ของวันที่ $T$ เป็นเกณฑ์ในการคำนวณ

$$\text{NAV Before Fee} = \text{สินทรัพย์รวม (Assets)} - \text{หนี้สินรวม (Liability)}$$

_(Liability = Total Liability - Today Fee)_

***

#### **1. คำอธิบายตัวแปรในการคำนวณ**

<table><thead><tr><th width="167">ตัวแปร</th><th width="177">ตัวแปรในระบบ</th><th>คำอธิบาย</th></tr></thead><tbody><tr><td><strong>Base</strong></td><td><code>nav_before_fee</code></td><td>มูลค่าตั้งต้นที่นำมาคำนวณ (ค่า NAV ก่อนหักค่าธรรมเนียม)</td></tr><tr><td><strong>Fee Rate</strong></td><td><code>fee_rate</code></td><td>อัตราค่าธรรมเนียมรายปี แปลงเป็นทศนิยม <br>(เช่น <code>0.03% = 0.0003</code>)</td></tr><tr><td><strong>Basis Day</strong></td><td><code>basis_day</code></td><td>จำนวนวันในรอบปีตามเงื่อนไขการคำนวณ เช่น 360, 365, หรือ 366 วัน</td></tr><tr><td><strong>Accumulate Day</strong></td><td><code>accumulate_day</code></td><td>จำนวนวันคงค้างสะสม (วันทำการปกติมีค่าเท่ากับ 1)</td></tr></tbody></table>

#### **สูตรการคำนวณ (Calculation Formula)**

$$\text{ค่าธรรมเนียมรายวัน} = \left( \frac{\text{Base} \times \text{Fee Rate}}{\text{Basis Day}} \right) \times \text{Accumulate Day}$$

***

#### **2. ตารางรายละเอียดและตัวอย่างการคำนวณค่าธรรมเนียม**

<table><thead><tr><th width="128">ประเภทค่าธรรมเนียม</th><th width="85" align="center">อัตรา (%)</th><th width="119" align="center">มูลค่าตั้งต้น (Base)</th><th width="86" align="center">วันในรอบปี</th><th width="94" align="center">จำนวนวัน</th><th width="213">ตัวอย่างการแทนค่าในสูตร</th><th width="114" align="center">ค่าธรรมเนียม/วัน</th></tr></thead><tbody><tr><td><strong>Management Fee</strong></td><td align="center">0.03%</td><td align="center">4,911,557.81</td><td align="center">366</td><td align="center">1</td><td><code>(4,911,557.81 * 0.0003 / 366) * 1</code></td><td align="center"><strong>4.03</strong></td></tr><tr><td><strong>Custodian Fee</strong></td><td align="center">0.01%</td><td align="center">4,911,557.81</td><td align="center">366</td><td align="center">1</td><td><code>(4,911,557.81 * 0.0001 / 366) * 1</code></td><td align="center"><strong>1.34</strong></td></tr></tbody></table>

> ⚠️ **หมายเหตุสำคัญในกรณีที่เจอวันหยุด (กรณีวันจันทร์):**
>
> * **การสะสมวันคงค้าง:** ในวันจันทร์ ค่า `Accumulate Day` จะปรับเป็น **3** (นับรวมวันเสาร์ วันอาทิตย์ และวันจันทร์)
> * **เกณฑ์ราคาที่ใช้:** ระบบจะนำ **ราคาปิดของวันจันทร์** มาคำนวณหาค่า `Base` จากนั้นจึงคูณด้วย 3 เพื่อคิดรวบยอดค่าธรรมเนียมสะสมของช่วงวันหยุดทั้งหมด





