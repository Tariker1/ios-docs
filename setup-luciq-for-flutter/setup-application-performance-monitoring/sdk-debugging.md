---
description: >-
  This page explains the different tools to debug your APM Flutter integration,
  bypass the 6-hour batching, and change the SDK log level for your Flutter
  apps.
---

# SDK Debugging

### Debug Mode

In case you would like to view your data on the dashboard without having to wait for the SDK's default 6-hour batching period, you can do so by enabling Debug Mode. Once enabled, data captured by our SDK will be synced upon **closing a session and starting a new one**. This can be especially helpful if you are debugging an integration issue or simply trying out APM for the first time.

**iOS**

Debug Mode is enabled by default for iOS if you’re running the app via Xcode (i.e. the debugger is attached).

**Android**

Debug Mode can be enabled on Android by running the following command via terminal:

{% code title="Shell" %}
```bash
adb shell setprop debug.luciq.apm.app YOUR_APP_PACKAGE_NAME
```
{% endcode %}

If you would like to disable Debug Mode on Android, simply run the following command:

{% code title="Shell" %}
```bash
adb shell setprop debug.luciq.apm.app none
```
{% endcode %}

{% hint style="warning" %}
Please note that rate limiting will apply if the number of sessions exceeds 50 per hour. Once this limit is reached, you will have to wait until a full hour has elapsed in order to be able to keep using Debug Mode. Data collected during this period will not show up on your Dashboard.
{% endhint %}

***

### Logging

APM SDK provides useful console logs in Xcode for you to be able to have visibility on significant events that might be of interest to you. Since not all events are equal in terms of importance or relevance, you can control the level of verbosity of those logs via the following API:

{% code title="Dart" %}
```dart
Luciq.init(
  // ...
  debugLogsLevel: LogLevel.debug,
);
```
{% endcode %}

The available levels are:

* **`none`:** disables all APM SDK console logs.
* **`error`:** prints errors only; we use this level to let you know if something goes wrong.
* **`warning`:** displays warnings that will not necessarily lead to errors but should be addressed nonetheless.
* **`info`:** this is the default level and it logs information that we think is useful without being too verbose.
* **`debug`:** use this in case you are debugging an issue. Not recommended for production use.
* **`verbose`:** use this only if `debug` was not enough and you need more visibility on what is going on under the hood. Similar to the `debug` level, this is not meant to be used on production environments.

{% hint style="info" %}
Please note that each level displays the logs corresponding to its own level as well as all the levels above it. This means that `info` also includes `warning` and `error` logs, and so on.
{% endhint %}
