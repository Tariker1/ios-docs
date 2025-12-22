---
title: APM Overview
---

## Try out Luciq APM

If you are already using Luciq, but [Luciq App Performance Monitoring](https://www.luciq.ai/product/app-performance-monitoring) isn't included in your current plan, please reach out to us at [contactus@luciq.ai](mailto:contactus@luciq.ai). We would love to enable a custom trial for you and help you set it up.

{% hint style="info" %}
### Min Required SDK Version

APM is supported starting iOS SDK version 10.0.0.
{% endhint %}

## Supported Metrics

* [**App Launch**](../../product-guides/application-performance-monitoring/app-launch.md)
* [**Network**](../../product-guides/application-performance-monitoring/network.md)
* [**UI Hangs**](../../product-guides/application-performance-monitoring/ui-hangs.md)
* [**Flows**](../../product-guides/application-performance-monitoring/flows/)
* [**Screen Loading**](../../product-guides/application-performance-monitoring/screen-loading/)

## APM Footprint

We're taking several measures to make sure Luciq APM is resource-friendly. To minimize its impact on the device's battery and data consumption:

* The SDK collects your performance data and sends it in batches, at most, once every **6 hours**.
* The SDK doesn't perform any network operations while the app is in the background.
* This means, data collected by APM is sent to the server at the beginning of a session if the last server communication took place more than 6 hours ago.

The default 6-hour interval can be bypassed by enabling **Debug Mode** which you can use to visualize your data with almost no delay; this can be very useful in case you're still evaluating our SDK as well as help debug issues with your integration.

## Why APM?

In the field, your app goes through a wide range of different user scenarios, cellular networks, signal conditions, device types, as well as locations. This is when unexpected performance issues happen.

[Luciq App Performance Monitoring](https://www.luciq.ai/product/app-performance-monitoring) (APM) is built to provide you with insights about how your app is performing on your end-users' devices and hence shaping their experience.
