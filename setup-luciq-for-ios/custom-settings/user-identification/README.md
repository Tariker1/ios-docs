---
description: >-
  This section covers how to bind each report to the identity of the user
  reporting the problem for your iOS app. You have the flexibility to add some
  extra attributes about the device as well as the us
---

# User identification

Luciq helps you better identify the bug reports or feedback you get by associating a user's identity to them.

### User Email and Name

If you already have a user's name and email, you can pre-fill the email field in the bug, feedback, and question reporting flow. The user will then be identified in all reports (bugs, improvements, questions), crashes, surveys, and feature requests.

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p><br><em>An example of a pre-filled email field in the bug reporting form.</em></p></figcaption></figure>

Ideally, this API should be called as soon as a user logs into your app.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.identifyUser(withID: "2374927027", email: "john.appleseed@apple.com", name: "John Appleseed")
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq identifyUserWithID:@"2374927027" email:@"john.appleseed@apple.com" name:@"John Appleseed"];
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
### Null Values

If both the email and ID parameters are empty or null, the user will not be identified, and the SDK will through an error.
{% endhint %}

### User Data

You can also add additional data about your users. This API is best used for dumping large amounts of data. Each call to this method overrides the user data to be attached. The maximum length of the string is 1,000 characters.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
let profileDetails = user.allProfileDetails()
let profileDetailsString = "\(profileDetails)"
Luciq.userData = profileDetailsString
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
NSDictionary *profileDetails = [user allProfileDetails];
NSString *profileDetailsString = [NSString stringWithFormat:@"%@", profileDetails];
Luciq.userData = profileDetailsString;
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Logout

When a user logs out, the following API should be called. Calling `logOut` will reset the value of the email and name previously set. It will also remove any currently set user attributes, user events, user chats, and user data.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.logOut()
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq logOut];
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
### Logout only when user is identified

Please note that if the user is currently not identified using the `identifyUser` API, the `logOut` method will have no effect.
{% endhint %}
