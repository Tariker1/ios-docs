---
description: >-
  This page explains the different tools to debug your APM iOS integration,
  bypass the 6-hour batching, and change the SDK log level for your iOS apps.
---

# SDK Debugging

### Debug Mode

In case you would like to view your data on the dashboard without having to wait for the SDK's default 6-hour batching period, you can simply bypass this by **running the app while attached to the debugger**.

Attaching the app to the debugger will sync the data captured by our SDK upon **closing a session and starting a new one**. This can be especially helpful if you are debugging an integration issue or simply trying out APM for the first time.

{% hint style="info" %}
Please note that rate limiting will apply if the number of sessions exceeds 50 per hour. Once this limit is reached, you will have to wait until a full hour has elapsed in order to be able to keep using Debug Mode. Data collected during this period will not show up on your Dashboard.
{% endhint %}

***

### Logging

APM SDK provides useful console logs in Xcode for you to be able to have visibility on significant events that might be of interest to you. Since not all events are equal in terms of importance or relevance, you can control the level of verbosity of those logs via the following API:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.sdkDebugLogsLevel = SDKLogLevel.Debug
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
Luciq.sdkDebugLogsLevel = LCQLogLevelDebug;
```
{% endcode %}
{% endtab %}
{% endtabs %}

The available levels are:

* **`None`:** disables all APM SDK console logs.
* **`Error`:** prints errors only, we use this level to let you know if something goes wrong.
* **`Warning`:** displays warnings that will not necessarily lead to errors but should be addressed nonetheless.
* **`Info`:** this is the default level and it logs information that we think is useful without being too verbose.
* **`Debug`:** use this in case you are debugging an issue. Not recommended for production use.
* **`Verbose`:** use this only if `Debug` was not enough and you need more visibility on what is going on under the hood. Similar to the `Debug` level, this is not meant to be used on production environments.

{% hint style="info" %}
Please note that each level displays the logs corresponding to its own level as well as all the levels above it. This means that `Info` also includes `Warning` and `Error` logs and so on.
{% endhint %}
