---
description: >-
  Allocation Size configures how the system divides allocations across
  portfolios.
icon: square-sliders
---

# Allocation Size

### Allocation Size

Three modes are available:

### Top First

{% tabs %}
{% tab title="Top First Allocation Mode" %}
Top First Allocation Mode



<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (335).png" alt=""><figcaption></figcaption></figure></div>

| **Component**             | **Description (English)**                                           | **คำอธิบาย (ภาษาไทย)**                                        |
| ------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------- |
| Portfolio Models (Search) | Filter to find a specific set of portfolios or investment models.   | ช่องค้นหาชุดของพอร์ตโฟลิโอหรือโมเดลการลงทุน                   |
| Portfolio Code (Search)   | Filter to find an individual portfolio by its unique ID.            | ช่องค้นหาพอร์ตโฟลิโอรายตัวตามรหัส                             |
| Portfolio Models (Column) | Name of the investment group or model defined for allocation.       | ชื่อกลุ่มการลงทุนหรือโมเดลที่กำหนดไว้สำหรับการจัดสรร          |
| Portfolio (Column)        | Individual portfolio ID linked to the specific model.               | รหัสพอร์ตโฟลิโอรายตัวที่ผูกอยู่กับโมเดลนั้น ๆ                 |
| Weight                    | The specific allocation ratio or weight assigned to each portfolio. | สัดส่วนหรือน้ำหนักที่กำหนดให้แต่ละพอร์ต (เช่น 1.00 หรือ 0.10) |
| Edit Button               | Enable modification of the weight for a specific portfolio.         | ปุ่มสำหรับเริ่มแก้ไขค่าน้ำหนักสัดส่วนในพอร์ตที่ต้องการ        |
| Save Button               | Commit and update all changes made to the allocation sizes.         | ปุ่มสำหรับบันทึกการเปลี่ยนแปลงสัดส่วนทั้งหมดลงสู่ระบบ         |
{% endtab %}

{% tab title="Top First Algorithm Overview" %}
### Top First Allocation Mode

"Prioritize and Fill: High-Weight Portfolios First"

#### The Concept (Waterfall Analogy)

Think of this mode as a "Priority Queue." Portfolios are lined up based on their Weight value. The system fills the orders of those at the front of the line (highest weight) completely before moving to the next person. In this mode, the Weight number does not represent a ratio; it represents Priority.

***

#### The Allocation Process

**Step 1: Rank by Priority (Weight)**

The system ranks all portfolios from highest to lowest Weight.

* Weight 100 = 1st Priority
* Weight 50 = 2nd Priority
* Weight 1 = 3rd Priority

> Note: Portfolios with equal weights are treated as a single "Priority Group."

**Step 2: Distribute Units**

The system looks at the total available units and begins the distribution:

* Scenario A: Sufficient Supply (Full Fill) If there are enough units to satisfy everyone in the current priority group, the system fills their orders 100%. Any remaining units are then passed down to the next priority group.
* Scenario B: Insufficient Supply (Partial Fill) If units run out while filling a priority group, the system distributes the remaining stock so that everyone in that group misses the same amount of units (considering lot size rounding). The process ends immediately. Portfolios in lower priority groups (lower weights) will receive zero units.

#### Illustrative Example

Total Units Available: 1,000 | Total Orders: 1,500 (3 Portfolios ordering 500 units each)

| **Portfolio** | **Weight (Priority)** | **Order Amount** | **Final Allocation** |
| ------------- | --------------------- | ---------------- | -------------------- |
| Portfolio A   | 100                   | 500              | 500 (Full)           |
| Portfolio B   | 50                    | 500              | 500 (Full)           |
| Portfolio C   | 10                    | 500              | 0 (Empty)            |

> Why did Portfolio C get nothing? Because Portfolios A and B had higher priority and consumed the entire 1,000-unit supply before the system could reach the third tier.

***

#### Key Takeaways

* Weight = Order, Not Ratio: A portfolio with Weight 100 does not get twice as many units as Weight 50; it simply gets its entire order filled before Weight 50 is even considered.
* Hard Cut-off: This mode is ideal for limited-supply scenarios (like IPOs or restricted bond issues) where you want to ensure your primary "Model" or "Anchor" portfolios are fully satisfied first.
{% endtab %}
{% endtabs %}



