---
icon: building-magnifying-glass
---

# Unit Allocation

Unit Allocation serves as the final reconciliation and execution gateway for Fund Managers. Once a confirmation/receive note is received from the broker, the Fund Manager uses this module to transition trades from an "estimated" state to a "finalized" state.

{% hint style="info" %}
**Unit Allocation** is a critical post-trade process within the SouthBridge system designed to distribute investment units or redemption proceeds across multiple portfolios after a transaction has been executed.
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (334).png" alt=""><figcaption></figcaption></figure></div>

| **Component**              | **Description (English)**                                | **คำอธิบาย (ภาษาไทย)**                                       |
| -------------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| Trade Date / Tx No.        | The actual date the trade occurred and its unique ID.    | วันที่ทำรายการซื้อขายจริงและเลขที่อ้างอิงธุรกรรม             |
| Est. NAV/Unit              | The initial estimated price used during order placement. | ราคาต่อหน่วยโดยประมาณที่ใช้ตอนส่งคำสั่งซื้อขาย               |
| Est. No. of Unit           | The projected units to be allocated to each portfolio.   | จำนวนหน่วยที่คาดว่าจะจัดสรรให้แต่ละพอร์ต                     |
| Status (Waiting/Allocated) | Indicates if the trade is pending final confirmation.    | สถานะการจัดสรร (Waiting คือรอใส่ราคาจริงจาก Broker)          |
| NAV/Unit (Final)           | The actual price from the Broker's confirmation note.    | ราคาต่อหน่วยจริง ที่ได้รับยืนยันจาก Broker                   |
| No. of Unit (Final)        | The exact number of units allocated after calculation.   | จำนวนหน่วยสุดท้าย ที่คำนวณจากราคาจริง                        |
| Amount                     | The total monetary value of the allocated units.         | จำนวนเงินรวมสุทธิที่จัดสรรในรายการนั้น ๆ                     |
| Prove Selected             | Final approval button to confirm the allocation.         | ปุ่มอนุมัติเพื่อยืนยันการจัดสรรหน่วยเข้าพอร์ตอย่างเป็นทางการ |



