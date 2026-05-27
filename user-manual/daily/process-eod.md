---
description: >-
  Process EOD runs the End-of-Day routine. It locks every transaction, refreshes
  valuations, applies fees and updates portfolios so that the next business day
  starts from a clean state.
icon: spinner-scale
---

# Process EOD

### Process EOD

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (328).png" alt=""><figcaption></figcaption></figure></div>

| **Component**          | **Description (English)**                                         | **คำอธิบาย (ภาษาไทย)**                               |
| ---------------------- | ----------------------------------------------------------------- | ---------------------------------------------------- |
| Period                 | Select the date range for the EOD process.                        | เลือกช่วงวันที่ที่ต้องการประมวลผลสิ้นวัน             |
| Portfolio Group        | Filter and select portfolios by their designated group.           | เลือกกลุ่มของพอร์ตโฟลิโอที่ต้องการประมวลผล           |
| Available Portfolios   | List of portfolios ready to be processed.                         | รายชื่อพอร์ตโฟลิโอที่ระบบพร้อมนำเข้าสู่กระบวนการ     |
| Selected Portfolios    | Portfolios that have been chosen for the current EOD run.         | รายชื่อพอร์ตโฟลิโอที่ถูกเลือกเพื่อประมวลผลในรอบนี้   |
| Auto Generate TX       | Automatically creates recurring or pending transactions.          | ปุ่มสำหรับสั่งสร้างรายการธุรกรรมอัตโนมัติที่ค้างอยู่ |
| Download GL            | Export General Ledger entries for the processed period.           | ปุ่มสำหรับดาวน์โหลดบันทึกบัญชีแยกประเภท (GL)         |
| Close / Unclose        | Lock or unlock the accounting period for the selected portfolios. | ปุ่มสำหรับปิด (Lock) หรือเปิดงวดบัญชีของพอร์ตนั้น ๆ  |
| Process Fee            | Calculate and accrue management or performance fees.              | ปุ่มสำหรับสั่งประมวลผลการคำนวณค่าธรรมเนียม           |
| Process EOD Button     | Execute the final daily valuation and accounting updates.         | ปุ่มหลักสำหรับเริ่มการประมวลผลมูลค่าสิ้นวันและปิดยอด |
| Current Process Status | Real-time monitoring of the ongoing EOD task.                     | พื้นที่แสดงสถานะการทำงานปัจจุบันของการประมวลผล       |
| Process Task Status    | Historical logs of completed, failed, or pending EOD runs.        | ตารางสรุปประวัติและสถานะการประมวลผลที่ผ่านมา         |

{% hint style="info" %}
_The EOD process must be run every business day so that data, valuations and fees stay in sync._
{% endhint %}