### Distributed

{% tabs %}
{% tab title="Distributed" %}
### Distributed

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (336).png" alt=""><figcaption></figcaption></figure></div>

| **Component**             | **Description (English)**                                           | **คำอธิบาย (ภาษาไทย)**                                        |
| ------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------- |
| Portfolio Models (Search) | Filter to find a specific set of portfolios or investment models.   | ช่องค้นหาชุดของพอร์ตโฟลิโอหรือโมเดลการลงทุน                   |
| Portfolio Code (Search)   | Filter to find an individual portfolio by its unique ID.            | ช่องค้นหาพอร์ตโฟลิโอรายตัวตามรหัส                             |
| Portfolio Models (Column) | Name of the investment group or model defined for allocation.       | ชื่อกลุ่มการลงทุนหรือโมเดลที่กำหนดไว้สำหรับการจัดสรร          |
| Portfolio (Column)        | Individual portfolio ID linked to the specific model.               | รหัสพอร์ตโฟลิโอรายตัวที่ผูกอยู่กับโมเดลนั้น ๆ                 |
| Weight                    | The specific allocation ratio or weight assigned to each portfolio. | สัดส่วนหรือน้ำหนักที่กำหนดให้แต่ละพอร์ต (เช่น 1.00 หรือ 0.10) |
| Edit Button               | Enable modification of the weight for a specific portfolio.         | ปุ่มสำหรับเริ่มแก้ไขค่าน้ำหนักสัดส่วนในพอร์ตที่ต้องการ        |
| Save Button               | Commit and update all changes made to the allocation sizes.         | ปุ่มสำหรับบันทึกการเปลี่ยนแปลงสัดส่วนทั้งหมดลงสู่ระบบ         |
{% endtab %}

{% tab title="Distributed Algorithm Overview" %}
### Distributed Allocation Mode

"Fair Share: Proportional Distribution Based on Weights"

#### The Concept (The Pizza Analogy)

Think of this mode as sharing a large pizza among friends. Each friend has a different "hunger level" (Weight). Instead of giving the whole pizza to the first person, you divide the slices so that everyone gets a piece that matches their hunger level relative to the others.

***

#### The Allocation Process

**Step 1: Calculate the Ratio (Normalization)**

The system looks at the total sum of all weights and determines what percentage each portfolio represents.

* _Example:_ If Port A has Weight 60 and Port B has Weight 40 (Total = 100), Port A is entitled to 60% of the available units, and Port B is entitled to 40%.

**Step 2: The Main Distribution**

The system multiplies the total available units by each portfolio’s percentage.

* Rounding: Because you can't usually buy a fraction of a share (e.g., 0.5 shares), the system rounds the numbers based on the standard Lot Size (e.g., rounding to the nearest 100).

**Step 3: The "Cleanup" Loop (Remaining Units)**

Sometimes, after rounding, there are a few "leftover" units. The system repeats Step 2 using only the remaining units and distributing them among portfolios that haven't had their full orders filled yet. It keeps looping until all units are assigned or no further proportional distribution is possible.

***

#### Illustrative Example

Total Units Available: 1,000 | Portfolios order 1,000 each

| **Portfolio** | **Weight** | **Entitlement (%)** | **Final Allocation** |
| ------------- | ---------- | ------------------- | -------------------- |
| Portfolio A   | 80         | 80%                 | 800 Units            |
| Portfolio B   | 20         | 20%                 | 200 Units            |



> Key Difference: Unlike "Top First," both portfolios receive units at the same time. Portfolio B isn't ignored just because Portfolio A has a higher weight; it simply receives a smaller, proportional share.

***

#### Key Takeaways

* Weight = Percentage, Not Priority: A weight of 100 vs. 50 means the first portfolio will get double the units of the second, provided there is enough supply.
* Balanced Growth: This is the best mode for maintaining a specific "Model" or "Index" across multiple portfolios, ensuring they all grow or shrink in the same proportion.
* Fairness: No portfolio is left empty-handed as long as there are units available to be divided.
{% endtab %}
{% endtabs %}



### Highest NAV

{% tabs %}
{% tab title="Highest NAV" %}
### Highest NAV

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (337).png" alt=""><figcaption></figcaption></figure></div>

