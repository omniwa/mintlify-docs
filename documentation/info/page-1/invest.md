# Invest

This page documents the full end-to-end Invest workflow in SouthBridge / Level11: the **Investment ▸ Invest ▸ Edit Investment** screen, **Dealing ▸ Order Placement** where orders are routed after Submit, **Dealing ▸ Allocation** where placed orders are dealt and allocated to portfolios, **Dealing ▸ Commission Adjustment** where the user fine-tunes commission and tax values, **Dealing ▸ Post Allocation** where each transaction is reviewed and confirmed, **Daily ▸ Post Transaction** where confirmed transactions are finalised for the daily close, **Daily ▸ Close Transaction** which is the consolidated archive of every posted (completed) transaction, **Daily ▸ Process EOD** which closes the books for the day by reading the Close Transaction archive and adjusting position, NAV, fee, and GL data system-wide, and **Dealing ▸ Unit Allocation** which is the unit-trust post-EOD step where users enter the confirmed NAV / units received from the broker's confirmation note before re-running EOD. Each tab and section is described with its field definitions in the same format used in the Menu Set up reference.

***

## Page Header

The header bar appears on every tab of the Edit Investment screen and provides the order-group context, investment date, and the global Submit action.

### Active Order Group

**Field reference: Edit Investment Header**

| Field Name            | Description                                                                                                                                              | Field Type     | Linked data from                        | Available in                      |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | --------------------------------------- | --------------------------------- |
| Active Order Group    | The order group currently being edited. Defines which portfolios, model, and rules are in scope for this investment session.                             | Dropdown Field | Order Group: @Order Group Code          | All tabs (Matrix, Orders, Issues) |
| Investment Date       | The trading / order date applied to every order created in this session.                                                                                 | Date Picker    | System: SouthBridge (business calendar) | All tabs                          |
| Submit                | Submits all pending changes (orders, modifications) for approval and placement. Disabled until at least one change exists and no blocking Error is open. | Button         | -                                       | All tabs                          |
| Help (?)              | Opens contextual help for the Edit Investment screen.                                                                                                    | Icon Button    | System: SouthBridge                     | All tabs                          |
| Collapse / Expand (˅) | Collapses or expands the header bar to reclaim vertical space.                                                                                           | Icon Button    | -                                       | All tabs                          |
| Tab: Matrix           | Switches to the allocation matrix view (default).                                                                                                        | Tab Selector   | -                                       | -                                 |
| Tab: Orders           | Switches to the orders list view. Badge shows the current count of pending orders.                                                                       | Tab Selector   | -                                       | -                                 |
| Tab: Issues           | Switches to the rule-violation view. Badge shows total issues split by severity (Warning / Approval / Error).                                            | Tab Selector   | -                                       | -                                 |

***

## Matrix Tab

The Matrix tab is the main allocation workspace. Rows are securities (grouped by category such as Main Currencies, Thailand, Global), columns are portfolios, and the cells show each portfolio's current weight against the model target.

### Toolbar

**Field reference: Matrix Toolbar**

| Field Name             | Description                                                                                                      | Field Type          | Linked data from                 | Available in |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------- | -------------------------------- | ------------ |
| Show / Hide Empty Rows | Two toggle icons that show or hide securities with no current weight.                                            | Icon Toggle         | -                                | Matrix       |
| Perspective: %         | Display values as percentage of portfolio NAV.                                                                   | Toggle Button       | System: SouthBridge              | Matrix       |
| Perspective: Hierarchy | Display values grouped by hierarchical category (e.g., Country, Sector).                                         | Toggle Button       | System: SouthBridge              | Matrix       |
| Perspective: $         | Display values as monetary amounts in the portfolio's reporting currency.                                        | Toggle Button       | System: SouthBridge              | Matrix       |
| References             | Opens the reference panel showing model, benchmark, and rule references for the active order group.              | Button              | Portfolio Model, Benchmark Index | Matrix       |
| Column Width           | Adjust the visual width of the portfolio columns (compact / wide / custom).                                      | Slider / Icon Group | -                                | Matrix       |
| Submitted (count)      | Filter / pill showing the number of already-submitted orders for the active session. Click to toggle visibility. | Filter Pill         | Orders: @Status = Submitted      | Matrix       |
| Orders (count)         | Filter / pill showing the number of pending orders. Click to toggle visibility.                                  | Filter Pill         | Orders: @Status = Not Placed     | Matrix       |
| More (˅)               | Opens additional toolbar actions (export, settings).                                                             | Icon Menu           | -                                | Matrix       |

### Allocation Grid

**Field reference: Matrix Allocation Grid**

| Field Name                        | Description                                                                                                                                                                                            | Field Type                  | Linked data from                                      | Available in             |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------- | ----------------------------------------------------- | ------------------------ |
| Securities                        | The row dimension. Lists each security (or currency) grouped under its category (Main Currencies, Thailand, Global, etc.). Supports collapse / expand of each group.                                   | Hierarchy Column            | Equity: @Security Code, Cash Security: @Security Code | Matrix                   |
| Security Currency                 | Currency tag shown under each security row (e.g., THB, HKD, USD).                                                                                                                                      | Read-only Text              | Security: @Currency                                   | Matrix                   |
| Security Type Badge               | Visual marker such as "V" or "UNIT TRUST (OTC)" indicating the security type / sub-class.                                                                                                              | Badge / Tag                 | Security Type: @Security Type Code                    | Matrix                   |
| Target                            | The model target weight or amount for that security row (or category total).                                                                                                                           | Read-only Number            | Portfolio Model: @Target Weight                       | Matrix                   |
| Target Indicator (lightning icon) | Indicates rows whose target is auto-derived from the model rather than entered manually.                                                                                                               | Icon Indicator              | Portfolio Model                                       | Matrix                   |
| Order Action (▸)                  | Inline shortcut to open the order entry for that security on the active portfolio column.                                                                                                              | Icon Button                 | -                                                     | Matrix                   |
| Portfolio Column Header           | Header showing the portfolio code (e.g., INNO\_X) and current NAV (e.g., 50,622,426.82).                                                                                                               | Column Header               | Portfolio: @Portfolio Code, @NAV                      | Matrix                   |
| Portfolio Header Remove (×)       | Removes that portfolio column from the current matrix view (does not delete the portfolio).                                                                                                            | Icon Button                 | -                                                     | Matrix                   |
| Allocation Cell                   | Each row × portfolio cell. Shows the portfolio's current weight (or amount) for that security with conditional shading - green when within tolerance, red / pink when out of range, neutral otherwise. | Read-only / Editable Number | Holdings + Pending Orders                             | Matrix                   |
| Cell Indicator Dot                | Coloured dot (yellow / red) at the top-left of a cell indicating an active warning or error on that row × portfolio.                                                                                   | Status Icon                 | Issues: @Cell Reference                               | Matrix                   |
| (No Account) Marker               | Shown when a security cannot be held by that portfolio because no eligible account is configured.                                                                                                      | Status Label                | Bank Account / Cash Security                          | Matrix                   |
| Cell Cancel (×)                   | Cancels the pending order in that cell.                                                                                                                                                                | Icon Button                 | -                                                     | Matrix (Order View Mode) |

### Order View Mode

Order View Mode replaces the allocation columns with an editable order-entry strip (one row per security with Buy / Sell, order type, price, expiry, and remarks). It is entered from the toolbar and exited via the "Exit Order View Mode" button.

**Field reference: Matrix Order View Mode**

| Field Name           | Description                                                                                   | Field Type         | Linked data from                   | Available in             |
| -------------------- | --------------------------------------------------------------------------------------------- | ------------------ | ---------------------------------- | ------------------------ |
| Submit n Change(s)   | Submits the pending changes in this mode. The count reflects how many cells have been edited. | Button             | -                                  | Matrix - Order View Mode |
| Discard Changes      | Discards all pending edits in this mode without submitting.                                   | Button             | -                                  | Matrix - Order View Mode |
| Exit Order View Mode | Returns the Matrix grid to the standard allocation view. Unsaved changes are kept.            | Button             | -                                  | Matrix - Order View Mode |
| Securities           | The security row, same as in the standard Matrix.                                             | Hierarchy Column   | Equity / Cash Security             | Matrix - Order View Mode |
| Market Price         | The latest price for that security in the security's currency.                                | Read-only Number   | Price Source / Equity Price Import | Matrix - Order View Mode |
| B / S Indicator      | Buy ("B") or Sell ("S") flag applied to the row when an order is entered.                     | Toggle Button      | System: SouthBridge                | Matrix - Order View Mode |
| Order Type           | The order type to be placed - typically Limit or Market.                                      | Dropdown Field     | System: SouthBridge                | Matrix - Order View Mode |
| Limit Price          | The limit price (only required when Order Type = Limit).                                      | Number Input Field | -                                  | Matrix - Order View Mode |
| Expiry Date          | The order's expiry / time-in-force date. Blank defaults to "Day".                             | Date Picker        | System: SouthBridge                | Matrix - Order View Mode |
| Remarks              | Free-text note attached to the order.                                                         | Text Input Field   | -                                  | Matrix - Order View Mode |
| Cancel Row (×)       | Cancels the order entry on that row.                                                          | Icon Button        | -                                  | Matrix - Order View Mode |

***

## Orders Tab

The Orders tab lists every order generated from the current session. Orders can be created from the Matrix or imported in bulk from an Excel template.

### Import Orders From Spreadsheet

**Field reference: Order Import**

| Field Name              | Description                                                                                          | Field Type           | Linked data from    | Available in |
| ----------------------- | ---------------------------------------------------------------------------------------------------- | -------------------- | ------------------- | ------------ |
| Import .XLSX File       | Opens a file picker to upload an Excel order list. The file must follow the system's order template. | Button (File Upload) | -                   | Orders       |
| Download .XLSX Template | Downloads the latest blank order template with the required column structure.                        | Link                 | System: SouthBridge | Orders       |

### Orders Created After Submission

**Field reference: Orders List**

| Field Name                    | Description                                                                                               | Field Type           | Linked data from                                      | Available in |
| ----------------------------- | --------------------------------------------------------------------------------------------------------- | -------------------- | ----------------------------------------------------- | ------------ |
| Filters                       | Filter pill bar. Each pill toggles a quick filter (e.g., "Approval Related").                             | Filter Pills         | System: SouthBridge                                   | Orders       |
| Grouping                      | Choose how the order rows are grouped. Defaults are TX Type, Order Type, and Security.                    | Toggle Buttons       | System: SouthBridge                                   | Orders       |
| Expand / Collapse Row (+ / −) | Expands or collapses an order to show the per-portfolio breakdown.                                        | Icon Button          | -                                                     | Orders       |
| P. (Priority)                 | Order priority - usually a numeric value indicating the dealing-desk priority for that order.             | Read-only Number     | Orders: @Priority                                     | Orders       |
| TX                            | Transaction type of the order. Typical values are Buy and Sell.                                           | Read-only Text / Tag | System: SouthBridge                                   | Orders       |
| Security                      | The security being traded, with its code and currency tag.                                                | Read-only Text       | Equity: @Security Code, Cash Security: @Security Code | Orders       |
| Market Price                  | The latest market price for the security at order time, including currency.                               | Read-only Number     | Price Source / Equity Price Import                    | Orders       |
| Order Type                    | The placement type of the order (Market, Limit, etc.) plus the relevant price (e.g., "Market 47.75 THB"). | Read-only Text       | System: SouthBridge                                   | Orders       |
| Units                         | Total number of units / shares of the order across all portfolios.                                        | Read-only Number     | Orders: @Units                                        | Orders       |
| Sim. Value                    | Simulated value of the order in the security currency.                                                    | Read-only Number     | Orders: @Simulated Value                              | Orders       |
| Exp. (Expiry)                 | Time-in-force of the order. "Day" means it expires at end of trading day.                                 | Read-only Text       | System: SouthBridge                                   | Orders       |
| Remarks                       | Free-text note attached to the order. "—" if blank.                                                       | Read-only Text       | -                                                     | Orders       |
| Approval                      | Approval status of the order - typical states are Passed, Pending, Failed.                                | Status Tag           | System: SouthBridge                                   | Orders       |
| Status                        | Placement status of the order - typical states are Not Placed, Placed, Filled, Cancelled.                 | Status Tag           | System: SouthBridge                                   | Orders       |

### Portfolio Breakdown (per Order)

Each order can be expanded to show the per-portfolio split that makes up the parent order. This sub-table is shown inline under each parent row.

**Field reference: Order Portfolio Breakdown**

