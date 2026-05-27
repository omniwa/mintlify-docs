---
icon: ballot
---

# Unit Allocation

**Unit Allocation** is a critical post-trade process within the SouthBridge system designed to distribute investment units or redemption proceeds across multiple portfolios after a transaction has been executed.

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (332).png" alt=""><figcaption></figcaption></figure></div>

#### Grouping TX Type

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (333).png" alt=""><figcaption></figcaption></figure></div>

| **Component**              | **Description (English)**                                     | **คำอธิบาย (ภาษาไทย)**                                       |
| -------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------ |
| Date Range (Filter)        | Select the period to view transactions awaiting allocation.   | เลือกช่วงวันที่ที่ต้องการดูรายการเพื่อรอการจัดสรรหน่วย       |
| Filters & Portfolio        | Tools to refine search results or select specific portfolios. | เครื่องมือกรองข้อมูลหรือเลือกเฉพาะพอร์ตที่ต้องการ            |
| Grouping Options           | Group rows by Portfolio, Trade Date, or TX Type.              | ตัวเลือกการจัดกลุ่มข้อมูล (เช่น ตามพอร์ต หรือวันที่ทำรายการ) |
| Est. NAV/Unit              | Estimated NAV per unit used for preliminary calculation.      | ค่า NAV ต่อหน่วยโดยประมาณที่ใช้ในการคำนวณเบื้องต้น           |
| Est. No. of Unit           | Projected number of units to be allocated to the portfolio.   | จำนวนหน่วยลงทุนที่คาดว่าจะได้รับการจัดสรร                    |
| Status (Allocated/Waiting) | Current processing status of the individual transaction.      | สถานะการจัดสรร (เช่น สำเร็จแล้ว หรือ กำลังรอการประมวลผล)     |
| Allocated Date             | The official date when the unit allocation was finalized.     | วันที่ที่มีการจัดสรรหน่วยลงทุนเสร็จสมบูรณ์                   |
| NAV/Unit (Final)           | The actual final NAV per unit used for the transaction.       | ค่า NAV ต่อหน่วยที่แท้จริงซึ่งใช้ในการปิดรายการ              |
| No. of Unit / Amount       | Final number of units allocated and the total monetary value. | จำนวนหน่วยและจำนวนเงินสุทธิที่ได้รับการจัดสรรจริง            |

### Core Functions:

* Pro-rata Distribution: Calculates and assigns the correct number of units (for subscriptions/buys) or cash amounts (for redemptions/sells) to each participating portfolio.
* NAV Application: Applies the finalized Net Asset Value (NAV) per Unit to pending transactions to ensure that the valuation of the trade is accurate and matches official records.
* Status Reconciliation: Transitions transactions from a "Waiting" state (where the trade is known but the final unit count is estimated) to an "Allocated" state (where the actual units are officially recorded).
* Audit Trail: Provides a detailed breakdown of the Est. No. of Units versus the Final No. of Units, ensuring transparency for auditors and compliance teams.

