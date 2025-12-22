# Disabling/Enabling In-App Surveys

This page details the API for disabling and enabling in-app surveys for your Flutter apps.

You can completely disable any surveys from showing in general using the following API. Please note that this also disables surveys that will be shown manually as this disables any survey related request.

{% code title="Dart" %}
```dart
Surveys.setEnabled(false);
```
{% endcode %}
