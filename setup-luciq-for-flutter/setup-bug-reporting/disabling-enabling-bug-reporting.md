---
description: This section covers how to disable and enable bug reporting on Flutter.
---

# Disabling/Enabling Bug Reporting

When your users [invoke the SDK](showing-luciq.md), a popup appears with default [Prompt Options](../custom-settings/sdk-customization/prompt-options.md) for them to "Report a bug" (submit a bug), "Suggest an improvement" (send you feedback), or "Ask a question" (send you a chat). These options can be disabled or enabled separately. When only a single option is enabled, it becomes the default invocation mode and the Prompt Options menu doesn't appear.

The below API completely disables all forms of bug, improvement, and question reports.

{% code title="Dart" %}
```dart
BugReporting.setEnabled(false);
```
{% endcode %}

You can also specify whether to show any of the Report a bug, Suggest an improvement, Ask a question options, or all using this API:

{% code title="Dart" %}
```dart
BugReporting.setReportTypes([ReportType.bug, ReportType.feedback, ReportType.question]);
```
{% endcode %}

{% hint style="info" %}
By default, all three options are enabled if they are available in your current **plan**: https://luciq.ai/pricing
{% endhint %}
