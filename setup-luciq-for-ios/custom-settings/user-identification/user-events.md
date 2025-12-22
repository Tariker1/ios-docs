# User Events

You can log custom user events throughout your application. Custom events are automatically included with each report.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.logUserEvent(withName: "Skipped Walkthrough")
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq logUserEventWithName:@"Skipped Walkthrough"];
```
{% endcode %}
{% endtab %}
{% endtabs %}
