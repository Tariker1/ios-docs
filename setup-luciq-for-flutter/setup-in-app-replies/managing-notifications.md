---
description: >-
  Detailed in this page is how you can manage in-app notifications for new
  in-app chat messages for your Flutter apps.
---

# Managing Notifications

### In-App Notifications

{% hint style="info" %}
By default, a notification will be shown on top of your app's UI when a new message is received.
{% endhint %}

#### Disabling In-App Notifications

Use the following method to disable notifications that appear in-app.

{% code title="Dart" %}
```dart
Replies.setInAppNotificationsEnabled(false);
```
{% endcode %}

#### In-App Notification Sound

When your app users receive an in-app notification through Luciq, sound is enabled by default. You can disable it with the following method.

{% code title="Dart" %}
```dart
Replies.setInAppNotificationSound(false);
```
{% endcode %}

#### Get Unread Messages Count

You can use the following method to get the number of messages the user has yet to read.

{% code title="Dar" %}
```dart
final count = Replies.getUnreadRepliesCount();
```
{% endcode %}
