---
description: >-
  This page details the API for disabling and enabling crash reporting for your
  Flutter apps.
---

# Disabling/Enabling Crash Reporting

Luciq Crash Reporting can be disabled with the following method. This will completely prevent any crash report from being sent to your dashboard.

{% code title="Dart" %}
```dart
CrashReporting.setEnabled(false);
```
{% endcode %}
