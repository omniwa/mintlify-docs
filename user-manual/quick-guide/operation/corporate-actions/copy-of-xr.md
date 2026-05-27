---
hidden: true
icon: arrow-turn-down-right
---

# Copy of — XR

### **Clips Tutorial**

{% content-ref url="https://app.gitbook.com/s/5gU1vMFynoerZN6qaJVE/info/corporate-action-xr-xe-xd..." %}
[Corporate Action: XR, XE, XD...](https://app.gitbook.com/s/5gU1vMFynoerZN6qaJVE/info/corporate-action-xr-xe-xd...)
{% endcontent-ref %}

### Create Corporate Action Information

{% tabs %}
{% tab title="Important Dates" %}
<div data-with-frame="true"><figure><img src="../../../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure></div>

| **Date Type**    | **Description (English)**                                                                                | **คำอธิบาย (ภาษาไทย)**                                                             |
| ---------------- | -------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| X-Date           | The date when the corporate action takes effect (for foreign stocks, this follows Custodian guidelines). | วันที่สิทธิประโยชน์มีผลบังคับใช้ (สำหรับหุ้นต่างประเทศจะยึดตามแนวทางของ Custodian) |
| Resolution Date  | The date of the official announcement.                                                                   | วันที่ประกาศข้อมูลอย่างเป็นทางการ                                                  |
| Book Closed Date | The deadline for shareholder registration (Record Date).                                                 | วันปิดสมุดทะเบียนเพื่อรวบรวมรายชื่อผู้ถือหุ้นที่มีสิทธิ                            |
{% endtab %}

{% tab title="Corporate Action (X-Type)" %}
| **Term**         | **Full Name**     | **Description (English)**                                                                     | **คำอธิบาย (ภาษาไทย)**                               |
| ---------------- | ----------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| XR               | Ex-Rights         | The company issues new shares and allows purchases at a special price.                        | บริษัทออกหุ้นใหม่และให้สิทธิซื้อในราคาพิเศษ          |
| XD               | Ex-Dividend       | The company announces dividend payments.                                                      | บริษัทประกาศจ่ายเงินปันผล                            |
| XE               | Ex-Exercise       | The company closes shareholder registration to allow rights conversion into reference stocks. | ปิดสมุดทะเบียนเพื่อใช้สิทธิแปลงสภาพเป็นหุ้นอ้างอิง   |
| XN               | Ex-Capital Return | Shareholders receive capital refunds due to a reduction in share capital.                     | ผู้ถือหุ้นได้รับเงินคืนจากการลดทุนจดทะเบียน          |
| Split & Increase | Split & Increase  | The company splits share par value, increasing the number of shares proportionally.           | การแตกพาร์เพื่อเพิ่มจำนวนหุ้นตามสัดส่วน              |
| Convert          | Convert           | Shares are transformed from one type to another.                                              | การเปลี่ยนประเภทหุ้นจากประเภทหนึ่งเป็นอีกประเภทหนึ่ง |


{% endtab %}

{% tab title="Right rounding" %}
| **Option** | **Description (English)**                                         | **คำอธิบาย (ภาษาไทย)**                                            |
| ---------- | ----------------------------------------------------------------- | ----------------------------------------------------------------- |
| Blank      | Round up if the fraction is $$\ge 0.5$$, round down if $$< 0.5$$. | ปัดขึ้นหากเศษส่วนมากกว่าหรือเท่ากับ 0.5 และปัดทิ้งหากน้อยกว่า 0.5 |
| Round Down | Always round downward.                                            | ปัดเศษทิ้งเสมอ (ปัดลง)                                            |
| Round Up   | Always round upward.                                              | ปัดเศษขึ้นเสมอ                                                    |
{% endtab %}
{% endtabs %}

***



### X-Type — XR

Use the news / announcement to capture the key data — Payment Period, Right Rounding, Security Code, Tradable Date, Ratio and Price.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 223 - คำอธิบาย Figure 10.4e — XR news (GULF example)" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 224 - คำอธิบาย Figure 10.4f — Create Corporate Action (XR)" alt=""><figcaption></figcaption></figure>



_Right Rounding rules: Blank — round up if fraction ≥ 0.5; Round Down — always down; Round Up — always up._

In Pending Corporate Action, click (2) to confirm the creation.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 225 - คำอธิบาย Figure 10.4g — Confirm pending XR action" alt=""><figcaption></figcaption></figure>

Figure 10.4g — Confirm pending XR action

Role: Fund Manager / Dealer / PF Admin. Navigate to Dealing ▸ Approve X-Transaction, select (3) and click (4) to confirm. The status turns green when complete. Wait for Fund Account / Operation processing — the transaction will appear in Dealing ▸ Post Allocation. Continue with the standard investment process.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 226 - คำอธิบาย Figure 10.4h — Approve X-Transaction (XR)" alt=""><figcaption></figcaption></figure>

Figure 10.4h — Approve X-Transaction (XR)

Role: Fund Account / PF Operation. Navigate to Daily ▸ Generate Transaction, select the row and click (5) to generate. The status updates from red to green.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 227 - คำอธิบาย Figure 10.4i — Generate Transaction (XR)" alt=""><figcaption></figcaption></figure>

Figure 10.4i — Generate Transaction (XR)

_If no data appears in Generate Transaction, no portfolio held the stock during that period. Continue the standard process — wait for Fund Manager, then Daily ▸ Close Transaction and finally complete EOD._

<br>

***

### X-Type — XE

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 228 - คำอธิบาย Figure 10.4j — XE news (TMB-T1 example)" alt=""><figcaption></figcaption></figure>

Figure 10.4j — XE news (TMB-T1 example)

To exercise XE rights, enter the exercise date and the relevant details. The result will look like Figure 10.4k — click (1) to create.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 229 - คำอธิบาย Figure 10.4k — Create Corporate Action (XE)" alt=""><figcaption></figcaption></figure>

Figure 10.4k — Create Corporate Action (XE)

_For XE, the X-Date represents the exercise date. Resolution Date, Book Closed Date and Payment Period can also be set to the exercise date so they remain aligned._

In Pending Corporate Action, click (2) to confirm.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 230 - คำอธิบาย Figure 10.4l — Confirm pending XE action" alt=""><figcaption></figcaption></figure>

Figure 10.4l — Confirm pending XE action

Role: Fund Manager / Dealer / PF Admin. Navigate to Dealing ▸ Approve X-Transaction, select (3) and click (4) to confirm. The status turns green.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 231 - คำอธิบาย Figure 10.4m — Approve X-Transaction (XE)" alt=""><figcaption></figcaption></figure>

Figure 10.4m — Approve X-Transaction (XE)

Wait for Fund Account / Operation processing. The system will automatically generate Buy / Sell transactions in Dealing ▸ Allocation.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 232 - คำอธิบาย Figure 10.4n — Allocation (XE)" alt=""><figcaption></figcaption></figure>

Figure 10.4n — Allocation (XE)

Role: Fund Account / PF Operation. Navigate to Daily ▸ Generate Transaction, select the transaction and click (5) to complete the process. The status updates from red to green.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 233 - คำอธิบาย Figure 10.4o — Generate Transaction (XE)" alt=""><figcaption></figcaption></figure>

Figure 10.4o — Generate Transaction (XE)

Wait for the Fund Manager. The transaction appears in Post Transaction; follow the standard investment flow until Daily ▸ Close Transaction, then complete the EOD process. Verify holdings in Enquiry ▸ Equity Holding.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 234 - คำอธิบาย Figure 10.4p — Post Transaction (XE)" alt=""><figcaption></figcaption></figure>

Figure 10.4p — Post Transaction (XE)

<br>

&#x20;

***

### X-Type — XD

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 235 - คำอธิบาย Figure 10.4q — XD news (AOT example)" alt=""><figcaption></figcaption></figure>

Figure 10.4q — XD news (AOT example)

Enter the data and click (1) to create.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 236 - คำอธิบาย Figure 10.4r — Create Corporate Action (XD)" alt=""><figcaption></figcaption></figure>

Figure 10.4r — Create Corporate Action (XD)

_Dividend Type — type of dividend (cash or stock). Dividend Interval — payout frequency. Receive Date — when shareholders receive the dividend. Dividend per Unit — amount per share._

Confirm in Pending Corporate Action with click (2).

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 237 - คำอธิบาย Figure 10.4s — Confirm pending XD action" alt=""><figcaption></figcaption></figure>

Figure 10.4s — Confirm pending XD action

Role: Fund Account / PF Operation. Navigate to Daily ▸ Generate Transaction and click (3) to generate. The status updates from red to green. If nothing appears, no portfolio holds the stock during that period.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 238 - คำอธิบาย Figure 10.4t — Generate Transaction (XD)" alt=""><figcaption></figcaption></figure>

Figure 10.4t — Generate Transaction (XD)

Role: Fund Manager. Navigate to Dealing ▸ Post Allocation. Continue the standard investment flow until Daily ▸ Close Transaction and finalize EOD.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 239 - คำอธิบาย Figure 10.4u — Post Allocation (XD)" alt=""><figcaption></figcaption></figure>

Figure 10.4u — Post Allocation (XD)

***

### X-Type — Convert

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 240 - คำอธิบาย Figure 10.4v — Convert news (BROOK example)" alt=""><figcaption></figcaption></figure>

Figure 10.4v — Convert news (BROOK example)

Enter the data — Payment Period, Right Rounding, Security Code, Tradable Date, Ratio and Price (typically 0). Click (1) to create.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 241 - คำอธิบาย Figure 10.4w — Create Corporate Action (Convert)" alt=""><figcaption></figcaption></figure>

Figure 10.4w — Create Corporate Action (Convert)

Confirm in Pending Corporate Action with (2).

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 242 - คำอธิบาย Figure 10.4x — Confirm pending Convert action" alt=""><figcaption></figcaption></figure>

Figure 10.4x — Confirm pending Convert action

Role: Fund Manager / Dealer / PF Admin. In Dealing ▸ Approve X-Transaction, select (3) and click (4) to confirm.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 243 - คำอธิบาย Figure 10.4y — Approve X-Transaction (Convert)" alt=""><figcaption></figcaption></figure>

Figure 10.4y — Approve X-Transaction (Convert)

Role: Fund Account / PF Operation. In Daily ▸ Generate Transaction, run Generate Portfolio for the specific portfolio. Then Fund Manager / Dealer / PF Admin proceeds in Dealing ▸ Post Allocation through to EOD.

***

### X-Type — Split & Increase

Split & Increase reduces the par value while proportionally increasing the number of shares — lowering the stock price and improving liquidity.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 244 - คำอธิบาย Figure 10.4z — RS stock data and news" alt=""><figcaption></figcaption></figure>

Figure 10.4z — RS stock data and news

Enter the data and click (1) to create.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 245 - คำอธิบาย Figure 10.4aa — Create Corporate Action (Split &#x26; Increase)" alt=""><figcaption></figcaption></figure>

Figure 10.4aa — Create Corporate Action (Split & Increase)

_Effective Date — when the change takes effect (Trade Date / Settle Date / Custodian Visibility). Old Par — previous par value. New Par — adjusted par value._

Confirm in Pending Corporate Action with (2).

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 246 - คำอธิบาย Figure 10.4bb — Confirm pending Split &#x26; Increase" alt=""><figcaption></figcaption></figure>

Figure 10.4bb — Confirm pending Split & Increase

Navigate to Daily ▸ Process EOD. For Period (3), select Effective Date − 1, then click (4) to display the transactions.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 247 - คำอธิบาย Figure 10.4cc — Process EOD (Split &#x26; Increase)" alt=""><figcaption></figcaption></figure>

Figure 10.4cc — Process EOD (Split & Increase)

Navigate to Daily ▸ Post Transaction. The system generates the transaction automatically — press Post and complete the EOD.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 248 - คำอธิบาย Figure 10.4dd — Post Transaction (Split &#x26; Increase)" alt=""><figcaption></figcaption></figure>

Figure 10.4dd — Post Transaction (Split & Increase)

Verify the Equity record under Resources ▸ Company Group ▸ Equity — the system updates Par Value automatically.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 249 - คำอธิบาย Figure 10.4ee — Equity record updated" alt=""><figcaption></figcaption></figure>

Figure 10.4ee — Equity record updated

***

### X-Type — XN

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 250 - คำอธิบาย Figure 10.4ff — XN news (BTSGIF example)" alt=""><figcaption></figcaption></figure>

Figure 10.4ff — XN news (BTSGIF example)

Enter the data and click (1) to create.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 251 - คำอธิบาย Figure 10.4gg — Create Corporate Action (XN)" alt=""><figcaption></figcaption></figure>

Figure 10.4gg — Create Corporate Action (XN)

_X-Date — when the stock is marked. Book Closed Date — final shareholder registration date. Capital Decreasing Per Unit — refund per share. Receive Date — payout date._

Confirm in Pending Corporate Action with (2).

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 252 - คำอธิบาย Figure 10.4hh — Confirm pending XN action" alt=""><figcaption></figcaption></figure>

Figure 10.4hh — Confirm pending XN action

Navigate to Daily ▸ Generate Transaction, select the transaction and click (3). The status updates from red to green.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 253 - คำอธิบาย Figure 10.4ii — Generate Transaction (XN)" alt=""><figcaption></figcaption></figure>

Figure 10.4ii — Generate Transaction (XN)

Navigate to Daily ▸ Post Transaction. The system creates two transaction types — Deposit (capital decrease) and Adjusted (updated balance). Post the transactions and complete the EOD.

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 254 - คำอธิบาย Figure 10.4jj — Post Transaction (XN)" alt=""><figcaption></figcaption></figure>

Figure 10.4jj — Post Transaction (XN)

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 255 - คำอธิบาย Figure 10.4kk — Deposit Capital Decreasing detail" alt=""><figcaption></figcaption></figure>

Figure 10.4kk — Deposit: Capital Decreasing detail

<figure><img src="../../../.gitbook/assets/ชื่อเรื่อง Page 256 - คำอธิบาย Figure 10.4ll — Adjusted detail" alt=""><figcaption></figcaption></figure>

Figure 10.4ll — Adjusted detail
