---
description: >-
  This section covers how to customize how Instabug appears in your app in order
  to match your design and brand palette for Flutter apps.
---

# UI Color & Theme

### SDK Theme

The SDK UI has two color themes: light and dark.

You can set which theme to use with the following method:

{% code title="Dart" %}
```dart
Luciq.setColorTheme(ColorTheme.dark);
```
{% endcode %}

Here are the possible color themes:

{% code title="Dart" %}
```dart
ColorTheme.light
ColorTheme.dark
```
{% endcode %}

### Setting the Primary Color

You can set the color of UI elements that indicate interactivity, like links, or a call to action, like buttons, using the following method:

{% code title="Dart" %}
```dart
Luciq.setPrimaryColor(Color.blue);
```
{% endcode %}

### Floating Button Position

If your [invocation event](https://docs.luciq.ai/docs/flutter-invocation#section-invocation-events) is a floating button, you can set its position in your app. You can set the edge and the offset, which specify the position on the y-axis.

{% code title="Dart" %}
```dart
BugReporting.setFloatingButtonEdge(FloatingButtonEdge.right, 250);
```
{% endcode %}

### Video Recording Button

If you've enabled video recordings as attachments, you can change the position of the red recording button displayed in the screenshot below. The default position of the button is **bottom right**.

{% hint style="info" %}
Default position: bottom right
{% endhint %}

Use this method to set the position of the video recording button:

{% code title="Dart" %}
```dart
BugReporting.setVideoRecordingFloatingButtonPosition(Position.topLeft);
```
{% endcode %}

Here are the possible values:

{% code title="Dart" %}
```dart
Position.topLeft
Position.topRight
Position.bottomLeft
Position.bottomRight
```
{% endcode %}
