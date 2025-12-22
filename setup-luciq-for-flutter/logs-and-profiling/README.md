---
description: >-
  An overview of the different types of logs can be found in this section along
  with details regarding the session profiler for your Flutter apps.
---

# Logs & Profiling

{% hint style="warning" %}
#### Privacy Policy

It is highly recommended to mention in your privacy policy that you may be collecting logging data in order to assist with troubleshooting bugs.
{% endhint %}

With each bug and crash report, you can find a whole host of useful logs, as well as a session profiler to help you track your issues further.

{% stepper %}
{% step %}
#### [Repro Steps](auto-masking-and-repro-steps.md)

Trace your users' steps visually with simplified logs, grouped by screenshots.
{% endstep %}

{% step %}
#### Session Profiler

The session profiler shows the state of the device up to a minute prior to a report being sent, which can assist with the bug fixing process.
{% endstep %}

{% step %}
#### [Report Logs](report-logs.md)

Instead of having to reproduce the crash or bug on your device to check the logs, we automatically attach the console logs, the verbose logs, all the steps done by the user until the report was sent, the user events, and the network logs.
{% endstep %}
{% endstepper %}