| Field Name         | Description                                                                  | Field Type       | Linked data from                              | Available in       |
| ------------------ | ---------------------------------------------------------------------------- | ---------------- | --------------------------------------------- | ------------------ |
| Portfolio          | Portfolio code participating in the order, with its display name.            | Read-only Text   | Portfolio: @Portfolio Code                    | Orders (sub-table) |
| Units              | Units allocated to that portfolio.                                           | Read-only Number | Orders: @Portfolio Units                      | Orders (sub-table) |
| Lot Size           | The exchange / instrument lot size used to round the portfolio's units.      | Read-only Number | Equity: @Lot Size, Exchange Market: @Lot Size | Orders (sub-table) |
| Sim. Value (Local) | Simulated order value for that portfolio, in the portfolio's local currency. | Read-only Number | Orders: @Portfolio Sim. Value                 | Orders (sub-table) |
| Distribution       | The portfolio's share of the parent order, expressed as a percentage.        | Read-only Number | Calculated                                    | Orders (sub-table) |

***

## Issues Tab

The Issues tab lists every rule violation generated by the current session. Each issue links to the rule that produced it and the cause (portfolio, security, country, etc.).

### Issue Summary

**Field reference: Issue Summary**

| Field Name     | Description                                                                        | Field Type          | Linked data from             | Available in |
| -------------- | ---------------------------------------------------------------------------------- | ------------------- | ---------------------------- | ------------ |
| Total Issues   | Total count of all open issues for the active order group.                         | Read-only Number    | Issues: @Count               | Issues       |
| Warning Count  | Number of Warning-severity issues. Warnings do not block submission.               | Status Tag (Number) | Issues: @Severity = Warning  | Issues       |
| Approval Count | Number of issues that require approval before placement.                           | Status Tag (Number) | Issues: @Severity = Approval | Issues       |
| Error Count    | Number of Error-severity issues. Errors must be resolved before Submit is enabled. | Status Tag (Number) | Issues: @Severity = Error    | Issues       |
| Filters        | Filter pill bar (Warning / Approval / Error) used to narrow the visible issues.    | Filter Pills        | System: SouthBridge          | Issues       |
| Grouping       | Choose how the issues are grouped - typically by Rule or Severity.                 | Toggle Buttons      | System: SouthBridge          | Issues       |

### Issue List

**Field reference: Issue List**

| Field Name                | Description                                                                                                                                                                                                                           | Field Type     | Linked data from                                                                    | Available in |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ----------------------------------------------------------------------------------- | ------------ |
| Expand / Collapse (+ / −) | Expands an issue group to show the individual violation rows that contributed to it.                                                                                                                                                  | Icon Button    | -                                                                                   | Issues       |
| Severity                  | The severity of the issue - Error, Warning, or Approval. Determines colour and whether it blocks submission.                                                                                                                          | Status Tag     | System: SouthBridge                                                                 | Issues       |
| Cause                     | The entity that caused the violation, expressed as a small list of typed tags. Common types: Portfolio, Security, Country, Sector, Currency.                                                                                          | Tag Group      | Portfolio: @Portfolio Code, Equity: @Security Code, System: Country/Sector/Currency | Issues       |
| Rule                      | The name of the rule that fired. Links back to the Manage Rules entry.                                                                                                                                                                | Read-only Text | Manage Rules: @Code                                                                 | Issues       |
| Violation Message         | The message defined on the rule (may include both English and Thai text), explaining what is violated and any threshold / current value.                                                                                              | Read-only Text | Manage Rules: @Violation Message                                                    | Issues       |
| Sub-row Context Bar       | The grey separator line shown above each violation, summarising the comparison: investment date, current value, comparator, and threshold (e.g., "Inv. +0 01-Apr-2026 (Wed): Security Percentage 4.99% > 0.00% Security Percentage"). | Read-only Text | Calculated                                                                          | Issues       |

***

## Order Placement (post-Submit)

After clicking **Submit** on the Invest screen, every approved order is routed to **Dealing ▸ Order Placement**. The dealing desk works through this queue, assigns a broker, and places each order with the market. Orders that fail to place can be retried, blocked, or escalated from the same screen.

### Filter Bar

**Field reference: Order Placement Filter Bar**

| Field Name           | Description                                                                                                           | Field Type     | Linked data from    | Available in    |
| -------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------- | --------------- |
| All Unexpired Orders | Master toggle. When checked, the date range is ignored and every order whose Expiry Date has not yet passed is shown. | Checkbox       | -                   | Order Placement |
| Create Date          | Selector for the date field used by the range pickers below (e.g., Create Date, Investment Date, Expiry Date).        | Dropdown Field | System: SouthBridge | Order Placement |
| Today                | Quick-toggle to set the date range to today's date on both From and To.                                               | Checkbox       | System: SouthBridge | Order Placement |
| Date Range - From    | The earliest date for the selected date field.                                                                        | Date Picker    | System: SouthBridge | Order Placement |
| Date Range - To      | The latest date for the selected date field.                                                                          | Date Picker    | System: SouthBridge | Order Placement |

### Order Type Tabs

**Field reference: Order Placement Tabs**

| Field Name         | Description                                                                               | Field Type                | Linked data from             | Available in    |
| ------------------ | ----------------------------------------------------------------------------------------- | ------------------------- | ---------------------------- | --------------- |
| Unit-Based Orders  | Tab listing orders specified in units / shares. The badge shows the current count.        | Tab Selector (with badge) | Orders: @Order Basis = Unit  | Order Placement |
| Value-Based Orders | Tab listing orders specified in cash value (notional). The badge shows the current count. | Tab Selector (with badge) | Orders: @Order Basis = Value | Order Placement |

### Toolbar and Grouping

**Field reference: Order Placement Toolbar**

| Field Name              | Description                                                                                                                                | Field Type     | Linked data from                                      | Available in    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | -------------- | ----------------------------------------------------- | --------------- |
| Order Placement Title   | Title of the working area with the Last Updated timestamp of the order queue.                                                              | Section Header | System: SouthBridge                                   | Order Placement |
| Columns                 | Opens the column chooser to show / hide columns in the order list.                                                                         | Button         | -                                                     | Order Placement |
| Placing Orders          | Mode toggle. In Placing Orders mode the row actions (Place / Block / Push) are enabled.                                                    | Toggle Button  | -                                                     | Order Placement |
| Watch Compliance        | Mode toggle. In Watch Compliance mode the list shows compliance / approval status alongside each order and the action icons are read-only. | Toggle Button  | -                                                     | Order Placement |
| Grouping: Investment    | Groups order rows by Investment ID.                                                                                                        | Toggle Button  | Orders: @Investment ID                                | Order Placement |
| Grouping: TX Type       | Groups order rows by Buy / Sell.                                                                                                           | Toggle Button  | Orders: @TX Type                                      | Order Placement |
| Grouping: Security      | Groups order rows by Security Code.                                                                                                        | Toggle Button  | Equity: @Security Code, Cash Security: @Security Code | Order Placement |
| Grouping: Security Type | Groups order rows by Security Type Code.                                                                                                   | Toggle Button  | Security Type: @Security Type Code                    | Order Placement |

### Order List

**Field reference: Order Placement List**

| Field Name           | Description                                                                                                                    | Field Type          | Linked data from                                      | Available in    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------- | ----------------------------------------------------- | --------------- |
| Select (Checkbox)    | Row checkbox for bulk actions on multiple orders. The header checkbox selects / deselects every row in the current view.       | Checkbox            | -                                                     | Order Placement |
| TX Type              | The order's transaction type - Buy or Sell.                                                                                    | Status Tag          | System: SouthBridge                                   | Order Placement |
| Security             | Security being traded.                                                                                                         | Read-only Text      | Equity: @Security Code, Cash Security: @Security Code | Order Placement |
| Portfolios           | Portfolios that make up this order. The icon opens a popover listing every participating portfolio and its unit / value share. | Hyperlink / Popover | Portfolio: @Portfolio Code                            | Order Placement |
| Order ID             | System-assigned identifier of the order.                                                                                       | Read-only Number    | Orders: @Order ID                                     | Order Placement |
| Investment ID / Name | The parent investment session that generated the order, with its display name.                                                 | Read-only Text      | Investment: @Investment ID, @Investment Name          | Order Placement |
| Investment Date      | The investment date carried over from the originating Invest session.                                                          | Date                | Investment: @Investment Date                          | Order Placement |
| Expiry Date          | The order's expiry date (after which it is no longer placeable).                                                               | Date                | Orders: @Expiry Date                                  | Order Placement |
| Order Type           | The order's placement type (Market, Limit, etc.).                                                                              | Read-only Text      | System: SouthBridge                                   | Order Placement |
| Ordered              | Total quantity originally ordered (units or value, depending on the active tab).                                               | Read-only Number    | Orders: @Ordered Qty                                  | Order Placement |
| Placeable            | Quantity still available to place. Equals Ordered minus already-placed and minus blocked quantity.                             | Read-only Number    | Calculated                                            | Order Placement |
| Dealing Status       | The order's current dealing status. Typical states: Not Placed, Placed, Partially Placed, Filled, Cancelled, Expired.          | Status Tag          | System: SouthBridge                                   | Order Placement |

### Row Actions

Three icon actions are available on each row when the toolbar is set to **Placing Orders** mode.

**Field reference: Order Placement Row Actions**

| Field Name               | Description                                                                                                                      | Field Type  | Linked data from | Available in    |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | --------------- |
| Place (link icon)        | Opens the Place Order modal for this row, so the dealer can assign a broker and dispatch the order.                              | Icon Button | -                | Order Placement |
| Block (prohibition icon) | Blocks the placeable quantity on this row from being placed. Used when the dealer wants to hold the order without cancelling it. | Icon Button | -                | Order Placement |
| Push (up arrow icon)     | Pushes the order to the next stage (e.g., escalates to a senior dealer or routes to the configured downstream queue).            | Icon Button | -                | Order Placement |

### Place Order Modal

The Place Order modal opens from a row's Place icon. It captures the broker assignment and the quantity to place, then dispatches the order.

**Field reference: Place Order Modal - Header**

| Field Name      | Description                                                                                                                 | Field Type       | Linked data from                                     | Available in      |
| --------------- | --------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------------------------------------------- | ----------------- |
| Modal Title     | Heading of the modal in the form "Place Order (ID: {Order ID})".                                                            | Read-only Text   | Orders: @Order ID                                    | Place Order Modal |
| Order ID        | The order's system identifier.                                                                                              | Read-only Number | Orders: @Order ID                                    | Place Order Modal |
| Tx Type         | Buy / Sell tag carried over from the row.                                                                                   | Status Tag       | Orders: @TX Type                                     | Place Order Modal |
| Security Code   | The security being placed.                                                                                                  | Read-only Text   | Orders: @Security Code                               | Place Order Modal |
| Created By      | The user who created the parent investment / order.                                                                         | Read-only Text   | Orders: @Created By                                  | Place Order Modal |
| Created At      | Timestamp when the order was created.                                                                                       | Read-only Text   | Orders: @Created At                                  | Place Order Modal |
| Price condition | The price condition carried from the order (e.g., MARKET, LIMIT).                                                           | Read-only Text   | Orders: @Price Condition                             | Place Order Modal |
| Members         | The portfolios participating in this order, shown as tags with each portfolio's unit allocation (e.g., "INNO\_X (34,500)"). | Tag Group        | Portfolio: @Portfolio Code, Orders: @Portfolio Units | Place Order Modal |
| Close (×)       | Closes the modal without placing the order.                                                                                 | Icon Button      | -                                                    | Place Order Modal |

**Field reference: Place Order Modal - Form**

| Field Name        | Description                                                                                                                      | Field Type         | Linked data from                                | Available in      |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------------- | ----------------- |
| Broker Group      | The broker group used to filter the broker dropdown. Defaults to "All Brokers".                                                  | Dropdown Field     | Broker Group: @Broker Group Name                | Place Order Modal |
| Broker (required) | The broker to which the order will be sent. Required before Place is enabled.                                                    | Dropdown Field     | Broker: @Broker Code (filtered by Broker Group) | Place Order Modal |
| Placable          | Display of the quantity that can still be placed for this order (read-only summary).                                             | Read-only Number   | Orders: @Placeable                              | Place Order Modal |
| Units (required)  | The quantity to place on this dispatch. Defaults to the full Placable amount; the dealer can split by entering a smaller number. | Number Input Field | -                                               | Place Order Modal |
| Cancel            | Closes the modal without placing the order.                                                                                      | Button             | -                                               | Place Order Modal |
| Place             | Submits the placement to the selected broker for the entered units. Disabled until Broker and Units are valid.                   | Button             | -                                               | Place Order Modal |

