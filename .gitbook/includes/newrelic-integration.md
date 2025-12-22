---
title: newrelic-integration
---

## Overview

The new Luciq integration with New Relic enables end-to-end tracing for network calls, connecting client-side and server-side monitoring for your network requests. By using a unique trace ID, you can follow any network request from the client to the server, providing insights for troubleshooting networking issues.

![](<../assets/4f9062660bfc8b21382a5b124d04e5eb1f842dfc79bc4698f3a7483976c0132b new relic 2.png>)

## Prerequistes

### New Relic

To use this integration, ensure the following prerequisites are met in your New Relic setup:

* **Distributed Tracing in Your Plan**: Ensure that your New Relic plan includes distributed tracing.
* **New Agent Supporting W3C Context Propagation**: You need to use a New Relic agent that supports W3C context propagation. More details can be found [here](https://newrelic.com/blog/nerdlog/w3c-trace-context-distributed-tracing-standard).
* **Enable Distributed Tracing in Backend Agent**: Distributed tracing must be enabled in your backend agent. More information is available [here](https://docs.newrelic.com/docs/distributed-tracing/concepts/quick-start/).

{% hint style="info" %}
Note: if you use any trace sampling algorithms, New Relic may drop some traces. Consequently, you might see network requests in Luciq that are not available in New Relic.
{% endhint %}

### Luciq

* **Supported Platforms**: This integration is only supported for iOS and Android.
* **Luciq SDK Version**: Ensure you have a minimum SDK v13.2.0 or higher on either iOS or Android.

## Integration Steps

{% hint style="info" %}
By setting up this integration, Luciq will attach a trace ID as an HTTP header to your network requests. This allows us to link network requests from Luciq to New Relic.
{% endhint %}

Go to **Settings** -> **Integrations** -> **New Relic** in your Luciq dashboard, and follow these integration steps:

{% stepper %}
{% step %}
## Set Up

Enter your New Relic dashboard link. If you use custom domains for New Relic, replace `one.newrelic.com` with your company domain (e.g., `x.newrelic.com`). For redirecting to multiple organizations from the same app, use `one.newrelic.com`.

![](<../assets/95065454842ee89fddf9e90db9cb9fabfcb05f0b813e97bf186a567918c829c2 image.png>)
{% endstep %}

{% step %}
## Test

Validate the New Relic dashboard link to ensure it is correct.

![](<../assets/43762d9f9abc2e7b1e4adf694194daf5922efb5f4fee4ad0557913941f4d2084 image.png>)
{% endstep %}

{% step %}
## Finish

Ensure the APM - Network Requests checkbox is checked to trace network requests to New Relic, then give your integration a name and save the integration.

![](<../assets/de0bc60 image.png>)
{% endstep %}
{% endstepper %}

## Using the integration

When a network occurrence is logged, a unique trace ID will appear on the occurrence page in the Luciq dashboard.

{% stepper %}
{% step %}
## Copy the Trace ID

Navigate to any network occurrence and **copy the Trace ID**.

![](<../assets/3ccd7089298aecf628abb2d40525fba781a82dd95591b20437168090342bca29 image.png>)
{% endstep %}

{% step %}
## View on New Relic

Click on "**View on New Relic**" to go to the traces page in New Relic.

![](<../assets/998a854 image.png>)
{% endstep %}

{% step %}
## Filter by Trace ID

**Paste the Trace ID into the filter** in New Relic (traceid = xxxxx) to view the same trace.

<figure><img src="../assets/image (54).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
