---
description: >-
  This section provides a step-by-step guide on how to upload an authorized
  signature picture to a user profile and configure it as the primary signer for
  system-generated report instructions.
icon: arrow-turn-down-right
---

# Signature Setup & Report Signer Configuration —

***

### Phase 1: Uploading the User Signature Picture

To attach a physical signature to a specific user account, follow these steps:

{% stepper %}
{% step %}
#### Navigate to **System Management** ▸ **User Management**
{% endstep %}

{% step %}
#### **Click the Edit button (pencil icon) on the** specific **user row.**

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (362).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### Upload your target signature image file (Supported formats: .png, .jpg).

<div><figure><img src="../../.gitbook/assets/image (364).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (365).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### **Click the** <a class="button secondary">Submit</a> **to apply the changes to the user account.**
{% endstep %}
{% endstepper %}

***

### Phase 2: Assigning the Authorized Report Signer

Once the signature is uploaded, you must instruct the system to pull this signature onto official report documents by mapping it in the app configurations:

{% stepper %}
{% step %}
#### Navigate to **System Management** ▸ **App Configuration**.

Scroll down or search for the configuration parameter row titled: `REPORT_INSTRUCTION_SIGNER`.
{% endstep %}

{% step %}
#### **Enter the exact Username of the account you modified in Phase 1.**

In the value input field for `REPORT_INSTRUCTION_SIGNER`, added with usernames, comma-separated and space-insensitive.

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (366).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### **Click the** <a class="button secondary">Save</a> **to deploy the changes system.**
{% endstep %}
{% endstepper %}



#### Example

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (369).png" alt=""><figcaption></figcaption></figure></div>

***

> 📘 **Important Operational Notes:**
>
> * **Image Resolution & Quality:** To ensure the generated PDF reports maintain a professional look, ensure the uploaded signature picture has high resolution and a transparent or plain white background.
> * **Strict Matching:** The value entered in `REPORT_INSTRUCTION_SIGNER` is case-sensitive and must perfectly match the internal system **Username** (not the display full name) of the target account. If mismatched, the report layout might fail to fetch or render the signature graphic.