***

## Allocation (post-Placement)

Once an order has been placed in **Dealing ▸ Order Placement**, the placed order moves to **Dealing ▸ Allocation**. Here the dealer enters the executed trade details (price, commission, taxes) via the **Deal Placed Order** modal, then distributes the executed units across the participating portfolios via the **Allocate** modal.

The lifecycle of a row on this screen is: **In Progress** (just placed) → **Dealt** (trade details entered) → **Allocating** (some portfolios filled) → **Allocated** (fully allocated).

### Allocation Filter Bar

**Field reference: Allocation Filter Bar**

| Field Name        | Description                                                                                                    | Field Type     | Linked data from    | Available in |
| ----------------- | -------------------------------------------------------------------------------------------------------------- | -------------- | ------------------- | ------------ |
| Show All          | Master toggle. When checked, the date range is ignored and every placed-order row is shown regardless of date. | Checkbox       | -                   | Allocation   |
| Create Date       | Selector for the date field used by the range pickers (e.g., Create Date, Trade Date, Settle Date).            | Dropdown Field | System: SouthBridge | Allocation   |
| Today             | Quick-toggle to set the date range to today's date on both From and To.                                        | Checkbox       | System: SouthBridge | Allocation   |
| Date Range - From | The earliest date for the selected date field.                                                                 | Date Picker    | System: SouthBridge | Allocation   |
| Date Range - To   | The latest date for the selected date field.                                                                   | Date Picker    | System: SouthBridge | Allocation   |

### Allocation Toolbar and Status Filters

**Field reference: Allocation Toolbar**

| Field Name           | Description                                                                                                                                   | Field Type     | Linked data from                                      | Available in |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ----------------------------------------------------- | ------------ |
| Placed Orders Title  | Title of the working area with the Last Updated timestamp of the placed-order queue.                                                          | Section Header | System: SouthBridge                                   | Allocation   |
| Columns              | Opens the column chooser to show / hide columns in the placed-orders list.                                                                    | Button         | -                                                     | Allocation   |
| Filters: All         | Status pill that shows every row regardless of stage.                                                                                         | Filter Pill    | -                                                     | Allocation   |
| Filters: In Progress | Status pill that shows only rows that have been placed but not yet dealt.                                                                     | Filter Pill    | Orders: @Allocation Status = In Progress              | Allocation   |
| Filters: Dealt       | Status pill that shows rows for which the Deal Placed Order modal has been submitted (trade details captured) but allocation has not started. | Filter Pill    | Orders: @Allocation Status = Dealt                    | Allocation   |
| Filters: Allocating  | Status pill that shows rows that are partly allocated to portfolios.                                                                          | Filter Pill    | Orders: @Allocation Status = Allocating               | Allocation   |
| Filters: Allocated   | Status pill that shows rows that are fully allocated.                                                                                         | Filter Pill    | Orders: @Allocation Status = Allocated                | Allocation   |
| Grouping: Order      | Groups rows by parent Order ID.                                                                                                               | Toggle Button  | Orders: @Order ID                                     | Allocation   |
| Grouping: TX Type    | Groups rows by Buy / Sell.                                                                                                                    | Toggle Button  | Orders: @TX Type                                      | Allocation   |
| Grouping: Security   | Groups rows by Security Code.                                                                                                                 | Toggle Button  | Equity: @Security Code, Cash Security: @Security Code | Allocation   |
| Grouping: Broker     | Groups rows by Broker.                                                                                                                        | Toggle Button  | Broker: @Broker Code                                  | Allocation   |

### Placed Orders List

**Field reference: Placed Orders List**

| Field Name        | Description                                                                                                                  | Field Type              | Linked data from                                      | Available in |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ----------------------------------------------------- | ------------ |
| Select (Checkbox) | Row checkbox for bulk actions. The header checkbox selects / deselects every row in the current view.                        | Checkbox                | -                                                     | Allocation   |
| ID                | The allocation row ID (distinct from the parent Order ID). Used to identify the deal lot.                                    | Read-only Number        | Allocation: @Allocation ID                            | Allocation   |
| Order             | The parent Order ID (from Order Placement) that this allocation row was created from.                                        | Read-only Number / Link | Orders: @Order ID                                     | Allocation   |
| Security          | The security being dealt.                                                                                                    | Read-only Text          | Equity: @Security Code, Cash Security: @Security Code | Allocation   |
| Portfolios        | Portfolios attached to the order. The icon opens a popover listing every participating portfolio with its target unit share. | Hyperlink / Popover     | Portfolio: @Portfolio Code                            | Allocation   |
| TX Type           | The order's transaction type - BUY or SELL.                                                                                  | Status Tag              | System: SouthBridge                                   | Allocation   |
| Broker            | The broker that received the order.                                                                                          | Read-only Text          | Broker: @Broker Code                                  | Allocation   |
| Trade Date        | The date on which the trade is dealt (executed).                                                                             | Date                    | Allocation: @Trade Date                               | Allocation   |
| Settle Date       | The settlement date for the dealt trade.                                                                                     | Date                    | Allocation: @Settle Date                              | Allocation   |
| Target Unit       | The target quantity of units for this allocation row.                                                                        | Read-only Number        | Orders: @Placed Units                                 | Allocation   |
| Status            | The current allocation lifecycle state - In Progress, Dealt, Allocating, or Allocated (colour-coded badge).                  | Status Tag              | System: SouthBridge                                   | Allocation   |

### Allocation Row Actions

Each row has a set of icon actions on the right that drive the deal / allocate workflow.

**Field reference: Allocation Row Actions**

| Field Name            | Description                                                                                                                                                 | Field Type  | Linked data from | Available in |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | ------------ |
| Deal (send icon)      | Opens the **Deal Placed Order** modal so the dealer can record the executed price, commission, VAT, and withholding tax. Enabled when Status = In Progress. | Icon Button | -                | Allocation   |
| Allocate (split icon) | Opens the **Allocate** modal so the user can distribute the dealt units across the participating portfolios. Enabled when Status = Dealt or Allocating.     | Icon Button | -                | Allocation   |
| Confirm (check icon)  | Confirms the allocation, moving the row to Allocated. Enabled when allocation totals match the dealt quantity.                                              | Icon Button | -                | Allocation   |
| Cancel (trash icon)   | Cancels / discards this allocation row.                                                                                                                     | Icon Button | -                | Allocation   |
| Push (up arrow icon)  | Pushes the row to the next downstream queue / stage (e.g., Post Allocation).                                                                                | Icon Button | -                | Allocation   |

### Deal Placed Order Modal

Opened from the **Deal** icon on a placed-order row. Captures the executed trade details (price, commission, taxes) and computes Expected Totals. Submitting moves the row from **In Progress** to **Dealt**.

**Field reference: Deal Placed Order Modal - Header**

| Field Name            | Description                                                                                                                                  | Field Type       | Linked data from                             | Available in |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------------------------- | ------------ |
| Modal Title           | Heading "Deal Placed Order" with a close (×) button.                                                                                         | Read-only Text   | -                                            | Deal Modal   |
| Type                  | Transaction type tag carried from the order (Buy / Sell).                                                                                    | Status Tag       | Orders: @TX Type                             | Deal Modal   |
| Security              | Security code and description (from the Equity / Cash Security record).                                                                      | Read-only Text   | Equity: @Security Code, @Description         | Deal Modal   |
| Broker                | Broker code and full company name.                                                                                                           | Read-only Text   | Broker: @Broker Code, Company: @Company Name | Deal Modal   |
| Placed from Order ID  | The parent Order ID that this deal is recorded against.                                                                                      | Read-only Number | Orders: @Order ID                            | Deal Modal   |
| Order Condition       | The order condition carried from the placed order (e.g., Market, Limit).                                                                     | Read-only Text   | Orders: @Order Condition                     | Deal Modal   |
| Portfolio Allocations | Read-only summary showing the total target units and the per-portfolio unit split (e.g., "71,700 Units → INNO\_X: 34,500, INNO\_Y: 37,200"). | Read-only Text   | Orders: @Portfolio Units                     | Deal Modal   |
| Broker Allocations    | Read-only summary showing the total units routed to each broker (e.g., "71,700 Units → YUANTA: 71,700").                                     | Read-only Text   | Orders: @Broker Units                        | Deal Modal   |

**Field reference: Deal Placed Order Modal - Trade Details**

| Field Name                | Description                                                                                                                              | Field Type                        | Linked data from                    | Available in |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- | ----------------------------------- | ------------ |
| Investment Date           | The investment date carried from the originating Invest session (read-only label above the date fields).                                 | Read-only Date                    | Investment: @Investment Date        | Deal Modal   |
| Trade Date                | The execution date of the deal. Defaults to the investment date.                                                                         | Date Picker                       | System: SouthBridge                 | Deal Modal   |
| Settle Date               | The settlement date of the deal. Defaults to Trade Date plus the security's settlement convention.                                       | Date Picker                       | Exchange Market: @Settlement Day(s) | Deal Modal   |
| Cost Per Unit (required)  | The executed price per unit in the security currency.                                                                                    | Number Input Field + Currency Tag | -                                   | Deal Modal   |
| Units (required)          | The executed quantity. The label shows the target (e.g., "Target: 71,700") for reference.                                                | Number Input Field                | -                                   | Deal Modal   |
| Commission Rate           | The commission rate applied to this deal, in percent. May be auto-filled from the broker's commission matrix.                            | Number Input Field (%)            | Broker Commission: @Rate            | Deal Modal   |
| {Broker} Commission Rates | Inline indicator that shows the broker's matched commission rate for this trade with a "View Ranges" link to the full commission matrix. | Read-only Text + Link             | Broker Commission                   | Deal Modal   |
| VAT Rate                  | The VAT rate applied to the commission, in percent.                                                                                      | Number Input Field (%)            | System: SouthBridge                 | Deal Modal   |
| Withholding Tax Rate      | The withholding tax rate applied to the commission, in percent.                                                                          | Number Input Field (%)            | System: SouthBridge                 | Deal Modal   |

**Field reference: Deal Placed Order Modal - Expected Totals**

| Field Name               | Description                                                                                                             | Field Type       | Linked data from | Available in |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------- | ------------ |
| Expected Totals (panel)  | Right-hand panel that recomputes live as the dealer edits price, units, and rates. The expand icon opens a larger view. | Section Header   | Calculated       | Deal Modal   |
| Cost Amount              | Units × Cost Per Unit, in the security currency.                                                                        | Read-only Number | Calculated       | Deal Modal   |
| Commission Excluding VAT | Cost Amount × Commission Rate.                                                                                          | Read-only Number | Calculated       | Deal Modal   |
| VAT                      | Commission Excluding VAT × VAT Rate.                                                                                    | Read-only Number | Calculated       | Deal Modal   |
| Commission Including VAT | Commission Excluding VAT + VAT, less any withholding adjustment as configured.                                          | Read-only Number | Calculated       | Deal Modal   |

**Field reference: Deal Placed Order Modal - Actions**

| Field Name | Description                                                                                                                            | Field Type | Linked data from | Available in |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------- | ------------ |
| Cancel     | Closes the modal without saving.                                                                                                       | Button     | -                | Deal Modal   |
| Deal       | Records the deal, moves the row to Dealt status, and creates the underlying booking entries. Disabled until required fields are valid. | Button     | -                | Deal Modal   |

### Allocate Modal

Opened from the **Allocate** icon (split icon) on a dealt row. Distributes the dealt units across the participating portfolios. Submitting moves the row to **Allocating** (or **Allocated** when fully distributed).

**Field reference: Allocate Modal - Header**

