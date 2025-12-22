# Setup Session Replay

If you're already using Luciq, but [Session Replay](https://www.luciq.ai/product/session-replay) isn't included in your current plan, please reach out to us at [contactus@luciq.ai.](mailto:contactus@luciq.ai.) We would love to enable a custom trial for you and help you set it up.

{% hint style="warning" %}
#### Min Required SDK Version

Session Replay is supported starting React Native SDK version 12.1.0.
{% endhint %}

**Session Replay Footprint**

We're taking several measures to make sure Luciq Session Replay is resource-friendly. To minimize its impact on the device's battery and data consumption:

* The SDK collects your performance data and sends it in batches, at most, once every 6 hours.
* The SDK doesn't perform any network operations while the app is in the background.
  * This means data collected is sent to the server at the beginning of a session if the last server communication took place more than 6 hours ago.

{% hint style="info" %}
#### Data Retention

Data retention period changes from plan to plan and can be checked [here](https://www.luciq.ai/pricing). This is customizable on the [Enterprise plan](https://docs.luciq.ai/docs/enterprise-plan).
{% endhint %}

## Enabling/Disabling Session Replay

Luciq's Session Replay can be disabled with the following method. This will completely prevent any session replay data from being sent to your dashboard. By default, Session Replay is enabled if it is available in your current [plan](https://www.luciq.ai/pricing).

{% tabs %}
{% tab title="Dart" %}
```dart
SessionReplay.setEnabled(true); // Enabled
SessionReplay.setEnabled(false); // Disabled
```
{% endtab %}
{% endtabs %}

## Logs

All logs are enabled by default, but can be manually disabled/enabled using the below APIs. More details about each log type can be found [here](https://docs.luciq.ai/docs/flutter-logging).

### Network

{% tabs %}
{% tab title="Dart" %}
```dart
SessionReplay.setNetworkLogsEnabled(true); // Enabled
SessionReplay.setNetworkLogsEnabled(false); // Disabled
```
{% endtab %}
{% endtabs %}

### Luciq Logs

{% tabs %}
{% tab title="Dart" %}
```dart
SessionReplay.setLuciqLogsEnabled(true); // Enabled
SessionReplay.setLuciqLogsEnabled(false); // Disabled
```
{% endtab %}
{% endtabs %}

### User Steps

{% tabs %}
{% tab title="Dart" %}
```dart
SessionReplay.setUserStepsEnabled(true); // Enabled
SessionReplay.setUserStepsEnabled(false); // Disabled
```
{% endtab %}
{% endtabs %}

### Screenshots

{% tabs %}
{% tab title="Dart" %}
```dart
Luciq.setReproStepsConfig(sessionReplay: ReproStepsMode.enabled);
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
#### Notes on Screenshots

* Adjusting the `setReproStepsConfig` method's `sessionReplay` parameter could affect previous configurations and unspecified parameters will revert back to the default values. For more information, please check the example [here](https://docs.luciq.ai/docs/flutter-repro-steps#examples-1).
{% endhint %}

### Limits

* Each session contains up to 2MB of compressed logs and 2MB of compressed screenshots.
* Luciq saves sessions up to 50MB worth of data. (for multiple sessions)
* Data is sent through requests with a maximum of 1MB per request.

## Privacy options

#### Private Views

Set certain screens as private, and they will automatically appear with a black overlay covering any screenshot. You can find more details about private views [here](https://docs.luciq.ai/docs/flutter-repro-steps#private-views).

#### Network Logs Masking

To obfuscate parts of a network request prior to sending it to the dashboard, you can follow the below steps found [here](https://docs.luciq.ai/docs/flutter-logging#obfuscating-data).
