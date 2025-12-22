---
description: >-
  This section covers how to bind each report to the identity of the user
  reporting the problem for your Flutter app. You can also add extra attributes
  about the device and the user. Luciq helps you bet
---

# User Identification

### User Email and Name

If you already have a user's name and email, you can pre-fill the email field in the bug, feedback, and question reporting flow. The user will then be identified in all reports (bugs, improvements, questions), crashes, surveys, and feature requests.

Ideally, call this API as soon as a user logs into your app.

{% code title="Dart" %}
```dart
Luciq.identifyUser(String email, [String name, String id]);
```
{% endcode %}

{% hint style="danger" %}
The userID Must Be Unique

The `userID` you provide is the primary identifier for a user within Luciq. You must ensure that this ID is unique for each of your users.

Providing a generic, non-unique ID (e.g., `guest` or `unknown_user`) for multiple users will cause their data to be incorrectly merged. This can lead to critical data integrity and privacy issues, such as different users being able to see and reply to each other's private chat conversations.

If a user is anonymous, do not call the `identifyUser` API. The SDK will automatically handle a unique anonymous identity for you.
{% endhint %}

{% hint style="warning" %}
Null Values

If both the `email` and `ID` parameters are empty or null, the user will not be identified, and the SDK will throw an error.
{% endhint %}

### User Data

You can add additional data about your users. This API is best used for dumping large amounts of data. Each call to this method overrides the user data attached. The maximum length of the string is 1,000 characters.

{% code title="Dart" %}
```dart
Luciq.setUserData("User data sample");
```
{% endcode %}

### Logout

When a user logs out, call the following API. Calling `logOut` will reset the email and name previously set. It will also remove any currently set user attributes, user events, user chats, and user data.

{% code title="Dart" %}
```dart
Luciq.logOut();
```
{% endcode %}

{% hint style="warning" %}
Logout only when user is identified

If the user is not currently identified using the `identifyUser` API, the `logOut` method will have no effect.
{% endhint %}

