---
description: Report Automation Tool
icon: cabinet-filing
---

# mket-cli Guide

## mket-cli (Report Automation Tool: Option)

mket-cli is a specialized Command Line Interface tool designed to automate the generation of the `MKET_PF_SUMMARY_T1` report. It serves as a bridge to deliver reports directly to client network shares, ensuring seamless data flow even in isolated network environments.



{% tabs %}
{% tab title="TH" %}
<table data-view="cards"><thead><tr><th></th><th data-type="content-ref"></th></tr></thead><tbody><tr><td>mket-cli Guide (TH)</td><td><a href="mket-cli-guide-th.md">mket-cli-guide-th.md</a></td></tr></tbody></table>

เครื่องมืออัตโนมัติแบบ One-shot สำหรับสร้างและนำส่งไฟล์รายงานตามมาตรฐาน

โดยระบบจะคำนวณวันรันงานอัตโนมัติจากวันทำการหลังสิ้นเดือน และจัดการเขียนไฟล์ลงใน Network Share ของลูกค้าโดยตรง เพื่อแก้ปัญหาข้อจำกัดด้านความปลอดภัยของเครือข่าย
{% endtab %}

{% tab title="ENG" %}
<table data-view="cards"><thead><tr><th></th><th data-type="content-ref"></th></tr></thead><tbody><tr><td>mket cli Guide (ENG)</td><td><a href="mket-cli-guide-eng.md">mket-cli-guide-eng.md</a></td></tr></tbody></table>

A one-shot execution tool that automates report generation according to specifications.&#x20;

It calculates trigger dates based on end-of-month business days and handles secure data transmission from the Level11 server to local destinations (e.g., Windows Network Shares).
{% endtab %}
{% endtabs %}