| Field Name            | Description                                                                                                                           | Field Type               | Linked data from                             | Available in   |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | -------------------------------------------- | -------------- |
| Modal Title           | Heading "Allocate - Allocation ID {ID}" with a close (×) button.                                                                      | Read-only Text           | Allocation: @Allocation ID                   | Allocate Modal |
| Type                  | Transaction type tag carried from the deal (Buy / Sell).                                                                              | Status Tag               | Orders: @TX Type                             | Allocate Modal |
| Security              | Security code and description.                                                                                                        | Read-only Text           | Equity: @Security Code, @Description         | Allocate Modal |
| Broker                | Broker code and full company name.                                                                                                    | Read-only Text           | Broker: @Broker Code, Company: @Company Name | Allocate Modal |
| Placed from Order ID  | The parent Order ID this allocation belongs to.                                                                                       | Read-only Number         | Orders: @Order ID                            | Allocate Modal |
| Order Condition       | Order condition carried from the placed order.                                                                                        | Read-only Text           | Orders: @Order Condition                     | Allocate Modal |
| Portfolio Allocations | Read-only summary showing the total target units and per-portfolio unit split.                                                        | Read-only Text           | Orders: @Portfolio Units                     | Allocate Modal |
| Broker Allocations    | Read-only summary showing the total units routed per broker.                                                                          | Read-only Text           | Orders: @Broker Units                        | Allocate Modal |
| Trade Date            | The execution date carried from the deal (read-only).                                                                                 | Read-only Date           | Allocation: @Trade Date                      | Allocate Modal |
| Settle Date           | The settlement date carried from the deal (read-only).                                                                                | Read-only Date           | Allocation: @Settle Date                     | Allocate Modal |
| Cost Per Unit         | The executed price per unit, with the security currency tag (read-only).                                                              | Read-only Number         | Allocation: @Cost Per Unit                   | Allocate Modal |
| Units                 | The dealt quantity with target reference (e.g., "Target: 71,700") (read-only).                                                        | Read-only Number         | Allocation: @Units                           | Allocate Modal |
| Commission Rate       | The commission rate captured in the Deal step (read-only).                                                                            | Read-only Number (%)     | Allocation: @Commission Rate                 | Allocate Modal |
| VAT Rate              | The VAT rate captured in the Deal step (read-only).                                                                                   | Read-only Number (%)     | Allocation: @VAT Rate                        | Allocate Modal |
| Withholding Tax Rate  | The withholding tax rate captured in the Deal step (read-only).                                                                       | Read-only Number (%)     | Allocation: @Withholding Tax Rate            | Allocate Modal |
| Totals (panel)        | Right-hand panel showing Cost Amount, Commission Excluding VAT, VAT, and Commission Including VAT (read-only, carried from the deal). | Section Header + Numbers | Calculated                                   | Allocate Modal |

**Field reference: Allocate Modal - Allocation Controls**

| Field Name           | Description                                                                                                  | Field Type                      | Linked data from    | Available in   |
| -------------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------- | ------------------- | -------------- |
| Allocate By Settings | Opens the configured allocation method dialog (e.g., pro-rata by target, equal split, custom).               | Button                          | System: SouthBridge | Allocate Modal |
| Allocated            | Live indicator of the total currently allocated against the dealt quantity (e.g., "71,700 / 71,700").        | Read-only Number                | Calculated          | Allocate Modal |
| Remaining            | Live indicator of the quantity still unallocated. Shows zero with a green progress bar when fully allocated. | Read-only Number + Progress Bar | Calculated          | Allocate Modal |
| Adjust: Reset        | Clears the manual Adjust column back to zero on every row.                                                   | Button                          | -                   | Allocate Modal |
| Adjust: Auto         | Recomputes the Auto Calc. Allocation column using the active allocation method (e.g., pro-rata to target).   | Button                          | -                   | Allocate Modal |

**Field reference: Allocate Modal - Portfolio Table**

| Field Name            | Description                                                                                                                                                                   | Field Type                      | Linked data from                              | Available in   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | --------------------------------------------- | -------------- |
| Portfolio             | Portfolio code participating in the order.                                                                                                                                    | Read-only Text                  | Portfolio: @Portfolio Code                    | Allocate Modal |
| Ordered Unit          | The portfolio's original target quantity from the order.                                                                                                                      | Read-only Number                | Orders: @Portfolio Units                      | Allocate Modal |
| Ordered %             | The portfolio's target share of the order, in percent.                                                                                                                        | Read-only Number                | Calculated                                    | Allocate Modal |
| Allocated Unit        | The portfolio's quantity already allocated to it from prior deal lots. The (i) icon tooltip explains how this is accumulated across multiple deals.                           | Read-only Number + Info Tooltip | Allocation Ledger                             | Allocate Modal |
| Rounding              | The lot-size / rounding step applied when computing this portfolio's auto allocation (e.g., 100 = round to nearest 100 units).                                                | Number Input Field              | Equity: @Lot Size, Exchange Market: @Lot Size | Allocate Modal |
| Auto Calc. Allocation | The system-computed allocation for the portfolio after rounding. The (i) icon tooltip explains the formula.                                                                   | Read-only Number + Info Tooltip | Calculated                                    | Allocate Modal |
| Adjust                | Editable column for the user's final allocation per portfolio. Defaults to Auto Calc. Allocation; the user can override and the Remaining / Allocated indicators update live. | Number Input Field              | -                                             | Allocate Modal |
| Pagination            | Page selector when there are more portfolios than fit on one page.                                                                                                            | Pagination Control              | -                                             | Allocate Modal |

**Field reference: Allocate Modal - Actions**

| Field Name           | Description                                                                                                                                                             | Field Type | Linked data from | Available in   |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| Cancel               | Closes the modal without saving.                                                                                                                                        | Button     | -                | Allocate Modal |
| Allocate and Confirm | Saves the allocation. The row moves to Allocating if Remaining > 0 or to Allocated if Remaining = 0. Disabled until at least one portfolio has a non-zero Adjust value. | Button     | -                | Allocate Modal |

***

## Commission Adjustment (post-Confirm Allocation)

After the allocation is confirmed on **Dealing ▸ Allocation**, every resulting transaction lands on **Dealing ▸ Commission Adjustment** as an **unconfirmed transaction**. From this screen the user can fine-tune the commission, VAT, and withholding tax per row before sending the transaction downstream for booking. Adjustments can be made one row at a time inline or in bulk via an Excel upload.

### Tab Navigation

**Field reference: Commission Adjustment Tabs**

| Field Name                      | Description                                                                                     | Field Type   | Linked data from | Available in          |
| ------------------------------- | ----------------------------------------------------------------------------------------------- | ------------ | ---------------- | --------------------- |
| Browse Unconfirmed Transactions | Default tab. Lists every unconfirmed transaction so the user can edit commission values inline. | Tab Selector | -                | Commission Adjustment |
| Upload File                     | Tab that lets the user upload an Excel file to apply commission adjustments in bulk.            | Tab Selector | -                | Commission Adjustment |

### Commission Filter Bar

**Field reference: Commission Adjustment Filter Bar**

| Field Name        | Description                                                                                         | Field Type     | Linked data from    | Available in          |
| ----------------- | --------------------------------------------------------------------------------------------------- | -------------- | ------------------- | --------------------- |
| Create Date       | Selector for the date field used by the range pickers (e.g., Create Date, Trade Date, Settle Date). | Dropdown Field | System: SouthBridge | Commission Adjustment |
| Date Range - From | The earliest date for the selected date field.                                                      | Date Picker    | System: SouthBridge | Commission Adjustment |
| Date Range - To   | The latest date for the selected date field.                                                        | Date Picker    | System: SouthBridge | Commission Adjustment |
| Refresh           | Re-runs the query with the current filter values.                                                   | Icon Button    | -                   | Commission Adjustment |

### Additional Filters

**Field reference: Commission Adjustment Additional Filters**

| Field Name         | Description                                                                            | Field Type             | Linked data from           | Available in          |
| ------------------ | -------------------------------------------------------------------------------------- | ---------------------- | -------------------------- | --------------------- |
| From Placed Orders | Filter the list to transactions originating from a specific Order ID or set of orders. | Dropdown Field (multi) | Orders: @Order ID          | Commission Adjustment |
| Portfolios         | Filter the list to transactions for selected portfolio(s).                             | Dropdown Field (multi) | Portfolio: @Portfolio Code | Commission Adjustment |

### Unconfirmed Transactions List

**Field reference: Unconfirmed Transactions List**

| Field Name                       | Description                                                                                                                                                                                                      | Field Type         | Linked data from                                      | Available in          |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------------------- | --------------------- |
| Unconfirmed Transactions (count) | Section heading. The number in parentheses is the count of rows currently shown.                                                                                                                                 | Section Header     | Calculated                                            | Commission Adjustment |
| Download Excel                   | Exports the current list of unconfirmed transactions to an Excel file (useful for bulk editing offline before re-uploading via the Upload File tab).                                                             | Button             | -                                                     | Commission Adjustment |
| Security                         | The security on the transaction. For FX or other non-equity rows the cell shows the transaction identifier (e.g., "FX-TX.10074").                                                                                | Read-only Text     | Equity: @Security Code, Cash Security: @Security Code | Commission Adjustment |
| Portfolio                        | The portfolio that holds the transaction.                                                                                                                                                                        | Read-only Text     | Portfolio: @Portfolio Code                            | Commission Adjustment |
| TX Type                          | The transaction type - Buy or Sell, colour-coded (green / red).                                                                                                                                                  | Status Tag         | System: SouthBridge                                   | Commission Adjustment |
| TX ID                            | The system-assigned transaction identifier.                                                                                                                                                                      | Read-only Number   | Transaction: @TX ID                                   | Commission Adjustment |
| Trade Date                       | The trade date carried over from the deal.                                                                                                                                                                       | Date               | Allocation: @Trade Date                               | Commission Adjustment |
| Unit                             | The transacted quantity for this row.                                                                                                                                                                            | Read-only Number   | Transaction: @Unit                                    | Commission Adjustment |
| Cost Amount                      | The cost amount in the security currency (Unit × Cost Per Unit).                                                                                                                                                 | Read-only Number   | Calculated                                            | Commission Adjustment |
| Calc Commission + VAT            | The system-calculated commission including VAT, derived from the broker's commission matrix and the configured VAT rate. Used as a reference value.                                                              | Read-only Number   | Calculated                                            | Commission Adjustment |
| Commission + VAT                 | The commission including VAT that is currently saved on the transaction.                                                                                                                                         | Read-only Number   | Transaction: @Commission Including VAT                | Commission Adjustment |
| Adj. Commission + VAT            | The adjusted commission including VAT. Editable while the row is in edit mode; otherwise read-only. This is the value that will be booked when the adjustment is submitted.                                      | Number Input Field | Transaction: @Adjusted Commission Including VAT       | Commission Adjustment |
| Settle Amount                    | The expected settlement amount in the security currency, recomputed after adjustment (Cost Amount + Adj. Commission + VAT for Buy, or Cost Amount - Adj. Commission - VAT for Sell, depending on configuration). | Read-only Number   | Calculated                                            | Commission Adjustment |
| Wh. Tax                          | Withholding tax amount on the commission, recomputed when the adjustment changes.                                                                                                                                | Read-only Number   | Calculated                                            | Commission Adjustment |
| Net Amount                       | The net cash impact after all adjustments and taxes.                                                                                                                                                             | Read-only Number   | Calculated                                            | Commission Adjustment |
| Created At                       | Timestamp the transaction was created on this screen.                                                                                                                                                            | Read-only Text     | Transaction: @Created At                              | Commission Adjustment |
| Operation                        | Inline action area. Shows **Edit** when the row is in view mode; switches to **Save** and **Cancel** while the row is in edit mode.                                                                              | Action Buttons     | -                                                     | Commission Adjustment |

### Row Edit Operations

**Field reference: Commission Adjustment Row Operations**

| Field Name | Description                                                                                                                                                            | Field Type | Linked data from | Available in          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------- | --------------------- |
| Edit       | Puts the row into edit mode. The Adj. Commission + VAT cell becomes an editable input and Save / Cancel replace the Edit button. Only one row can be edited at a time. | Button     | -                | Commission Adjustment |
| Save       | Persists the edited Adj. Commission + VAT value on the row, recomputes Settle Amount, Wh. Tax, and Net Amount, and returns the row to view mode.                       | Button     | -                | Commission Adjustment |
| Cancel     | Discards the edit and returns the row to view mode without changes.                                                                                                    | Button     | -                | Commission Adjustment |

### Submit Commission Adjustments

**Field reference: Submit Commission Adjustments**

| Field Name                    | Description                                                                                                                                                            | Field Type | Linked data from | Available in          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------- | --------------------- |
| Submit Commission Adjustments | Commits every saved row in the current list, sending the adjusted transactions downstream for booking. Disabled until at least one row has a pending saved adjustment. | Button     | -                | Commission Adjustment |

### Upload File Tab

Use this tab to apply commission adjustments to many transactions at once by uploading an Excel file with the desired Adj. Commission + VAT values. The expected file format matches the layout produced by the **Download Excel** button on the Browse Unconfirmed Transactions tab, so the typical workflow is: Download Excel → edit offline → upload here.

**Field reference: Commission Adjustment Upload File**

