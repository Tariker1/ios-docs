---
description: >-
  This section covers on-boarding your users about how to reach you through
  Luciq with a mode for either beta testers or live users on iOS apps.
---

# Welcome Message

### Setting the welcome message mode

By default, a welcome message that explains how to [show Luciq](../../setup-bug-reporting/showing-luciq.md) will be shown to your app users within 10 seconds of starting their first session after the SDK is integrated. The welcome mode can be set to live, beta, or disabled using the method below. The default welcome mode is set to live.

The popups that appear follow the [color theme](ui-color-and-theme.md) and [primary color](ui-color-and-theme.md) that you set for the SDK.

You can also edit the content of the message using the method and keys found in the [Locale](sdk-locale.md) page.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.welcomeMessageMode = LCQWelcomeMessageMode.beta // For beta testers
Luciq.welcomeMessageMode = LCQWelcomeMessageMode.live // For live users
Luciq.welcomeMessageMode = LCQWelcomeMessageMode.disabled // Disable welcome message
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq setWelcomeMessageMode:LCQWelcomeMessageModeBeta]; // For beta testers
[Luciq setWelcomeMessageMode:LCQWelcomeMessageModeLive]; // For live users
[Luciq setWelcomeMessageMode:LCQWelcomeMessageModeDisabled]; // Disable welcome message
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Showing the welcome message manually

Instead of showing the welcome message automatically, you can manually show the welcome message in either live or beta mode using the following method.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.showWelcomeMessage(with: LCQWelcomeMessageMode.beta) // For beta testers
Luciq.showWelcomeMessage(with: LCQWelcomeMessageMode.live) // For live users
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Instabug showWelcomeMessageWithMode:IBGWelcomeMessageModeBeta]; // For beta testers
[Instabug showWelcomeMessageWithMode:IBGWelcomeMessageModeLive]; // For live users
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
### Invocation Method Set to None?

If your [invocation method](../../setup-bug-reporting/showing-luciq.md) is set to "none", the welcome message will not appear to your users.
{% endhint %}

### Live welcome message

This mode is primarily aimed at users of your production builds, or live apps.

A single popup appears to your users with instructions on how to show Luciq depending on the invocation method you're using.

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption><p><br><em>Examples of the welcome message that appears to users in live apps depending on the invocation method set.</em></p></figcaption></figure>

### Beta welcome message

This mode is primarily aimed at beta testers of your development builds, or beta apps.

A three-step on-boarding flow appears to your testers. First, your testers see a welcome message customized for beta testers. The second screen explains how to show Luciq depending on the invocation method you're using. The third and last screen reminds your testers to use the latest version of your application in order to access all your latest fixes and features.

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption><p><br><em>An example of the three-step on-boarding flow that appears to users in beta apps.</em></p></figcaption></figure>
