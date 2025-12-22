---
description: >-
  Covered here is how to set up the event handler that fires with every new
  message received for your Flutter apps.
---

# In-App Replies Callbacks

### New Received Message

This block is executed each time a new message is received in the SDK. This can be used to show your own UI when a new message is received when default chat notifications are disabled.

{% code title="Dart" %}
```dart
Replies.setOnNewReplyReceivedCallback(Function function);
```
{% endcode %}
