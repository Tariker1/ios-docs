# Feature Flags

In certain scenarios, you might find that you're rolling out different experiments to different users, where your user base would see different features depending on what's enabled for them. In scenarios such as these, you'll want to keep track of the enabled experiments for each user and even filter by them.

**Notes:**

1. **Feature Flag Naming**: Each feature flag name should not exceed 70 characters and each variant name should not exceed 70 characters. Otherwise, they will get ignored by the SDK. Note that feature flag names are case-insensitive.
2. **Feature Flag Persistence**: Feature flag persist beyond individual sessions and are not automatically removed at the end of a session. Additionally, calling the logOut function does not impact the existence of the feature flag. The feature flag is only removed when you call the removing method or the clearing method.
3. The amount of feature flags sent in a session is 200 with maximum of 1 variant per a multivariate feature flag. For example, a feature flag that has 3 variants sent within 1 session will only be sent to our backend as the last variant, and not all 3.

For more information on feature flags, visit [Feature Flags.](feature-flags.md)

### Adding Feature flags

#### Boolean Feature Flags — Example Usage

Below is an example of where in your code you would use feature flag. In this example, you are experimenting with feature logic that controls whether or not the user has a Dark Mode toggle available.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
let flag = FeatureFlag(name: "flag")
Luciq.add(featureFlag: flag)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq addFeatureFlag: [[LCQFeatureFlag alloc] initWithName:@"boolFeatureFlag"]];
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Multivariant Feature Flags — Example usage

Below is an example of where in your code you would use feature flag with multiple variants. In this example, you are experimenting with feature logic that controls multiple versions of a specific feature.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
let flagWithVariant = FeatureFlag(name: "flag", variant: "variant")
Luciq.add(featureFlag: flagWithVariant)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq addFeatureFlag: [[LCQFeatureFlag alloc] initWithName:@"stringFeatureFlag" variant:@"Value1"]];
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Removing Feature Flags

If your feature flag is concluded or you would like to simply remove it, you can use this method:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.removeFeatureFlag("stringFeatureFlag")
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq removeFeatureFlag:@"boolFeatureFlag"];
[Luciq removeFeatureFlags:@[flag1]];
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### Clearing Feature Flags

You can use the below method to clear all the Feature Flags from your reports:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.removeAllFeatureFlags()
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq removeAllFeatureFlags];
```
{% endcode %}
{% endtab %}
{% endtabs %}
