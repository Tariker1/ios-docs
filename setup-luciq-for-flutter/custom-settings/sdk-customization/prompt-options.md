---
description: >-
  This section covers how to control the popup menu that appears when your app
  users invoke Luciq for Flutter apps.
---

# Prompt Options

By default, when the Luciq SDK is shown, a popup appears to your app users with options for them to report a bug ("Report a bug"), share feedback ("Suggest an improvement"), or ask you a question ("Ask a question"). This popup is called the Prompt Options.

All Luciq popups follow the color theme and primary color that you set for the SDK.

By default, all of your enabled products are listed in the Prompt Options menu. You can control which options appear by disabling and enabling any of the products. Each one can be enabled or disabled separately.

{% code title="Dart" %}
```dart
// Disable the Bugs, Feedback, & Questions. If disabled, "Report a problem" "Suggest an improvement" & "Ask a Question" are removed from Luciq's prompt, and manually showing the bug reporting or feedback doesn't have an effect.
BugReporting.setEnabled(true);

// Specify which of the feedback, bug, or question options appear in the prompt options
BugReporting.setReportTypes([ReportType.bug, ReportType.feedback, ReportType.question]);

// Disable the Replies. If disabled, the chats list button is removed from Luciq's prompt, the in-app notifications are disabled, and manually showing the chats list doesn't have an effect.
Replies.setEnabled(true);
```
{% endcode %}

{% hint style="info" %}
When only a single option is enabled, it becomes the default invocation mode. If all options are disabled, bug reporting becomes the default invocation mode and the Prompt Options menu won't appear to your users; instead, they will be shown the bug reporting form.
{% endhint %}
