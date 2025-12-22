---
title: iOS code
---

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
let configuration = URLSessionConfiguration.ephemeral
NetworkLogger.enableLogging(for: configuration)
let session = URLSession(configuration: configuration)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
NSURLSessionConfiguration *configuration = NSURLSessionConfiguration.ephemeralSessionConfiguration;
[LCQNetworkLogger enableLoggingForURLSessionConfiguration:configuration];
NSURLSession *session = [NSURLSession sessionWithConfiguration:configuration];
```
{% endcode %}
{% endtab %}
{% endtabs %}
