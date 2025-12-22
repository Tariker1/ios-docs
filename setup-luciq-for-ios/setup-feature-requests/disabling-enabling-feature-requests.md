---
description: >-
  Described here is how to disable or enable the feature requests for your iOS
  apps.
---

# Disabling/Enabling Feature Requests

You can completely prevent any feature request related features from displaying by disabling it using the API below.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
//Enable
FeatureRequests.enabled = true

//Disable
FeatureRequests.enabled = false
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
//Enable
LCQFeatureRequests.enabled = YES;

//Disable
LCQFeatureRequests.enabled = NO;
```
{% endcode %}
{% endtab %}
{% endtabs %}
