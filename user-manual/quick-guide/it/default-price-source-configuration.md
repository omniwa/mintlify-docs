---
description: >-
  This section provides a step-by-step guide on how to configure the default
  system-wide Price Source ID.
icon: arrow-turn-down-right
---

# Default Price Source Configuration —

This setting ensures that the system automatically generates the correct price codes once an equity instrument has been approved.

***

### Step 1: Locate the Target Price Source ID

Before updating the configuration, you need to retrieve the specific Price Source ID from the Market module:

{% stepper %}
{% step %}
#### Navigate to **Market** ▸ **Price Source**

Browse the registry table to find your preferred price source provider.
{% endstep %}

{% step %}
#### Click <a class="button secondary" data-icon="eye"></a> to view to **Price Source details.**
{% endstep %}

{% step %}
#### **Note down the Price Source ID displayed in the details panel.**

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (370).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

***

### Step 2: Update the Application Configuration

Once you have the ID, map it into the system's global environment settings:

{% stepper %}
{% step %}
#### Navigate to **System Management** ▸ **App Configuration**.
{% endstep %}

{% step %}
Scroll down or use the search bar to locate the configuration parameter row titled: `DEFAULT_PRICESOURCE_ID`.
{% endstep %}

{% step %}
#### In the value input field for `DEFAULT_PRICESOURCE_ID`, enter the Price Source ID you retrieved in Step 1.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (371).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### **Click the** <a class="button secondary">Save</a> **to apply and deploy the changes system.**
{% endstep %}
{% endstepper %}

### System Effect: Market ▸ Price Code

When a user registers and approves a new asset under the equity workflow, the application's core data engine executes an automated setup routine driven by the global configuration settings:

```
[ New Equity Approved ]
│
▼
Reads: DEFAULT_PRICESOURCE_ID
│
▼
Automatically Generates ──► New Entry in [ Market ▸ Price Code ]
```

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (372).png" alt=""><figcaption></figcaption></figure></div>



***

> 📘 **Technical Concept & Automation Logic:**
>
> * **Automatic Price Code Generation:** The `DEFAULT_PRICESOURCE_ID` parameter dictates which data vendor or pricing feed logic the system will default to.
> * **Trigger Event:** As soon as an equity instrument's workflow status transitions to **Approved** (after proving equity), the background engine reads this ID to automatically initialize and create the corresponding asset price codes, eliminating manual setup errors.
