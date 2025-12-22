---
description: >-
  This page explains the API to disable and enable App Performance Monitoring
  (APM) on Flutter.
---

# Disabling/Enabling APM

You can disable APM by calling the following API right after initializing the SDK. This completely prevents the SDK from collecting any performance data or executing any APM related logic.

{% code title="Dart" %}
```dart
// Enable APM
APM.setEnabled(true);

// Disable APM
APM.setEnabled(false);
```
{% endcode %}

{% hint style="info" %}
Please note that disabling APM will also clear any data that has already been collected and stored on your users' devices but hasn't been synced to our servers yet.
{% endhint %}