| Field Name        | Description                                                                                                                                                            | Field Type             | Linked data from | Available in                        |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | ---------------- | ----------------------------------- |
| File Picker       | Opens a file dialog to choose the Excel file with adjusted commission values. The file must follow the system's column structure (TX ID, Adj. Commission + VAT, etc.). | Button (File Upload)   | -                | Commission Adjustment - Upload File |
| Validation Result | Shown after upload. Lists rows that passed validation, rows with errors, and any duplicates. The user can correct the file and re-upload before applying.              | Read-only Text / Table | Calculated       | Commission Adjustment - Upload File |
| Apply / Submit    | Applies the validated rows to the unconfirmed transactions, replacing the Adj. Commission + VAT value on each matched TX ID.                                           | Button                 | -                | Commission Adjustment - Upload File |

***

## Post Allocation (Final Confirmation)

After Commission Adjustment is submitted, each resulting transaction lands on **Dealing ▸ Post Allocation** with **Confirmed = NO**. From this screen the user performs the final review and confirms each transaction. Once confirmed, the transaction is locked and forwarded to the downstream accounting / booking pipeline.

The column layout is configurable: the **Columns** toggle in the toolbar lets the user switch between four pre-defined column sets (Allocation, Cash, Costs, Timestamp) so the most relevant fields are shown for the task at hand.

### Post Allocation Filter Bar

**Field reference: Post Allocation Filter Bar**

| Field Name                         | Description                                                                                         | Field Type     | Linked data from    | Available in    |
| ---------------------------------- | --------------------------------------------------------------------------------------------------- | -------------- | ------------------- | --------------- |
| Create Date                        | Selector for the date field used by the range pickers (e.g., Create Date, Trade Date, Settle Date). | Dropdown Field | System: SouthBridge | Post Allocation |
| Today                              | Quick-toggle to set the date range to today's date on both From and To.                             | Checkbox       | System: SouthBridge | Post Allocation |
| Date Range - From                  | The earliest date for the selected date field.                                                      | Date Picker    | System: SouthBridge | Post Allocation |
| Date Range - To                    | The latest date for the selected date field.                                                        | Date Picker    | System: SouthBridge | Post Allocation |
| Page Info Tooltip (i)              | Hover tooltip next to the page title with context-help about Post Allocation.                       | Info Icon      | System: SouthBridge | Post Allocation |
| Post-Allocation Transactions Title | Title of the working area with the Last Updated timestamp of the queue.                             | Section Header | System: SouthBridge | Post Allocation |

### Column Set Toggle

The **Columns** button group switches the visible columns to one of four pre-defined views. The current selection is highlighted (default: Allocation).

**Field reference: Post Allocation Column Sets**

| Field Name          | Description                                                                                                                                                | Field Type    | Linked data from | Available in    |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ---------------- | --------------- |
| Columns: Allocation | Shows allocation-centric columns - Portfolio, TX Type, Security, TX ID, Type, Class, Allocation ID, Broker, Counterparty, Quantity, Unit Cost, Net Amount. | Toggle Button | -                | Post Allocation |
| Columns: Cash       | Shows cash-impact columns - the cash leg(s) of each transaction (currency, debit / credit account, cash amount, FX rate, settlement currency totals).      | Toggle Button | -                | Post Allocation |
| Columns: Costs      | Shows cost / fee columns - Cost Amount, Commission Excluding VAT, VAT, Commission Including VAT, Withholding Tax, Stamp Duty, Other Fees.                  | Toggle Button | -                | Post Allocation |
| Columns: Timestamp  | Shows date / time columns - Trade Date, Settle Date, Tradable Date, Created At, Confirmed At.                                                              | Toggle Button | -                | Post Allocation |

### Status and Asset-Type Filters

Two pill filter groups sit on the right of the toolbar. They are independent: any combination is allowed.

**Field reference: Post Allocation Status and Asset-Type Filters**

| Field Name           | Description                                                             | Field Type  | Linked data from              | Available in    |
| -------------------- | ----------------------------------------------------------------------- | ----------- | ----------------------------- | --------------- |
| Filters: Confirmed   | Status pill that shows rows already confirmed.                          | Filter Pill | Transaction: @Confirmed = YES | Post Allocation |
| Filters: Unconfirmed | Status pill that shows rows still pending confirmation.                 | Filter Pill | Transaction: @Confirmed = NO  | Post Allocation |
| Filters: Equity      | Asset-type pill that shows Equity-class transactions.                   | Filter Pill | Transaction: @Class = EQUITY  | Post Allocation |
| Filters: Cash        | Asset-type pill that shows Cash-class transactions (FX, deposit, etc.). | Filter Pill | Transaction: @Class = CASH    | Post Allocation |

### Post Allocation Grouping

**Field reference: Post Allocation Grouping**

| Field Name          | Description                                                                                                                          | Field Type    | Linked data from                                      | Available in    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------- | ----------------------------------------------------- | --------------- |
| Grouping: Order     | Groups rows by parent Order ID.                                                                                                      | Toggle Button | Orders: @Order ID                                     | Post Allocation |
| Grouping: TX Type   | Groups rows by Buy / Sell.                                                                                                           | Toggle Button | Orders: @TX Type                                      | Post Allocation |
| Grouping: Security  | Groups rows by Security Code.                                                                                                        | Toggle Button | Equity: @Security Code, Cash Security: @Security Code | Post Allocation |
| Grouping: Portfolio | Groups rows by Portfolio Code.                                                                                                       | Toggle Button | Portfolio: @Portfolio Code                            | Post Allocation |
| Grouping: More (⋮)  | Reveals additional grouping options (e.g., Broker, Counterparty, Trade Date) and the count of currently-hidden options ("(n More)"). | Icon Menu     | System: SouthBridge                                   | Post Allocation |

### Post-Allocation Transactions List

The following table lists every column that can appear in the list across the four column sets. Columns marked as common are always visible; the others appear only when the corresponding **Columns** toggle is active.

**Field reference: Post-Allocation Transactions List**

| Field Name          | Description                                                                                                                                            | Field Type         | Linked data from                                      | Available in             |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | ----------------------------------------------------- | ------------------------ |
| Select (Checkbox)   | Row checkbox for bulk actions. The header checkbox selects / deselects every row in the current view.                                                  | Checkbox           | -                                                     | Common (all column sets) |
| Portfolio           | The portfolio that holds the transaction.                                                                                                              | Read-only Text     | Portfolio: @Portfolio Code                            | Common                   |
| TX Type             | The transaction type - BUY or SELL, colour-coded.                                                                                                      | Status Tag         | System: SouthBridge                                   | Common                   |
| Security            | The security on the transaction.                                                                                                                       | Read-only Text     | Equity: @Security Code, Cash Security: @Security Code | Common                   |
| Confirmed           | Confirmation status badge - YES (green) when confirmed, NO (red) while still pending.                                                                  | Status Tag         | Transaction: @Confirmed                               | Common                   |
| Operation           | Inline action area showing the **Confirm** and **Edit** icons.                                                                                         | Action Buttons     | -                                                     | Common                   |
| TX ID               | The system-assigned transaction identifier.                                                                                                            | Read-only Number   | Transaction: @TX ID                                   | Allocation               |
| Type                | The instrument type of the security (e.g., Stock-TH).                                                                                                  | Read-only Text     | Security Type: @Description                           | Allocation               |
| Class               | The high-level asset class of the security (e.g., EQUITY, CASH).                                                                                       | Status Tag         | Security Type: @Asset Class                           | Allocation               |
| Allocation ID       | The allocation lot identifier carried from the Allocation screen.                                                                                      | Read-only Number   | Allocation: @Allocation ID                            | Allocation               |
| Broker              | The broker that executed the transaction.                                                                                                              | Read-only Text     | Broker: @Broker Code                                  | Allocation               |
| Counterparty        | The counterparty for non-broker transactions (or em-dash "—" if not applicable).                                                                       | Read-only Text     | Counterparty: @Reference Code                         | Allocation               |
| Quantity            | The transacted quantity, shown with full decimal precision (e.g., 34,500.000000).                                                                      | Read-only Number   | Transaction: @Quantity                                | Allocation               |
| Unit Cost           | The executed price per unit in the security currency, shown with full decimal precision.                                                               | Read-only Number   | Transaction: @Unit Cost                               | Allocation               |
| Net Amount          | The net cash impact of the transaction after all costs and taxes.                                                                                      | Read-only Number   | Calculated                                            | Allocation, Timestamp    |
| Trade Date          | The trade (execution) date carried from the Allocation deal.                                                                                           | Date               | Allocation: @Trade Date                               | Timestamp                |
| Settle Date         | The settlement date carried from the Allocation deal.                                                                                                  | Date               | Allocation: @Settle Date                              | Timestamp                |
| Tradable Date       | The date from which the resulting position is tradable. Used for non-standard instruments such as IPO / subscription where it differs from Trade Date. | Date               | Transaction: @Tradable Date                           | Timestamp                |
| Created At          | Timestamp the transaction was created in Post Allocation.                                                                                              | Read-only Text     | Transaction: @Created At                              | Timestamp                |
| Remarks             | Free-text remark on the transaction (blank by default).                                                                                                | Read-only Text     | Transaction: @Remarks                                 | Timestamp                |
| Pagination Controls | Standard pagination bar at the bottom right - "n-m of total", page navigation, and page-size dropdown (default 30 / page).                             | Pagination Control | -                                                     | Post Allocation          |

### Post Allocation Row Actions

**Field reference: Post Allocation Row Actions**

| Field Name           | Description                                                                                                                                                                                                                    | Field Type  | Linked data from | Available in    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- | ---------------- | --------------- |
| Confirm (check icon) | Confirms the transaction. The row's Confirmed badge flips from NO to YES, the row is locked, and the transaction is forwarded downstream for booking. Hovering shows the tooltip "Confirm". Enabled only while Confirmed = NO. | Icon Button | -                | Post Allocation |
| Edit (pencil icon)   | Opens an inline / modal editor for the editable fields on the row (e.g., Remarks, Tradable Date, and any field configured as adjustable in Post Allocation). Disabled once the row is Confirmed.                               | Icon Button | -                | Post Allocation |

***

## Post Transaction (Final Daily Confirmation)

**Daily ▸ Post Transaction** is the last stop in the Invest pipeline. Every transaction that has been confirmed in **Dealing ▸ Post Allocation** lands here as a **Confirmed Transaction** awaiting the final daily-close confirmation. From this screen the user reviews the complete transaction record (identifiers, quantities, cost, commission, taxes, audit trail) and finalises each row, after which the transaction is fully locked and made available to the daily NAV / accounting cycle.

Note that this screen is structurally similar to Post Allocation but the data is much richer: instead of a column-set toggle it uses a single **Columns: All** view that scrolls horizontally to surface every field.

### Post Transaction Filter Bar

**Field reference: Post Transaction Filter Bar**

| Field Name                     | Description                                                                          | Field Type     | Linked data from    | Available in     |
| ------------------------------ | ------------------------------------------------------------------------------------ | -------------- | ------------------- | ---------------- |
| Transaction Trade Date (label) | Header label clarifying that the date range applies to the transaction's Trade Date. | Section Label  | -                   | Post Transaction |
| Today                          | Quick-toggle to set the date range to today's date on both From and To.              | Checkbox       | System: SouthBridge | Post Transaction |
| Date Range - From              | The earliest Trade Date to include.                                                  | Date Picker    | System: SouthBridge | Post Transaction |
| Date Range - To                | The latest Trade Date to include.                                                    | Date Picker    | System: SouthBridge | Post Transaction |
| Page Info Tooltip (i)          | Hover tooltip next to the page title with context-help about Post Transaction.       | Info Icon      | System: SouthBridge | Post Transaction |
| Confirmed Transactions Title   | Title of the working area with the Last Updated timestamp of the queue.              | Section Header | System: SouthBridge | Post Transaction |

### Post Transaction Toolbar

**Field reference: Post Transaction Toolbar**

| Field Name      | Description                                                                                                                           | Field Type    | Linked data from                     | Available in     |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ------------------------------------ | ---------------- |
| Columns: All    | Single column-set toggle that shows every column in the list (the list scrolls horizontally rather than using multiple view buckets). | Toggle Button | -                                    | Post Transaction |
| Filters: Equity | Asset-type pill that shows Equity-class transactions. The "+/-" toggle adds / removes the pill from the active filter.                | Filter Pill   | Security Type: @Asset Class = EQUITY | Post Transaction |
| Filters: Cash   | Asset-type pill that shows Cash-class transactions (FX, deposit, etc.).                                                               | Filter Pill   | Security Type: @Asset Class = CASH   | Post Transaction |

