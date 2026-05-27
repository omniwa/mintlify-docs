---
icon: file-lines
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

# Reporting on Non-Trading Days

### **Report Generation with Available Market Price**

When generating a report for a standard trading day, the system retrieves and applies the exact closing price corresponding to that specific date. This ensures that the Portfolio Holding Report reflects the real-time market value and accurate unrealized gain/loss based on actual exchange data.



### **Report Generation for Missing Market Prices (Non-Trading Days)**

In the event that a report is requested for a date where no market price is recorded (such as weekends or public holidays), the system is designed to maintain valuation continuity by using the Last Available Price.

* Logic: The system automatically looks back to find the most recent closing price before the selected date.
* User Impact: The report will display the valuation based on this historical "latest" price without a specific notification of the original price date.
* Result: This allows for a complete calculation of the Net Asset Value (NAV) and Portfolio Holding even when the market is closed.



{% hint style="info" %}
If you generate a report for a date that does not have an active market price, the system will apply the latest available closing price from the database. This ensures your portfolio valuation remains complete, even when current market data is not present for that specific day.
{% endhint %}

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure></div>
