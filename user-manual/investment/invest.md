---
hidden: true
icon: hand-holding-circle-dollar
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

# Invest

The Investment module is where fund managers record investment plans for their clients. It captures everything from the initial idea to the final list of buy / sell orders, and supports designing reusable Investment Models that can be applied to many portfolios at once.

### Invest

Invest is used to record investment transactions inside a customer’s portfolio. The screen lists every investment that has been created and provides controls for editing, deleting and tracking each one through the approval workflow.

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 73 - คำอธิบาย Figure 4.1a — Investment list interface" alt=""><figcaption></figcaption></figure>

Figure 4.1a — Investment list interface

1\.  Investment Date: Date the investment was created.

2\.  Columns: Toggle which columns are visible.

3\.  Filter: Filter the displayed investments.

4\.  ID / Name: Unique identifier of each investment entry.

5\.  Design Status: Progress of the investment design.

6\.  Created By: User who initiated the investment.

7\.  Investment Date: Creation date of the investment.

8\.  Submitted By: User who submitted the investment for approval.

9\.  Submitted At: Date and time of submission.

10\.  Rule Status: Compliance rule status for the investment.

11\.  Approval Verdict: Approval status (approved, rejected, etc.).

12\.  View Button: Open detailed information about the investment.

13\.  Edit Button: Edit the investment details.

14\.  Delete Button: Remove the investment.

15\.  New Investment Button: Create a new investment entry.

#### 4.1.1 Create a New Investment

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 74 - คำอธิบาย Figure 4.1b — Create Investment dialog" alt=""><figcaption></figcaption></figure>

Figure 4.1b — Create Investment dialog

**New Investment fields**

1\.  Name: Title of the investment.

2\.  Enable Backdate: Enable to set an investment date in the past instead of today.

3\.  Advanced Options: Additional settings (usually all selected).

4\.  Cancel Button: Cancel the investment creation.

5\.  OK Button: Confirm the settings.

**Add Members to Order Group 1**

6\.  Add From Portfolio Model: Add portfolios using a predefined Portfolio Model.

7\.  Add From Portfolio Group: Add portfolios from a Portfolio Group.

8\.  Add From Individual Portfolio: Manually pick specific portfolios.

9\.  Portfolio Table: Lists portfolios available for selection.

10\.  Cancel Button: Discard the selection.

11\.  Add Button: Confirm and create the investment.

#### 4.1.2 Edit Investment — Matrix view

The Matrix is the main editing surface for an investment. Each row is a security, each column is a portfolio. Use the toolbar to switch between Percentage, Units and Value views and to apply Investment Model templates.

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 75 - คำอธิบาย Figure 4.1c — Edit Investment (Matrix)" alt=""><figcaption></figcaption></figure>

Figure 4.1c — Edit Investment (Matrix)

**Toolbar reference**

A.  Undo / Redo: Reverse or reapply the most recent changes.

B.  Percentage: View / enter values as a percentage of the total portfolio.

C.  Unit: View / enter values as units.

D.  Value: View / enter values as a money amount.

E.  Reference Values: Show / hide reference values on each cell.

F.  Column size: Increase or decrease the width of the portfolio columns.

G.  Show submitted orders: Show the orders already submitted for the investment date.

H.  Variation view: Highlight changes (variations) in the orders.

I.  History: Browse the action history and roll back to a specific point.

J.  Concentration view: Aggregate the matrix by sector, exchange or country.

K.  Conform all portfolios: Conform every portfolio to the model’s plan.

L.  Simulation details: Open the simulation details based on the day before the investment date.

M.  Clear: Clear the investment for a portfolio or for a security.

N.  Investment target: Investment target across the whole Investment Group.

O.  Foldout group: Expand or collapse the investment group.

P.  Conform this row: Conform the selected security across all portfolios to the model’s plan.

Q.  Value-Based Investment: Open the value-based investment dialog.

R.  Set value: Set the value to invest in the selected portfolio.

_You cannot submit an investment while it still contains any ERROR-severity issue._

#### 4.1.3 Cell reference values

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 77 - คำอธิบาย Figure 4.1d — Cell reference values pop-up" alt=""><figcaption></figcaption></figure>

Figure 4.1d — Cell reference values pop-up

E1.  Upper Reference Number: Top reference value in the cell.

E2.  Lower Reference Number: Bottom reference value in the cell.

e1.  Before: Value before the change.

e2.  After: Value after the change.

e3.  Difference: Difference between Before and After.

#### 4.1.4 Edit Investment — full Matrix toolbar reference

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 78 - คำอธิบาย Figure 4.1e — Investment (Matrix) Edit Page" alt=""><figcaption></figcaption></figure>

Figure 4.1e — Investment (Matrix) Edit Page

1\.  Active Order Group: Active order group currently displayed.

2\.  Matrix: Main editing page that lists all assets in the investment.

3\.  Orders: Lists the buy / sell transactions resulting from the investment.

4\.  Issues: Highlights any compliance or operational problems.

5\.  Undo Button: Undo the latest action.

6\.  Perspective: Switch between Percentage / Units / Value.

7\.  References: Show or hide reference data inside the table.

8\.  Investment Name & Creation Date: Header that identifies and timestamps the investment.

9\.  Portfolio Assets Table: Lists every asset in the matrix.

10\.  Set Percentage Window: Pop-up that lets you input the desired percentage for the selected cells.

#### 4.1.5 Orders tab

<figure><img src="../.gitbook/assets/ชื่อเรื่อง Page 79 - คำอธิบาย Figure 4.1f — Investment Orders tab" alt=""><figcaption></figcaption></figure>

Figure 4.1f — Investment Orders tab

1\.  Orders: Shows the buy / sell transactions of the investment.

2\.  Import XLSX File: Upload an Excel file containing order rows.

3\.  Download XLSX Template: Download a sample template that matches the import format.

4\.  Orders Table: Lists every transaction in the investment.

5\.  Grouping: Group orders by category.

6\.  Submit Button: Submit the orders for execution.
