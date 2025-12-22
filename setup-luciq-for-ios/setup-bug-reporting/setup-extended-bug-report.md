---
description: >-
  This section documents the APIs you can use to collect specific details in
  your bug reports from your QA team, internal testers, or beta testers on your
  iOS apps.
---

# Setup Extended Bug Report

## Enabling the Extended Bug Report

By default, the Extended Bug Report mode is disabled. When enabling the Extended Bug Report, you can set whether the additional fields are required or optional.

{% tabs %}
{% tab title="Swift" %}
```swift
BugReporting.extendedBugReportMode = .enabledWithRequiredFields
```
{% endtab %}

{% tab title="Objective-C" %}
```objective-c
LCQBugReporting.extendedBugReportMode = LCQExtendedBugReportModeEnabledWithRequiredFields;
```
{% endtab %}
{% endtabs %}

Here are the possible modes you can set for Extended Bug Reports.

{% tabs %}
{% tab title="Swift" %}
```javascript
//Disable extended bug report mode
.disabled
//Enable extended bug report mode and make all additional fields required 
.enabledWithRequiredFields
//Enable extended bug report mode and make all additional fields optional
.enabledWithOptionalFields
```
{% endtab %}

{% tab title="Objective-C" %}
```python
//Disable extended bug report mode
LCQExtendedBugReportModeDisabled
//Enable extended bug report mode and make all additional fields required 
LCQExtendedBugReportModeEnabledWithRequiredFields
//Enable extended bug report mode and make all additional fields optional
LCQExtendedBugReportModeEnabledWithOptionalFields
```
{% endtab %}
{% endtabs %}

