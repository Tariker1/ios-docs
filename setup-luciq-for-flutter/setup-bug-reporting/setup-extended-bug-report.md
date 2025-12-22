---
description: >-
  This section documents the APIs you can use to collect specific details in
  your bug reports from your QA team, internal testers, or beta testers on your
  Flutter apps.
---

# Setup Extended Bug Report

### What is an Extended Bug Report?

Free-form comments from reporters can be time-consuming to read through when triaging bugs. The Extended Bug Report standardizes all of your bug reports with additional fields that are commonly used by QA and technical beta testers: steps to reproduce the bug, actual results, and expected results.

In your dashboard, your testers' responses to the additional fields are listed under their description of the bug.

{% hint style="info" %}
If enabled, the Extended Bug Report adds a second step to the bug reporting flow that your testers experience in your app.
{% endhint %}

{% stepper %}
{% step %}
#### Reporter step

Reporters submit their description of the bug (free-form).
{% endstep %}

{% step %}
#### Extended Bug Report step

When enabled, testers are presented with additional structured fields such as:

* Steps to reproduce
* Actual results
* Expected results
{% endstep %}
{% endstepper %}

### Enabling the Extended Bug Report

By default, the Extended Bug Report mode is disabled. When enabling the Extended Bug Report, you can set whether the additional fields are required or optional.

{% code title="Dart" %}
```dart
BugReporting.setExtendedBugReportMode(ExtendedBugReportMode.enabledWithRequiredFields;);
```
{% endcode %}

Here are the possible modes you can set for Extended Bug Reports.

{% code title="Dart" %}
```dart
//Disable extended bug report mode
ExtendedBugReportMode.disabled
//Enable extended bug report mode and make all additional fields required
ExtendedBugReportMode.enabledWithRequiredFields;
//Enable extended bug report mode and make all additional fields optional
ExtendedBugReportMode.enabledWithOptionalFields
```
{% endcode %}
