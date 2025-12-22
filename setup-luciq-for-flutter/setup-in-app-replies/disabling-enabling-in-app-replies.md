# Disabling/Enabling In-App Replies

Explained in this page is how to hide the replies page in your Flutter apps.

When the Luciq SDK is invoked, a popup appears to your app users with default [Prompt Options](../custom-settings/sdk-customization/prompt-options.md) for them to "Report a problem" (send you a bug report), "Suggest an improvement" (send you feedback), or "Ask a Question" (send you a question). There is also an option to view the chat history, or replies, page.

The API below can be used to hide the replies page from the user as well as disable it. The button in the prompt options will no longer be visible if this API is used. The in-app notifications will also be disabled, and manually showing the chats list won't have an effect.

{% code title="Dart" %}
```dart
Replies.setEnabled(false);
```
{% endcode %}
