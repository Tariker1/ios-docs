---
description: >-
  Covered here is how to set up the event handler that fires before and after
  every survey is shown for your Flutter apps.
---

# In-app Surveys Callback

You can execute code in a handler that gets called before a survey is shown and after it has been dismissed. You can use this for things like pausing and resuming a game, for example.

#### Before Showing the Survey

{% code title="Dart" %}
```dart
Surveys.setOnShowCallback(Function function);
```
{% endcode %}

#### After the Survey Has Been Dismissed

{% code title="Dart" %}
```dart
Surveys.setOnDismissCallback(Function function);
```
{% endcode %}
