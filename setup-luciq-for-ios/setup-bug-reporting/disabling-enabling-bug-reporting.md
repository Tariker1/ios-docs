---
description: This section covers how to disable and enable bug reporting on iOS.
---

# Disabling/Enabling Bug Reporting

When your users [invoke the SDK](showing-luciq.md#invocation-events), a popup appears with default [Prompt Options](../custom-settings/sdk-customization/prompt-options.md) for them to "Report a bug" (submit a bug), "Suggest an improvement" (send you feedback), or "Ask a question" (send you a chat).

These options can be disabled or enabled separately. When only a single option is enabled, it becomes the default [invocation mode](showing-luciq.md#invocation-events) and the Prompt Options menu doesn't appear.

The below API completely disables all forms of bug, improvement, and question reports.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
BugReporting.enabled = false
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
LCQBugReporting.enabled = NO;
```
{% endcode %}
{% endtab %}
{% endtabs %}

You can also specify whether to show any of the Report a bug, Suggest an improvement, Ask a question options, or all using this API:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
// Specify which of the feedback or bug options appear in the prompt options
BugReporting.promptOptionsEnabledReportTypes = [.bug, .feedback, .question]
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
// Specify which of the feedback or bug options appear in the prompt options
LCQBugReporting.promptOptionsEnabledReportTypes = LCQBugReportingReportTypeBug | LCQBugReportingReportTypeFeedback | LCQBugReportingReportTypeQuestion;
```
{% endcode %}
{% endtab %}
{% endtabs %}

By default, all three options are enabled if they are available in your current subscription plan.
