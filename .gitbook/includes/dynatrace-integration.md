---
title: dynatrace-integration
---

## Overview

The new Luciq integration with Dynatrace enables end-to-end tracing for network calls, connecting client-side and server-side monitoring for your network requests. By using a unique trace ID, you can follow any network request from the client to the server, providing insights for troubleshooting networking issues.

![](<../assets/5821e14a48410ec2d887c63cb9fcdce50f0ffe90252e2fc6669869e8f404df71 image.png>)

## Prerequistes

### Dynatrace

To use this integration, ensure the following prerequisites are met in your Dynatrace setup:

* **Supporting for W3C Context Propagation**: Have W3C enabled. W3C Trace Context support is available as an Early Adopter Release (no registration required) beginning with Dynatrace version 1.180.
  * You can enable this on Dynatrace through Settings > Server-side service monitoring > Deep monitoring > Distributed tracing.

### Luciq

* **Supported Platforms**: This integration is only supported for iOS and Android.
* **Luciq SDK Version**: Ensure you have a minimum SDK v13.2.0 or higher on either iOS or Android.

# Integration Steps

{% hint style="info" %}
By setting up this integration, Luciq will attach a trace ID as an HTTP header to your network requests. This allows us to link network requests from Luciq to New Relic.
{% endhint %}

Go to **Settings -> Integrations -> Dynatrace** in your Luciq dashboard, and follow these integration steps:

{% stepper %}
{% step %}
### Set Up

* Enter your Dynatrace dashboard link.
  * If you’re using Dynatrace SaaS, replace x in `x.apps.dynatrace.com` with your environment ID.
  * If you're using Dynatrace Managed (on-premises), replace x in `x.apps.dynatrace.com` with your Dynatrace domain.

![](<../assets/de58981defda650154b799aa82dc0aac0c88144205b7c14ed18ab67ecd5c7643 image.png>)
{% endstep %}

{% step %}
### Test

* Validate the Dynatrace dashboard link to ensure it is correct.

![](<../assets/40b336e9b446f689b4cdf1bcde89954347d404aa272c195ee646f108c79d63e5 image.png>)
{% endstep %}

{% step %}
### Finish

* Ensure the **APM - Network Requests** checkbox is checked to trace network requests to Dynatrace.
* Give your integration a name and save the integration.

![](<../assets/22b87f4bf231dff34b71f1f00024e9352cff2df87163bdda5bbf78169f9bb7d8 image 20250307 104435.png>)
{% endstep %}
{% endstepper %}

## Using the Integration

When a network occurrence is logged, a unique trace ID will appear on the occurrence page in the Luciq dashboard.

Navigate to any network occurrence received after you created the integration, click on “View on Dynatrace” to view the same network occurrence on your Dynatrace dashboard.

<figure><img src="../assets/image (52).png" alt=""><figcaption></figcaption></figure>
