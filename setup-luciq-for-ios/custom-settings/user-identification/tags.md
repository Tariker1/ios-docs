# Tags

You can add custom tags to your bug and crash reports. These tags can later be used to filter reports or set custom rules from your dashboard.

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

The example below demonstrates how to add tags to a report.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.appendTags(["Design", "Flow"])
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq appendTags:@[@"Design", @"Flow"]];
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
### Adding tags before sending reports

Sometimes it's useful to be able to add a tag to a bug report before it's been sent. In these cases, the perfect solution would be use the event handlers of the bug reporting class. You can find more details [here](../../setup-bug-reporting/bug-reporting-callbacks.md).
{% endhint %}

You can also get all the currently set tags as follows.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
let tags = Luciq.getTags()
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
NSString *tags = [Luciq getTags];
```
{% endcode %}
{% endtab %}
{% endtabs %}

Last, you can reset all the tags.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.resetTags()
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq resetTags];
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Managing Tags

If you'd like to remove a particular tag from your dashboard to prevent it from appearing again when entering a new tag manually, you can do so by navigating to the tags page under the settings options and remove the tag. You can also edit and rename the tag.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