### Post Transaction Grouping

**Field reference: Post Transaction Grouping**

| Field Name          | Description                                                                                                                                                                            | Field Type    | Linked data from                                      | Available in     |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ----------------------------------------------------- | ---------------- |
| Grouping: Order     | Groups rows by parent Order ID.                                                                                                                                                        | Toggle Button | Orders: @Order ID                                     | Post Transaction |
| Grouping: Portfolio | Groups rows by Portfolio Code.                                                                                                                                                         | Toggle Button | Portfolio: @Portfolio Code                            | Post Transaction |
| Grouping: TX Type   | Groups rows by Buy / Sell.                                                                                                                                                             | Toggle Button | Orders: @TX Type                                      | Post Transaction |
| Grouping: Security  | Groups rows by Security Code.                                                                                                                                                          | Toggle Button | Equity: @Security Code, Cash Security: @Security Code | Post Transaction |
| Grouping: More (⋮)  | Reveals additional grouping options. The count "(n More)" indicates how many additional grouping fields are available (e.g., Broker, Dealer, Confirmed By, Trade Date, Allocation ID). | Icon Menu     | System: SouthBridge                                   | Post Transaction |

### Confirmed Transactions List - Identifiers

The list spans many columns and is split here into three logical groups (identifiers, amounts, audit) for readability. In the application all columns appear in a single horizontally-scrollable table.

**Field reference: Confirmed Transactions - Identifiers**

| Field Name        | Description                                                                                                           | Field Type           | Linked data from                                      | Available in     |
| ----------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------- | ----------------------------------------------------- | ---------------- |
| Select (Checkbox) | Row checkbox for bulk actions. The header checkbox selects / deselects every row in the current view.                 | Checkbox             | -                                                     | Post Transaction |
| Portfolio         | The portfolio that holds the transaction.                                                                             | Read-only Text       | Portfolio: @Portfolio Code                            | Post Transaction |
| TX ID             | The system-assigned transaction identifier.                                                                           | Read-only Number     | Transaction: @TX ID                                   | Post Transaction |
| Limit             | The order's limit / order condition carried from Order Placement (e.g., NORMAL, LIMIT, MARKET).                       | Read-only Text / Tag | Orders: @Order Condition                              | Post Transaction |
| Type              | The instrument type of the security (e.g., Stock-TH).                                                                 | Read-only Text       | Security Type: @Description                           | Post Transaction |
| Security          | The security code on the transaction.                                                                                 | Read-only Text       | Equity: @Security Code, Cash Security: @Security Code | Post Transaction |
| Ref.Security      | Reference security, used when the transaction relates to a derivative or convertible (otherwise blank).               | Read-only Text       | Equity: @Security Code                                | Post Transaction |
| TX Type           | The transaction type - BUY or SELL, colour-coded.                                                                     | Status Tag           | System: SouthBridge                                   | Post Transaction |
| Cash TX Type      | The cash-leg transaction type (e.g., Buy Cash, Sell Cash, Subscription, Redemption). Blank for non-cash transactions. | Read-only Text       | Cash GL: @Cash TX Type                                | Post Transaction |
| Cash GL           | The Cash GL code applied to the cash leg of the transaction (blank for pure security legs).                           | Read-only Text       | Cash GL: @Cash GL Code                                | Post Transaction |
| Allocation ID     | The allocation lot identifier carried from the Allocation screen.                                                     | Read-only Number     | Allocation: @Allocation ID                            | Post Transaction |
| Trade Date        | The trade (execution) date carried from the Allocation deal.                                                          | Date                 | Allocation: @Trade Date                               | Post Transaction |
| Settle Date       | The settlement date carried from the Allocation deal.                                                                 | Date                 | Allocation: @Settle Date                              | Post Transaction |

### Confirmed Transactions List - Amounts

**Field reference: Confirmed Transactions - Amounts**

| Field Name        | Description                                                                                                                                            | Field Type       | Linked data from                       | Available in     |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------- | -------------------------------------- | ---------------- |
| Tradable Date     | The date from which the resulting position is tradable. Used for non-standard instruments such as IPO / subscription where it differs from Trade Date. | Date             | Transaction: @Tradable Date            | Post Transaction |
| Ccy.              | The currency of the security and of the amounts on this row (e.g., THB).                                                                               | Read-only Text   | Currency: @Currency Code               | Post Transaction |
| Quantity          | The transacted quantity with full decimal precision (e.g., 5,300.000000).                                                                              | Read-only Number | Transaction: @Quantity                 | Post Transaction |
| Unit Cost         | The executed price per unit in the security currency, with full decimal precision.                                                                     | Read-only Number | Transaction: @Unit Cost                | Post Transaction |
| Face Amount       | The face / par value amount, used for fixed-income or par-quoted instruments. Zero for equity.                                                         | Read-only Number | Transaction: @Face Amount              | Post Transaction |
| Cost              | The cost amount in the security currency (Quantity × Unit Cost), before commission and taxes.                                                          | Read-only Number | Calculated                             | Post Transaction |
| Commission & VAT  | Commission including VAT, carried from the Commission Adjustment step.                                                                                 | Read-only Number | Transaction: @Commission Including VAT | Post Transaction |
| Settlement Amount | The settlement amount in the security currency (Cost + Commission & VAT for Buy, or Cost - Commission & VAT for Sell, depending on configuration).     | Read-only Number | Calculated                             | Post Transaction |

### Confirmed Transactions List - Audit and Confirmation

**Field reference: Confirmed Transactions - Audit and Confirmation**

| Field Name          | Description                                                                                                                | Field Type         | Linked data from           | Available in     |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------ | -------------------------- | ---------------- |
| Yield               | The yield on the transaction (used for fixed-income / interest-bearing instruments; 0.000000 when not applicable).         | Read-only Number   | Calculated                 | Post Transaction |
| Wht. Amount         | Withholding tax amount on the commission, recomputed from Commission Adjustment values.                                    | Read-only Number   | Calculated                 | Post Transaction |
| Net Amount          | The net cash impact of the transaction after all costs and taxes.                                                          | Read-only Number   | Calculated                 | Post Transaction |
| Broker              | The broker that executed the transaction.                                                                                  | Read-only Text     | Broker: @Broker Code       | Post Transaction |
| Dealer              | The user (dealer) who placed and / or dealt the transaction.                                                               | Read-only Text     | Transaction: @Dealer       | Post Transaction |
| Created At          | Timestamp the transaction record was created.                                                                              | Read-only Text     | Transaction: @Created At   | Post Transaction |
| Confirmed By        | The user who confirmed the transaction in Post Allocation.                                                                 | Read-only Text     | Transaction: @Confirmed By | Post Transaction |
| Confirmed At        | Timestamp of the Post Allocation confirmation.                                                                             | Read-only Text     | Transaction: @Confirmed At | Post Transaction |
| Remarks             | Free-text remark on the transaction (blank by default).                                                                    | Read-only Text     | Transaction: @Remarks      | Post Transaction |
| Pagination Controls | Standard pagination bar at the bottom right - "n-m of total", page navigation, and page-size dropdown (default 30 / page). | Pagination Control | -                          | Post Transaction |

### Post Transaction Row Actions

**Field reference: Post Transaction Row Actions**

| Field Name           | Description                                                                                                                                                                                                           | Field Type  | Linked data from | Available in     |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | ---------------- |
| Confirm (check icon) | Performs the final daily-close confirmation on the transaction. The row is fully locked and forwarded to the daily NAV / accounting cycle. Enabled while the transaction is still pending the final confirmation.     | Icon Button | -                | Post Transaction |
| Edit (pencil icon)   | Opens an inline / modal editor for the still-editable fields on the row (typically Remarks and any field configured as adjustable in Post Transaction). Disabled once the row is finally confirmed.                   | Icon Button | -                | Post Transaction |
| View (eye icon)      | Opens a read-only detail view of the complete transaction record, including the upstream audit trail (Order, Allocation, Commission Adjustment, Post Allocation). Always enabled, including after final confirmation. | Icon Button | -                | Post Transaction |

***

## Close Transaction (Posted / Completed Transactions)

**Daily ▸ Close Transaction** is the consolidated archive of every transaction that has been **posted** (i.e., made it through Post Transaction and on into the books). The list is read-mostly; the only write actions available are **Cancel** (to reverse / un-post a transaction) and **View** (to inspect the full record). Each row carries a **Post Seq** assigned at posting time so that a transaction's place in the daily ledger is uniquely identifiable.

This screen is structurally similar to Post Transaction, with two differences:

1. The header reads **Posted Transactions** instead of "Confirmed Transactions" and rows include the **Post Seq** column.
2. The toolbar offers two column-set toggles - **All** (the default super-set) and **Timestamp** (date-only view) - rather than the single "All" view used by Post Transaction.

### Close Transaction Filter Bar

**Field reference: Close Transaction Filter Bar**

| Field Name                     | Description                                                                          | Field Type     | Linked data from    | Available in      |
| ------------------------------ | ------------------------------------------------------------------------------------ | -------------- | ------------------- | ----------------- |
| Transaction Trade Date (label) | Header label clarifying that the date range applies to the transaction's Trade Date. | Section Label  | -                   | Close Transaction |
| Today                          | Quick-toggle to set the date range to today's date on both From and To.              | Checkbox       | System: SouthBridge | Close Transaction |
| Date Range - From              | The earliest Trade Date to include.                                                  | Date Picker    | System: SouthBridge | Close Transaction |
| Date Range - To                | The latest Trade Date to include.                                                    | Date Picker    | System: SouthBridge | Close Transaction |
| Page Info Tooltip (i)          | Hover tooltip next to the page title with context-help about Close Transaction.      | Info Icon      | System: SouthBridge | Close Transaction |
| Posted Transactions Title      | Title of the working area with the Last Updated timestamp of the archive.            | Section Header | System: SouthBridge | Close Transaction |

### Close Transaction Toolbar

**Field reference: Close Transaction Toolbar**

| Field Name         | Description                                                                                                                                        | Field Type    | Linked data from                     | Available in      |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ------------------------------------ | ----------------- |
| Columns: All       | Default column set that shows every column in the archive (the list scrolls horizontally).                                                         | Toggle Button | -                                    | Close Transaction |
| Columns: Timestamp | Compact column set that hides amounts and shows only date / time-related columns (Trade Date, Settle Date, Tradable Date, Post Date / Created At). | Toggle Button | -                                    | Close Transaction |
| Filters: Equity    | Asset-type pill that shows Equity-class transactions. The "+/-" toggle adds / removes the pill from the active filter.                             | Filter Pill   | Security Type: @Asset Class = EQUITY | Close Transaction |
| Filters: Cash      | Asset-type pill that shows Cash-class transactions (FX, deposit, etc.).                                                                            | Filter Pill   | Security Type: @Asset Class = CASH   | Close Transaction |

### Close Transaction Grouping

**Field reference: Close Transaction Grouping**

| Field Name          | Description                                                                                                                                                              | Field Type    | Linked data from                                      | Available in      |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------- | ----------------------------------------------------- | ----------------- |
| Grouping: Order     | Groups rows by parent Order ID.                                                                                                                                          | Toggle Button | Orders: @Order ID                                     | Close Transaction |
| Grouping: TX Type   | Groups rows by Buy / Sell.                                                                                                                                               | Toggle Button | Orders: @TX Type                                      | Close Transaction |
| Grouping: Portfolio | Groups rows by Portfolio Code.                                                                                                                                           | Toggle Button | Portfolio: @Portfolio Code                            | Close Transaction |
| Grouping: Security  | Groups rows by Security Code.                                                                                                                                            | Toggle Button | Equity: @Security Code, Cash Security: @Security Code | Close Transaction |
| Grouping: More (⋮)  | Reveals additional grouping options. The count "(n More)" indicates how many additional grouping fields are available (e.g., Broker, Dealer, Trade Date, Allocation ID). | Icon Menu     | System: SouthBridge                                   | Close Transaction |

### Posted Transactions List - Identifiers

The list spans many columns and is split here into three logical groups (identifiers, trade and quantity, amounts and broker) for readability. In the application all columns appear in a single horizontally-scrollable table when **Columns: All** is selected.

**Field reference: Posted Transactions - Identifiers**

