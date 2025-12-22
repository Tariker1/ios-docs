---
description: >-
  This section covers how Luciq automatically attaches console logs, verbose
  logs, and all steps made by your users before a bug report is sent for Flutter
  apps.
---

# Report Logs

{% hint style="warning" %}
It is highly recommended to mention in your privacy policy that you may be collecting logging data in order to assist troubleshooting bugs.
{% endhint %}

A variety of log types are sent with each crash or bug report. They appear within each report in your Luciq dashboard. Log collection stops when Luciq is shown.

We support the following types of logs:

* [Network Logs](report-logs.md#network-logs)
* [Luciq Logs](report-logs.md#luciq-logs)
* [Console Logs](report-logs.md#console-logs)
* [User Events](report-logs.md#user-events)

### Network Logs

Luciq automatically logs all network requests performed by your app from the start of the session. Request details, along with their responses, are sent with each report. Luciq will also show you an alert at the top of the bug report in your dashboard when network requests have timed out or taken too long to complete. Note that the maximum number of network logs sent with each report is 1,000.

You can choose to attach all your network requests to the reports being sent to the dashboard. To enable the feature when using the `dart:io` package `HttpClient`, please refer to the [Luciq Dart IO Http Client](https://github.com/instabug/instabug-dart-io-http-client) repository.

We also support the packages `http` and `dio`. For details on how to enable network logging for these external packages, refer to the [Luciq Dart Http Adapter](https://github.com/instabug/instabug-Dart-http-Adapter) and the [Luciq Dio Interceptor](https://github.com/instabug/instabug-Dio-Interceptor) repositories.

#### Omitting Requests

You can omit requests from being logged based on either their request or response details. `NetworkLogger.omitLog` allows you to specify a predicate to be evaluated against every request and response to determine if the request should be included in the logs or not.

{% code title="Dart" %}
```dart
NetworkLogger.omitLog((data) =>
  // you can also use other parts of data for filtering (e.g.: responseBody, requestBody)
  data.url.contains('/payment')
);
```
{% endcode %}

The code above excludes all requests made to any URL containing `/payment`. You can also use other parts of `data` for filtering (e.g., `responseBody`, `requestBody`).

#### Obfuscating Data

**Requests**

You can obfuscate sensitive user data in requests, like authentication tokens for example, without filtering out the whole request.

{% code title="Dart" %}
```dart
NetworkLogger.obfuscateLog((data) {
  data.requestHeaders.remove('Authorization');
  return data;
});
```
{% endcode %}

**Responses**

As with requests, the response object, as well as the response data, can be modified for obfuscation purposes before they are logged.

{% code title="Dart" %}
```dart
NetworkLogger.obfuscateLog((data) {
  data.responseBody = '';
  return data;
});
```
{% endcode %}

### Luciq Logs

You can log messages throughout your application's lifecycle to be sent with each report. Note that the maximum number of Luciq logs sent with each report is 1,000.

{% code title="Dart" %}
```dart
LuciqLog.logVerbose("Message to log");
LuciqLog.logInfo("Message to log");
LuciqLog.logDebug("Message to log");
LuciqLog.logError("Message to log");
LuciqLog.logWarn("Message to log");
```
{% endcode %}

### Console Logs

Luciq captures all console logs and displays them on your dashboard with each report. Note that the maximum number of console logs sent with each report is 1,000 statements with a limit of 5,000 characters for each statement.

### User Events

{% hint style="info" %}
Currently the limit of the number of user events sent with each report is 1,000. If you're planning on logging a large amount of unique data, the best practice here would be to use [Luciq Logging](https://docs.luciq.ai/docs/flutter-logging#section-luciq-logs) instead. The reason for this is that having a very large amount of user events will negatively impact the performance of the dashboard.

Having a large amount of user events will not affect dashboard performance if the user events are not unique.
{% endhint %}

You can log custom user events throughout your application and they will automatically be included with each report. Note that the maximum number of user events sent with each report is 1,000.

{% code title="Dart" %}
```dart
Luciq.logUserEventWithName("OnFeedbackButtonClicked");
```
{% endcode %}
