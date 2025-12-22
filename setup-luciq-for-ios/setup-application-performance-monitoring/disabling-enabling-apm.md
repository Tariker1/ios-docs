---
description: >-
  This page explains the API to disable and enable App Performance Monitoring on
  iOS.
---

# Disabling/Enabling APM

You can disable APM by calling the following API right after initializing the SDK. This completely prevents the SDK from collecting any performance data or executing any APM related logic:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
APM.enabled = true
APM.enabled = false
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
LCQAPM.enabled = YES;
LCQAPM.enabled = NO;
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Please note that disabling APM will also clear any data that has already been collected and stored on your users' devices but hasn't been synced to our servers yet.
{% endhint %}