| Field Name        | Description                                                                                                                                                               | Field Type           | Linked data from                                      | Available in      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ----------------------------------------------------- | ----------------- |
| Select (Checkbox) | Row checkbox for bulk actions. The header checkbox selects / deselects every row in the current view.                                                                     | Checkbox             | -                                                     | Close Transaction |
| Portfolio         | The portfolio that holds the transaction.                                                                                                                                 | Read-only Text       | Portfolio: @Portfolio Code                            | Close Transaction |
| TX ID             | The system-assigned transaction identifier.                                                                                                                               | Read-only Number     | Transaction: @TX ID                                   | Close Transaction |
| Post Seq          | The sequential number assigned to the transaction when it was posted. Used to identify its position in the daily ledger and to support reversal in the original sequence. | Read-only Number     | Transaction: @Post Seq                                | Close Transaction |
| Limit             | The order's limit / order condition carried from Order Placement (e.g., NORMAL, LIMIT, MARKET).                                                                           | Read-only Text / Tag | Orders: @Order Condition                              | Close Transaction |
| Type              | The instrument type of the security (e.g., UT-Feeder Fund, Stock-TH).                                                                                                     | Read-only Text       | Security Type: @Description                           | Close Transaction |
| Security          | The security code on the transaction.                                                                                                                                     | Read-only Text       | Equity: @Security Code, Cash Security: @Security Code | Close Transaction |
| Ref.Security      | Reference security, used when the transaction relates to a derivative or convertible (otherwise blank).                                                                   | Read-only Text       | Equity: @Security Code                                | Close Transaction |
| TX Type           | The transaction type - BUY or SELL, colour-coded.                                                                                                                         | Status Tag           | System: SouthBridge                                   | Close Transaction |
| Cash TX Type      | The cash-leg transaction type (e.g., Buy Cash, Sell Cash, Subscription, Redemption). Blank for non-cash transactions.                                                     | Read-only Text       | Cash GL: @Cash TX Type                                | Close Transaction |
| Cash GL           | The Cash GL code applied to the cash leg of the transaction (blank for pure security legs).                                                                               | Read-only Text       | Cash GL: @Cash GL Code                                | Close Transaction |
| Allocation ID     | The allocation lot identifier carried from the Allocation screen.                                                                                                         | Read-only Number     | Allocation: @Allocation ID                            | Close Transaction |

### Posted Transactions List - Trade and Quantity

**Field reference: Posted Transactions - Trade and Quantity**

| Field Name    | Description                                                                                                                             | Field Type       | Linked data from            | Available in      |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------------------- | ----------------- |
| Trade Date    | The trade (execution) date of the transaction.                                                                                          | Date             | Allocation: @Trade Date     | Close Transaction |
| Settle Date   | The settlement date of the transaction.                                                                                                 | Date             | Allocation: @Settle Date    | Close Transaction |
| Tradable Date | The date from which the resulting position is tradable (used for non-standard instruments such as IPO / subscription; blank otherwise). | Date             | Transaction: @Tradable Date | Close Transaction |
| Ccy.          | The currency of the security and of the amounts on this row (e.g., THB).                                                                | Read-only Text   | Currency: @Currency Code    | Close Transaction |
| Quantity      | The transacted quantity, shown with full decimal precision (e.g., 13,952.971250).                                                       | Read-only Number | Transaction: @Quantity      | Close Transaction |
| Unit Cost     | The executed price per unit in the security currency, shown with full decimal precision.                                                | Read-only Number | Transaction: @Unit Cost     | Close Transaction |
| Face Amount   | The face / par value amount, used for fixed-income or par-quoted instruments. Zero for equity / unit trust.                             | Read-only Number | Transaction: @Face Amount   | Close Transaction |

### Posted Transactions List - Amounts and Broker

**Field reference: Posted Transactions - Amounts and Broker**

| Field Name          | Description                                                                                                                                        | Field Type         | Linked data from                       | Available in      |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | -------------------------------------- | ----------------- |
| Cost                | The cost amount in the security currency (Quantity × Unit Cost), before commission and taxes.                                                      | Read-only Number   | Calculated                             | Close Transaction |
| Commission & VAT    | Commission including VAT, carried from the Commission Adjustment step.                                                                             | Read-only Number   | Transaction: @Commission Including VAT | Close Transaction |
| Settlement Amount   | The settlement amount in the security currency (Cost + Commission & VAT for Buy, or Cost - Commission & VAT for Sell, depending on configuration). | Read-only Number   | Calculated                             | Close Transaction |
| Yield               | The yield on the transaction (used for fixed-income / interest-bearing instruments; 0.000000 when not applicable).                                 | Read-only Number   | Calculated                             | Close Transaction |
| Wht. Amount         | Withholding tax amount on the commission.                                                                                                          | Read-only Number   | Calculated                             | Close Transaction |
| Net Amount          | The net cash impact of the transaction after all costs and taxes.                                                                                  | Read-only Number   | Calculated                             | Close Transaction |
| Broker              | The broker that executed the transaction.                                                                                                          | Read-only Text     | Broker: @Broker Code                   | Close Transaction |
| Pagination Controls | Standard pagination bar at the bottom right - "n-m of total", page navigation, and page-size dropdown (default 30 / page).                         | Pagination Control | -                                      | Close Transaction |

### Close Transaction Row Actions

Posted transactions are largely immutable - the only write action is a controlled reversal. There is no Edit or Confirm action on this screen.

**Field reference: Close Transaction Row Actions**

| Field Name      | Description                                                                                                                                                                                                                    | Field Type  | Linked data from | Available in      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- | ---------------- | ----------------- |
| Cancel (X icon) | Reverses / un-posts the transaction. The row is removed from the closed-transaction archive and routed back upstream for correction. Permission-restricted - typically requires a supervisor role and produces an audit entry. | Icon Button | -                | Close Transaction |
| View (eye icon) | Opens a read-only detail view of the full transaction record including the upstream audit trail (Order, Allocation, Commission Adjustment, Post Allocation, Post Transaction). Always available.                               | Icon Button | -                | Close Transaction |

***

## Process EOD (End-of-Day Batch)

**Daily ▸ Process EOD** is the end-of-day batch screen that closes the books for the selected period. It reads the order / transaction records from **Daily ▸ Close Transaction** as input and recomputes position, NAV, fee, and GL data system-wide so that every downstream report (NAV, statements, valuations) reflects the day's activity.

Operationally the user (1) picks the period and portfolio scope, (2) optionally generates missing system transactions with **Auto Generate TX**, then (3) runs **Process EOD** (or the more limited **Process Fee** when only fee re-calculation is needed). Days that have already been closed can be reopened with **Unclose**, and the resulting GL can be exported with **Download GL**.

### Period and Portfolio Group

**Field reference: Process EOD - Period and Portfolio Group**

| Field Name               | Description                                                                                                                                                                               | Field Type             | Linked data from                        | Available in |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------------------------- | ------------ |
| Period (required) - From | Start date of the EOD period to process. EOD will be run for every business day from this date through the end date inclusive.                                                            | Date Picker            | System: SouthBridge (business calendar) | Process EOD  |
| Period (required) - To   | End date of the EOD period to process.                                                                                                                                                    | Date Picker            | System: SouthBridge (business calendar) | Process EOD  |
| Portfolio Group          | Optional pre-filter that loads only the portfolios belonging to the selected portfolio group(s) into the Available list. Selected group(s) are shown as removable chips (e.g., "2025 ×"). | Dropdown Field (multi) | Portfolio Group: @Portfolio Group Code  | Process EOD  |

### Portfolio Selection

A dual-list selector is used to pick which portfolios to run EOD for. The left side is **Available** (filtered by Portfolio Group when set), the right side is **Selected** (the portfolios that will actually be processed).

**Field reference: Process EOD - Portfolio Selection**

| Field Name                               | Description                                                                                                                                                                  | Field Type              | Linked data from                                     | Available in |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------------------------------------- | ------------ |
| Portfolios (required, with info tooltip) | Section label. The (i) tooltip explains how Portfolios interact with Portfolio Group and the From / To validity dates shown next to each portfolio.                          | Section Label           | -                                                    | Process EOD  |
| Show Closed Portfolio                    | When checked, the Available list also includes portfolios whose validity period has ended (closed portfolios). Defaults to off.                                              | Checkbox                | -                                                    | Process EOD  |
| Available (count)                        | Header of the Available list with the count of portfolios it contains and a select-all dropdown (▾) that selects every visible item or applies an advanced selection action. | Section Header + Toggle | Portfolio: @Portfolio Code                           | Process EOD  |
| Available - Search                       | Free-text search restricted to the Available list.                                                                                                                           | Text Input              | -                                                    | Process EOD  |
| Available - Portfolio Row                | Each row in the Available list shows the portfolio code with its validity range ("From: {start}", "To: {end}").                                                              | Checkbox + Label        | Portfolio: @Portfolio Code, @Active From, @Active To | Process EOD  |
| Move Right (>)                           | Moves the checked Available rows into the Selected list.                                                                                                                     | Icon Button             | -                                                    | Process EOD  |
| Move Left (<)                            | Moves the checked Selected rows back into the Available list.                                                                                                                | Icon Button             | -                                                    | Process EOD  |
| Selected (count)                         | Header of the Selected list with the count of portfolios already chosen and a select-all dropdown for the Selected side.                                                     | Section Header + Toggle | -                                                    | Process EOD  |
| Selected - Search                        | Free-text search restricted to the Selected list.                                                                                                                            | Text Input              | -                                                    | Process EOD  |
| Selected - Portfolio Row                 | Each row in the Selected list shows the portfolio code with its validity range.                                                                                              | Checkbox + Label        | Portfolio: @Portfolio Code                           | Process EOD  |

### Action Bar

The action bar sits below the portfolio picker and drives the EOD workflow. Buttons that affect day-state (Close, Unclose) are typically permission-restricted.

**Field reference: Process EOD - Action Bar**

| Field Name       | Description                                                                                                                                                                                                                                                          | Field Type            | Linked data from                                        | Available in |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------------------------- | ------------ |
| Auto Generate TX | Generates any missing system-side transactions for the selected period and portfolios (e.g., accruals, scheduled subscriptions / redemptions) before EOD runs. The adjacent (i) tooltip lists the transaction types it can generate.                                 | Button + Info Tooltip | System: SouthBridge                                     | Process EOD  |
| Download GL      | Exports the General Ledger entries produced by EOD for the selected period and portfolios to a file (typically Excel / CSV) for accounting use.                                                                                                                      | Button                | Calculated                                              | Process EOD  |
| Close            | Marks the selected dates as closed for the selected portfolios after EOD has succeeded. A closed day prevents further changes upstream.                                                                                                                              | Button                | -                                                       | Process EOD  |
| Unclose          | Reverses a previous Close so the selected dates can be edited again. Permission-restricted and produces an audit entry.                                                                                                                                              | Button                | -                                                       | Process EOD  |
| Process Fee      | Re-runs the fee component of EOD only (management fee, performance fee, trustee fee, etc.) without rerunning the full EOD pipeline. The gear icon opens advanced settings (which fees to compute, override rates).                                                   | Button + Gear Icon    | Fee Code, Fee Account Code                              | Process EOD  |
| Process EOD      | Runs the full end-of-day pipeline for the selected period and portfolios - reads Close Transaction, updates positions, applies prices, runs accruals, computes NAV, posts GL. The gear icon opens advanced settings (which steps to include / skip, dry-run toggle). | Button + Gear Icon    | Close Transaction, Price Source, Fee Code, Manage Rules | Process EOD  |

### Current Process Status

A panel that shows live progress while an EOD job is running. When idle it shows the "No data" empty state.

**Field reference: Process EOD - Current Process Status**

| Field Name                     | Description                                                                                                                  | Field Type          | Linked data from | Available in                |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- | ------------------- | ---------------- | --------------------------- |
| Current Process Status (panel) | Section heading for the live-progress panel.                                                                                 | Section Header      | -                | Process EOD                 |
| Empty State                    | Shown when no EOD job is currently running. Displays an icon and the text "No data".                                         | Empty State         | -                | Process EOD                 |
| Progress Indicator             | While an EOD job is running, the panel displays the active sub-step, percentage progress, and a running log of step results. | Progress + Log View | Calculated       | Process EOD (while running) |

### Process Task Status

The history list of every EOD task that has been launched from this screen. It is filterable by outcome and can be expanded per row to see the per-portfolio detail.

**Field reference: Process EOD - Process Task Status**

