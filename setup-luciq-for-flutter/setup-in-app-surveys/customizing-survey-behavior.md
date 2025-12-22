---
description: >-
  This page covers all the in-app survey behavior that you can customize as well
  as related APIs for your Flutter apps.
---

# Customizing Survey Behavior

### Showing a Welcome Screen

You can show your users a welcome screen before a survey rather than asking the first question immediately. By default, this is disabled. To enable the survey welcome screen, use the following method.

{% code title="Dart" %}
```dart
Surveys.setShouldShowWelcomeScreen(true);
```
{% endcode %}

![Surveys - Mobile](<../../.gitbook/assets/c2788f362e035058c0ea40b4fca6e53130f0dc1319049027137aa72ffc483e1f flutter customizing survey behavior 1.png>)

### Integrating with Slack

If you have an already existing Slack integration, or are going to create one, you can enable auto-forwarding of Survey responses. If enabled, all NPS Survey score responses as well as Custom Survey responses will be forwarded to your Slack integration on the channel of your choosing.

Forwarded NPS responses will display user email, responses, and score, while Custom Survey responses will display the user email and every question and its response. You'll also have the option to reply to the user which will redirect you to the chat window to reply to that user.

### Setting App Store URL

While the SDK will normally automatically link to your application on the app store when needed, if your application is limited to certain regions, the automatic linking might not work. In these cases, we suggest using the API below to manually set the URL of your application in the store.

{% code title="Dart" %}
```dart
Surveys.setAppStoreURL('URL');
```
{% endcode %}
