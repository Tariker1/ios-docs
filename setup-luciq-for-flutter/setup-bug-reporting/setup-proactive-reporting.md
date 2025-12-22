---
description: >-
  This page covers how you can use Proactive Reporting to prompt users to submit
  feedback reports and how to configure it using APIs.
---

# Setup Proactive Reporting

### What is Proactive Reporting?

Proactive Reporting is a feature that prompts end users to submit their feedback after our SDK automatically detects a frustrating experience.

The frustrating experience our SDK detects to trigger the feedback modal is **Force Restart**.\
If you have our **Force Restart** product enabled as part of your plan, users will be prompted to submit their feedback and explain what triggered them to force restart the app.

The details of the feature are as follows:

* You should have **Force Restart** as part of your plan.
* Enable the feature (Using the APIs in the upcoming section).
* Once the SDK captures a Force Restart occurrence, a modal will be triggered to ask your end-users if they want to share their feedback and experience.
* This feedback will reflect on your Bug Reporting page in the dashboard.

If enabled, users will first see a modal asking if they want to report this experience. If their answer is yes, they will see a **Feedback** description modal that allows them to enter their email and describe their experience using their own words.

|                                                                                                                             |                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| ![](<../../.gitbook/assets/ba2fb841c90a3ee873e13a59fa07c9c64fc7d3eb27379cd89e17d96b0e9422bd ios proactive reporting 1.png>) | ![](<../../.gitbook/assets/96690010a0bb1031eaeba0c1a136279c9ff405974320fce53d4dbcec4134bec3 ios proactive reporting 2.png>) |

On the dashboard, your end-user's feedback will be reflected in the Bug Reporting page as a **Frustrating Experience** report type.\
Clicking the **Open Occurrence** under the **Force Restart** section will take you to the occurrence where the end-user force closed the app in the Force Restart product.

The report's details show the data from the session after the user force-closed the app, while the details you’ll see in the Force Restart occurrence are from the session in which they force-closed the app.

### Enabling Proactive Reporting

By default, Proactive Reporting is disabled. You can use the API below to:

* Enable/disable the feature.
* Configure the gap between two pop-ups for the same user.
* Configure the gap between the app launch and the first pop-up.

The gap calculation starts when our SDK detects a Force Restart or a Crash occurrence, usually a few milliseconds after the launch.

{% code title="Dart" %}
```dart
BugReporting.setProactiveReportingConfigurations(
  const ProactiveReportingConfigs(
    enabled: true,
    gapBetweenModals: 2, // time in seconds
    modalDelayAfterDetection: 2, // time in seconds
  ),
);
```
{% endcode %}

### Good to know about Proactive Reporting

{% hint style="info" %}
The feature’s default behavior is as follows:

* Feature is disabled by default.
* If you don’t configure the gap between pop-ups, the default gap will be 24 hours.
* If you don’t configure the gap between the launch and the first pop-up, the default gap will be 2 seconds.
* If you have Surveys enabled in your plan, please contact the support team to enable this feature for you from our backend. Remember to configure the surveys triggering differently from the proactive reporting modal to avoid overwhelming your users.
* To use this feature, Force Restart (part of Crash Reporting) has to be part of your plan.
* Proactive reports have the same data retention as Force Restart (part of Crash Reporting).
{% endhint %}
