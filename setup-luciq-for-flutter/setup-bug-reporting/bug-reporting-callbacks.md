---
description: >-
  Covered here are callbacks that you can use to have a block of code executed
  when a certain action is triggered for your Flutter apps.
---

# Bug Reporting Callbacks

### Before Invoking Luciq

This block is executed on the UI thread. You can use it to perform any UI changes before the SDK's UI is shown.

{% code title="Dart" %}
```dart
BugReporting.setOnInvokeCallback(Function function);
```
{% endcode %}

{% hint style="info" %}
The callback is invoked on the UI thread, so it's appropriate for UI updates.
{% endhint %}

### After Dismissing Luciq

This block is executed on the UI thread. You can use it to perform any UI changes after the SDK's UI has been dismissed.

{% code title="Dart" %}
```dart
BugReporting.setOnDismissCallback(Function function);
```
{% endcode %}

{% hint style="info" %}
The callback is invoked on the UI thread, so it's appropriate for UI updates.
{% endhint %}
