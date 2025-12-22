---
description: >-
  Described here is how to invoke the list of feature requests inside your iOS
  app.
---

# Showing feature requests list

The following method can be used to display the Feature Requests page to your users. Once you display the page, your users can submit new feature requests, add comments, and up-vote other feature requests.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
FeatureRequests.show()
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[LCQFeatureRequests show];
```
{% endcode %}
{% endtab %}
{% endtabs %}

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p><em>This is what the list of in-app feature requests looks like.</em></p></figcaption></figure>

{% hint style="info" %}
### When to Show Feature Requests

In order to get the feature requests page to show reliably, the above API should be linked with an action inside your application, such as the press of a button.
{% endhint %}
