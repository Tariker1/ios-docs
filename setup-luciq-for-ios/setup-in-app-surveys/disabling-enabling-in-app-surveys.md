---
description: >-
  This page details the API for disabling and enabling in-app surveys for your
  iOS apps.
---

# Disabling/Enabling In-App Surveys

You can completely disable any surveys from being shown to your app users with the following API. Please note that this also disables manually shown surveys, as this method disables any request related to surveys.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Surveys.enabled = false;
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[LCQSurveys setEnabled:YES];
```
{% endcode %}
{% endtab %}
{% endtabs %}
