---
description: Learn how to manually show the replies page to the users in your Flutter apps
---

# Show Replies List

### Show Replies

The below API can be used to display the replies page. This page contains a list of any previous chats that were opened for this customer.

{% code title="Dart" %}
```dart
Replies.show();
```
{% endcode %}

### Check if User Has Chats

If a user has no pre-existing chats, the previous API won't show the replies page. You can check whether the user has any available chats or not using the below API.

{% code title="Dart" %}
```dart
final hasChats = Replies.hasChats();
```
{% endcode %}