| **Component**       | **Description (English)**                                                          | **คำอธิบาย (ภาษาไทย)**                                                 |
| ------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| NAV Shift Threshold | The percentage limit allowed for NAV fluctuation before triggering a reallocation. | เกณฑ์เปอร์เซ็นต์ความผันผวนของ NAV ที่ยอมรับได้ก่อนที่จะทำการจัดสรรใหม่ |
| Save Button         | Commit the threshold and mode settings to the system.                              | ปุ่มบันทึกการตั้งค่าเกณฑ์และโหมดเข้าสู่ระบบ                            |
{% endtab %}

{% tab title="Highest NAV" %}


### Highest NAV Allocation Mode

"Fair Share + Strategic Extras for High-Value Portfolios"

#### The Concept (The Buffet Analogy)

Imagine a group of guests at a buffet. Everyone gets a standard serving based on what they ordered (Proportional). However, if there are leftover snacks, you give them to the guests with the "largest plates" (Highest NAV). But wait—you can't stack the plate too high, or it will spill (NAV Shift Threshold). If a plate is getting too full, you move to the next person.

***

#### The Allocation Process

**Step 1: The "Fair" Start (Proportional)**

The system doesn't just look at the high-value portfolios immediately. First, it gives everyone a fair, proportional slice of the units based on their order size (just like the Distributed Mode).

**Step 2: Find the "Big Plates" (Ranking)**

After the fair share is given, there might be a few "leftover" units (due to rounding or odd lot sizes). The system identifies which portfolios have the Highest NAV (total value) and still have unfilled orders.

**Step 3: Distribute the Extras (The "Spill" Check)**

The system gives the leftovers to the portfolio with the highest NAV first, but it follows a strict safety rule:

* The NAV Shift Threshold: This is a safety limit (e.g., 0.5%). The system calculates if adding these extra units will change the portfolio's total value too much.
* If it stays under the limit: The portfolio gets the units.
* If it hits the limit: The system stops giving to that portfolio and moves to the next highest NAV portfolio.
* If nobody can take them: The units remain unallocated to protect the stability of all portfolios.

***

#### Why use the NAV Shift Threshold?

Without this threshold, a small leftover amount might be "dumped" into one portfolio, making its asset concentration too high. The threshold ensures that the impact of the extra units is tiny and manageable for every portfolio.

***

#### Key Takeaways

* Balanced Foundation: It starts with a fair proportional distribution so everyone gets something.
* Smart Cleanup: It uses the remaining units to "beef up" the portfolios that can handle the volume (High NAV).
* Safety First: The threshold prevents any single portfolio from becoming "unbalanced" or shifting its value too drastically just to soak up leftovers.
{% endtab %}
{% endtabs %}



## Allocation Modes Comparison

| **Feature**    | **Top First**                      | **Distributed**             | **Highest NAV**                           |
| -------------- | ---------------------------------- | --------------------------- | ----------------------------------------- |
| Main Goal      | Priority Fulfillment               | Proportional Fairness       | Strategic Balancing                       |
| Logic          | Fill high weights 100% first       | Give everyone a fair share  | Give extras to high-value ports           |
| Weight Meaning | Priority Ranking (1st, 2nd...)     | Ratio/Percentage (60%, 40%) | Initial Ratio + Strategic Extras          |
| Leftover Units | Move to next weight group          | Distributed proportionally  | Given to high-NAV ports                   |
| Safety Limit   | None                               | None                        | NAV Shift Threshold                       |
| Result         | Low-weight ports may get $$ $0$ $$ | Everyone gets something     | Everyone gets a share; big ports get more |



#### **1. Top First (The Waterfall)**

* Best for: Limited supply assets like IPOs or restricted Bonds.
* Use case: When you have a "VIP" or "Main Model" portfolio that must be filled completely before any secondary portfolios receive units.

#### **2. Distributed (The Pizza Slice)**

* Best for: Standard daily trading or Index tracking.
* Use case: When you want all portfolios to mirror each other's growth and maintain a specific percentage of ownership across the board.

#### **3. Highest NAV (The Stabilizer)**

* Best for: Rebalancing large funds or managing excess liquidity.
* Use case: When you want to ensure that the portfolios with the most capital "soak up" the extra units, but only if it doesn't shift their overall value too drastically.

