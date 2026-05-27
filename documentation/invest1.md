---
hidden: true
---

# Invest1

This page documents the **Investment ▸ Invest ▸ Edit Investment** screen of the SouthBridge / Level11 system. Each tab and section is described with its field definitions in the same format used in the Menu Set up reference.

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