| Field Name                  | Description                                                                                                    | Field Type       | Linked data from                | Available in |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- | ---------------- | ------------------------------- | ------------ |
| Process Task Status (panel) | Section heading for the historical task list.                                                                  | Section Header   | -                               | Process EOD  |
| Filter Icon                 | Opens the column-level filter pop-over.                                                                        | Icon Button      | -                               | Process EOD  |
| Status Filter: All          | Status pill showing every task regardless of outcome (default).                                                | Filter Pill      | Process Task: @Status           | Process EOD  |
| Status Filter: Error        | Status pill that shows only failed tasks.                                                                      | Filter Pill      | Process Task: @Status = Error   | Process EOD  |
| Status Filter: Success      | Status pill that shows only successful tasks (status "สำเร็จ").                                                | Filter Pill      | Process Task: @Status = Success | Process EOD  |
| Expand / Collapse (− / +)   | Expands a task row to show the per-portfolio breakdown (which portfolio succeeded, which failed, with timing). | Icon Button      | -                               | Process EOD  |
| Type                        | The type of task that was run (e.g., EOD, Fee, Auto Gen TX, Close, Unclose).                                   | Status Tag       | System: SouthBridge             | Process EOD  |
| Status                      | Outcome of the task. Shown as a coloured label - green "สำเร็จ" (Success), red Error, amber Running / Partial. | Status Tag       | Process Task: @Status           | Process EOD  |
| From                        | Start date of the period the task processed.                                                                   | Date             | Process Task: @Period From      | Process EOD  |
| To                          | End date of the period the task processed.                                                                     | Date             | Process Task: @Period To        | Process EOD  |
| Portfolio Qty.              | Count of portfolios included in the task.                                                                      | Read-only Number | Process Task: @Portfolio Count  | Process EOD  |
| Created by                  | The user who launched the task.                                                                                | Read-only Text   | Process Task: @Created By       | Process EOD  |
| Created at                  | Timestamp the task was launched.                                                                               | Read-only Text   | Process Task: @Created At       | Process EOD  |

***

## Unit Allocation (Unit Trust Confirmation, post-EOD)

For **unit-trust / mutual-fund** orders, the actual NAV per unit and the resulting number of units are not known at trade time - they are confirmed by the asset-management company a day or two later via a written confirmation note. The **Dealing ▸ Unit Allocation** screen is where the user enters those confirmed values against the original estimates so that the system's positions and NAV reflect the true broker-confirmed allocation.

Operational order: (1) run **Process EOD** with the estimated values, (2) come to **Unit Allocation**, find each waiting unit-trust transaction, key in the confirmed Allocated Date / NAV / Unit / No. of Unit / Amount, save, then (3) run **Process EOD** again so the system updates positions and NAV with the confirmed figures.

### Unit Allocation Filter Bar

**Field reference: Unit Allocation Filter Bar**

| Field Name        | Description                                                                                                               | Field Type     | Linked data from           | Available in    |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------- | -------------------------- | --------------- |
| Date Range - From | Earliest Trade Date to include in the working list.                                                                       | Date Picker    | System: SouthBridge        | Unit Allocation |
| Date Range - To   | Latest Trade Date to include in the working list.                                                                         | Date Picker    | System: SouthBridge        | Unit Allocation |
| Filters: All      | Status filter dropdown. Pre-built choices include All, Allocated, Unallocated; the user can also pick saved filters here. | Dropdown Field | System: SouthBridge        | Unit Allocation |
| Select Portfolios | Opens a portfolio chooser to narrow the working list to specific portfolios.                                              | Button         | Portfolio: @Portfolio Code | Unit Allocation |

### Bulk Edit Bar

The bulk edit bar appears at the top of the list as soon as any row is in edit mode. It tracks every pending row across pages so that multiple rows can be saved together.

**Field reference: Unit Allocation Bulk Edit Bar**

| Field Name       | Description                                                                                                             | Field Type  | Linked data from | Available in    |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | --------------- |
| Editing n row(s) | Live count of rows currently in edit mode across all pages.                                                             | Status Text | Calculated       | Unit Allocation |
| Save All (n)     | Saves every row in edit mode in one shot. The badge mirrors the Editing count and is disabled when no rows are pending. | Button      | -                | Unit Allocation |
| Cancel All       | Discards every pending edit and returns those rows to view mode.                                                        | Button      | -                | Unit Allocation |

### Unit Allocation Toolbar

**Field reference: Unit Allocation Toolbar**

| Field Name            | Description                                                                                                                                                             | Field Type     | Linked data from                            | Available in    |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ------------------------------------------- | --------------- |
| Unit Allocation Title | Title of the working area with the Last Updated timestamp of the list.                                                                                                  | Section Header | System: SouthBridge                         | Unit Allocation |
| Columns: Default      | Column-set toggle (currently a single "Default" view; reserved for future custom views).                                                                                | Toggle Button  | -                                           | Unit Allocation |
| Filters: Allocated    | Status pill that shows rows whose confirmed allocation has already been keyed in (Status = Allocated). The "+/-" toggle adds / removes the pill from the active filter. | Filter Pill    | Transaction: @Allocation Status = Allocated | Unit Allocation |
| Filters: Unallocated  | Status pill that shows rows still awaiting the broker's confirmation values (Status = Waiting).                                                                         | Filter Pill    | Transaction: @Allocation Status = Waiting   | Unit Allocation |
| Grouping: Portfolio   | Groups rows by Portfolio Code.                                                                                                                                          | Toggle Button  | Portfolio: @Portfolio Code                  | Unit Allocation |
| Grouping: TX Type     | Groups rows by Buy / Sell.                                                                                                                                              | Toggle Button  | Orders: @TX Type                            | Unit Allocation |
| Grouping: Trade Date  | Groups rows by Trade Date.                                                                                                                                              | Toggle Button  | Transaction: @Trade Date                    | Unit Allocation |

### Unit Allocation List - Estimates

The first half of the list (left-hand columns) shows the **estimated** values that were used at trade time. These are read-only references against which the user enters the broker-confirmed values.

**Field reference: Unit Allocation List - Estimates**

| Field Name       | Description                                                                                                                                                                                                                                                                                              | Field Type       | Linked data from                       | Available in    |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------------------- | --------------- |
| Portfolio        | The portfolio that placed the unit-trust order.                                                                                                                                                                                                                                                          | Read-only Text   | Portfolio: @Portfolio Code             | Unit Allocation |
| Security         | The unit trust / fund security code.                                                                                                                                                                                                                                                                     | Read-only Text   | Equity / Cash Security: @Security Code | Unit Allocation |
| TX Type          | The transaction type - Buy (subscription) or Sell (redemption), colour-coded.                                                                                                                                                                                                                            | Status Tag       | System: SouthBridge                    | Unit Allocation |
| Trade Date       | The trade date of the unit-trust order.                                                                                                                                                                                                                                                                  | Date             | Transaction: @Trade Date               | Unit Allocation |
| Tx No.           | The system-assigned transaction number.                                                                                                                                                                                                                                                                  | Read-only Number | Transaction: @TX ID                    | Unit Allocation |
| Est. NAV/Unit    | The estimated NAV per unit used at trade time (the official NAV not yet known).                                                                                                                                                                                                                          | Read-only Number | Transaction: @Estimated NAV per Unit   | Unit Allocation |
| Est. No. of Unit | The estimated number of units derived from Est. NAV/Unit.                                                                                                                                                                                                                                                | Read-only Number | Calculated                             | Unit Allocation |
| Est. Amount      | The estimated subscription / redemption amount in the security currency.                                                                                                                                                                                                                                 | Read-only Number | Transaction: @Estimated Amount         | Unit Allocation |
| Status           | The allocation status of the row. Two states are shown: **Allocated** (green check) when the confirmed values have already been keyed in, **Waiting** (amber clock) when the broker confirmation is still pending. Rows in Waiting status display the confirmed columns to the right as editable inputs. | Status Tag       | Transaction: @Allocation Status        | Unit Allocation |

### Unit Allocation List - Allocated (Confirmed) Values

The right-hand columns hold the **confirmed** values taken from the broker's confirmation note. For rows whose Status is **Waiting**, these cells are editable inputs (the row is highlighted in yellow while it is in edit mode); for rows whose Status is already **Allocated**, the same cells are read-only.

**Field reference: Unit Allocation List - Allocated Values**

| Field Name          | Description                                                                                                                                                                     | Field Type                    | Linked data from        | Available in    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- | ----------------------- | --------------- |
| Allocated Date      | The trade / NAV date confirmed by the broker. Required when the row moves to Allocated.                                                                                         | Date Picker (editable)        | -                       | Unit Allocation |
| NAV/Unit            | The confirmed NAV per unit from the broker's note (full decimal precision, e.g., 9.000000). Required when the row moves to Allocated.                                           | Number Input Field (editable) | -                       | Unit Allocation |
| No. of Unit         | The confirmed number of units allocated for this transaction (full decimal precision, e.g., 47,680.577489). Required when the row moves to Allocated.                           | Number Input Field (editable) | -                       | Unit Allocation |
| Amount              | The confirmed amount in the security currency. Recomputes automatically from NAV/Unit × No. of Unit but can be overridden when the broker's amount differs because of rounding. | Number Input Field (editable) | Calculated, overridable | Unit Allocation |
| Pagination Controls | Standard pagination bar - "n-m of total", page navigation, and page-size dropdown (default 10 / page).                                                                          | Pagination Control            | -                       | Unit Allocation |

### Pending Unit Allocation Sub-panel

A second panel at the bottom of the screen, titled **Pending Unit Allocation**, lists every transaction whose allocation is currently in-progress (i.e., the row is being edited or has been saved against a broker confirmation but not yet picked up by the next EOD). It uses the same column set as the main list and is mainly a working sub-view to track what is still mid-flight.

**Field reference: Pending Unit Allocation Sub-panel**

| Field Name                    | Description                                                                                                          | Field Type       | Linked data from                       | Available in    |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------- | ---------------- | -------------------------------------- | --------------- |
| Pending Unit Allocation Title | Section heading for the sub-panel.                                                                                   | Section Header   | -                                      | Unit Allocation |
| Columns: Default              | Column-set toggle for the sub-panel (Default view).                                                                  | Toggle Button    | -                                      | Unit Allocation |
| Grouping                      | Grouping toggles for the sub-panel (same options as the main list).                                                  | Toggle Buttons   | System: SouthBridge                    | Unit Allocation |
| Select (Checkbox)             | Row checkbox for the sub-panel.                                                                                      | Checkbox         | -                                      | Unit Allocation |
| Tx (bulb icon)                | Indicator that the transaction has a pending in-progress action (the bulb icon highlights rows that need attention). | Icon Indicator   | Transaction: @Allocation Status        | Unit Allocation |
| Portfolio                     | The portfolio of the pending allocation row.                                                                         | Read-only Text   | Portfolio: @Portfolio Code             | Unit Allocation |
| Security                      | The unit trust / fund security code.                                                                                 | Read-only Text   | Equity / Cash Security: @Security Code | Unit Allocation |
| TX Type                       | Buy / Sell flag for the row.                                                                                         | Status Tag       | Orders: @TX Type                       | Unit Allocation |
| Trade Date                    | Trade date of the order.                                                                                             | Date             | Transaction: @Trade Date               | Unit Allocation |
| Tx No.                        | System-assigned transaction number.                                                                                  | Read-only Number | Transaction: @TX ID                    | Unit Allocation |
| Est. NAV/Unit                 | Estimated NAV/Unit used at trade time.                                                                               | Read-only Number | Transaction: @Estimated NAV per Unit   | Unit Allocation |
| Est. No. of Unit              | Estimated number of units.                                                                                           | Read-only Number | Calculated                             | Unit Allocation |
| Est. Amount                   | Estimated amount.                                                                                                    | Read-only Number | Transaction: @Estimated Amount         | Unit Allocation |
| Allocated Date                | The allocated date that has been keyed in for the pending row.                                                       | Date             | Transaction: @Allocated Date           | Unit Allocation |
| NAV/Unit                      | The confirmed NAV/Unit that has been keyed in.                                                                       | Read-only Number | Transaction: @NAV per Unit             | Unit Allocation |
| No. of Unit                   | The confirmed number of units that has been keyed in.                                                                | Read-only Number | Transaction: @No. of Unit              | Unit Allocation |
| Amount                        | The confirmed amount that has been keyed in.                                                                         | Read-only Number | Transaction: @Confirmed Amount         | Unit Allocation |

### Re-run EOD After Unit Allocation

Once every Waiting row for the period has been moved to Allocated (i.e., the broker-confirmation values have been keyed in and saved), the user must return to **Daily ▸ Process EOD** and run EOD again for the same period and portfolios. The re-run picks up the confirmed values from Unit Allocation, replaces the previous estimated position / NAV figures, and produces an updated GL. Without this second EOD run, downstream reports (NAV, statements, valuations) will continue to reflect the estimated, not the confirmed, allocation.

