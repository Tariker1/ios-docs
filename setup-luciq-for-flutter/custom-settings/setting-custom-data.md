---
description: >-
  Discussed here is how to set user attributes and tags, as well as log user
  events, and their relevant APIs for your Flutter app.
---

# Setting Custom Data

### User Attributes

You can assign custom attributes to your users and they will show up on your Luciq dashboard with each report. These attributes can later be used to filter reports in your dashboard.

This is where additional user attributes appear in your bug reports.

To add a new user attribute use the following method.

{% code title="Dart" %}
```dart
Luciq.setUserAttribute(String value, String key)
// Examples
Luciq.setUserAttribute("18", "Age");
Luciq.setUserAttribute("True", "Logged In");
```
{% endcode %}

{% hint style="info" %}
Disclaimers:

* Each Bug or Crash Report could have up to 100 user attributes only.
* The character limit for the Keys and Values is 90 characters each.
{% endhint %}

You can also retrieve the current value of a certain user attribute, or retrieve all user attributes.

{% code title="Dart" %}
```dart
// Getting attribute
Luciq.getUserAttributeForKey("Logged in");
// Loading all attributes
Luciq.getUserAttributes();
```
{% endcode %}

Or remove the current value of a certain user attribute:

{% code title="Dart" %}
```dart
Luciq.removeUserAttribute("Logged In");
```
{% endcode %}

### User Events

You can log custom user events throughout your application. Custom events are automatically included with each report.

{% code title="Dart" %}
```dart
Luciq.logUserEvent("OnFeedbackButtonClicked");
```
{% endcode %}

### Tags

You can add custom tags to your bug and crash reports. These tags can later be used to filter reports or set custom rules from your dashboard.

This is where tags appear in your bug reports.

The example below demonstrates how to add tags to a report.

{% code title="Dart" %}
```dart
Luciq.appendTags(["Tag 1", "Tag 2"]);
```
{% endcode %}

You can also get all the currently set tags as follows.

{% code title="Dart" %}
```dart
Luciq.getTags();
```
{% endcode %}

Last, you can reset all the tags.

{% code title="Dart" %}
```dart
Luciq.resetTags();
```
{% endcode %}

#### Managing Tags

If you'd like to remove a particular tag from your dashboard to prevent it from appearing again when entering a new tag manually, you can do so by navigating to the tags page under the settings options and remove the tag. You can also edit and rename the tag.

![](<../../.gitbook/assets/7f09dd89c1de2683fb2cbcfd72673d3df7a5cdd64304ea4ab7201938e10e791c flutter set custom data 1.png>)

***

### Feature Flags

In certain scenarios, you might find that you're rolling out different experiments to different users, where your user base would see different features depending on what's enabled for them. In scenarios such as these, you'll want to keep track of the enabled experiments for each user and even filter by them.

Notes:

* Feature Flag Naming: Each feature flag name should not exceed 70 characters and each variant name should not exceed 70 characters. Otherwise, they will get ignored by the SDK. Note that feature flag names are case-insensitive.
* Feature Flag Persistence: Feature flags persist beyond individual sessions and are not automatically removed at the end of a session. Additionally, calling the logOut function does not impact the existence of the feature flag. The feature flag is only removed when you call the removing method or the clearing method.
* The amount of feature flags sent in a session is 200 with a maximum of 1 variant per multivariate feature flag. For example, a feature flag that has 3 variants sent within 1 session will only be sent to our backend as the last variant, and not all 3.

#### Adding Feature Flags

**Boolean Feature Flags - Example Usage**

Below is an example of where in your code you would use a boolean feature flag. In this example, you are experimenting with feature logic that controls whether or not the user has a Dark Mode toggle available.

{% code title="Dart" %}
```dart
Luciq.addFeatureFlags([FeatureFlag(name: 'Boolean Feature Flag')]);
```
{% endcode %}

**Multivariant Feature Flags - Example Usage**

Below is an example of where in your code you would use a feature flag with multiple variants. In this example, you are experimenting with feature logic that controls multiple versions of a specific feature.

{% code title="Dart" %}
```dart
Luciq.addFeatureFlags([FeatureFlag(name: 'Feature Flag', variant: 'Value')]);
```
{% endcode %}

#### Removing Feature Flags

If your feature flag is concluded or you would like to simply remove it, you can use this method:

{% code title="Dart" %}
```dart
Luciq.removeFeatureFlags(['feature flag']);
```
{% endcode %}

#### Clearing Feature Flags

You can use the below method to clear all the Feature Flags from your reports:

{% code title="Dart" %}
```dart
Luciq.clearAllFeatureFlags();
```
{% endcode %}
