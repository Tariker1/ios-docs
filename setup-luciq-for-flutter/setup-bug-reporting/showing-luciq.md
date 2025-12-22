---
description: >-
  This section covers how to set the user action that initializes Luciq, as well
  as how to customize what appears to your app users after the SDK is shown for
  Flutter apps.
---

# Showing Luciq

By default, Luciq is shown when the device is shaken. This can be customized to several other modes that show the SDK. You can also invoke the SDK manually from a custom gesture or a button you add to your app.

### Invocation Events

You can set the SDK to be invoked when your users do one or more of the following actions:

* Shake device
* Take a screenshot
* Tap on a floating button shown above your app's UI
* Two-finger swipe from right to left
* None (manual showing)

![](<../../.gitbook/assets/762637d6e43b2fb082f894471c9fa184dad101ffa6ab0a623247e8ebd2305847 flutter invocation 1.png>)

You have the option to set one or multiple invocation events. To customize the invocation event, pass one of the values of the `InvocationEvent` enum when starting the SDK.

{% code title="Dart" %}
```dart
Luciq.start('APP\_TOKEN', [InvocationEvent.shake]);
// Second argument takes an array of invocation events
```
{% endcode %}

You can find the possible invocation events below:

{% code title="Dart" %}
```dart
InvocationEvent.none
InvocationEvent.shake
InvocationEvent.screenshot
InvocationEvent.twoFingersSwipe
InvocationEvent.floatingButton
```
{% endcode %}

#### Floating Button

If you are using the floating button, you can set its default position as explained [here](../custom-settings/sdk-customization/ui-color-and-theme.md#floating-button-position).

#### Shaking Threshold

If you are using the shaking gesture as your invocation event, you can set how sensitive the device should be to the shaking. The thresholds in the example below are the default values. The higher the value, the less sensitive the device will be to shaking.

{% code title="Dart" %}
```dart
// iOS
BugReporting.setShakingThresholdForiPhone(3.0);
BugReporting.setShakingThresholdForiPad(1.0);
// Android
BugReporting.setShakingThresholdForAndroid(800);
```
{% endcode %}

#### None

Use the "none" event if you want to invoke the SDK manually in order to prevent the SDK from being shown through the other events.

### Changing the Invocation Event

If you want to change the invocation event to any of the other supported events, you can do so at runtime as shown below.

{% code title="Dart" %}
```dart
BugReporting.setInvocationEvents(List invocationEvents)
```
{% endcode %}

### Manual Showing

If you want to show the SDK manually, use the `show` method.

{% code title="Dart" %}
```dart
Luciq.show();
```
{% endcode %}

### Showing Specific Modes

By default, when the Luciq SDK is shown, a popup appears to your app users with options for them to report a bug ("Report a bug"), share feedback ("Suggest an improvement"), or ask you a question ("Ask a question").

The Prompt Options menu appears when Luciq is invoked in your app.

Instead of showing this [Prompt Options](../custom-settings/sdk-customization/prompt-options.md) menu that lets your users choose what they want to do, you can skip this step and take users directly to the bug, feedback, or question reporting flow.

#### Show Bug Form

This API will show users a form they can use to submit new bug reports.

{% code title="Dart" %}
```dart
BugReporting.showWithOptions(BugReporting.reportType.bug, [BugReporting.option.emailFieldHidden]);
```
{% endcode %}

#### Show Feedback Form

This API will show users a form they can use to submit new feedback and suggestions.

{% code title="Dart" overflow="wrap" %}
```dart
BugReporting.showWithOptions(BugReporting.reportType.feedback, [BugReporting.option.emailFieldOptional]);
```
{% endcode %}

#### Show Question Form

This API will show users a form they can use to submit a new question.

{% code title="Dart" overflow="wrap" %}
```dart
BugReporting.showWithOptions(BugReporting.reportType.question, [BugReporting.option.emailFieldOptional]);
```
{% endcode %}

#### Show Replies Page

This API will show users a page where they can see all their ongoing chats. If the user has no ongoing chats, this API won't have an effect.

{% code title="Dart" %}
```dart
Replies.show();
```
{% endcode %}

### Enable/Disable Luciq

Sometimes, you might need to disable or enable Luciq if, for example, the user would like to opt out of collecting any sort of logs, bugs, crashes, or survey responses. This can be done using the API below:

{% code title="Dart" %}
```dart
// Enabled
Luciq.setEnabled(true)
// Disabled
Luciq.setEnabled(false)
```
{% endcode %}

{% hint style="warning" %}
If Luciq is disabled, all user data and attributes are deleted from the device. Answered surveys will be stored in case Luciq is enabled again in order to not show the survey once more. Storing user attributes will not be available while Luciq is disabled.
{% endhint %}
