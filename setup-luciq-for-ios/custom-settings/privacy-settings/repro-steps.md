---
description: How to automatically mask the screens reported in Repro Steps
---

# Repro Steps

Repro Steps is your go-to tool for understanding what led to a bug or crash in your app. This guide will help you make the most of Repro Steps.

#### What are "Repro Steps"?

Repro Steps capture and present all the actions a user takes in your app before encountering a bug or crash. These steps are grouped by the app view, and you can view user steps alongside relevant screenshots. It's like having a play-by-play visual and written record of the user's actions leading to the problem.

<figure><img src="https://files.readme.io/51c0cd2-Repro_Steps_1.png" alt="Repro steps captured by Instabug"><figcaption><p>Repro steps captured by Luciq</p></figcaption></figure>

#### Where can you find "Repro Steps"?

To find the Repro Steps, simply scroll down below the bug details. If you are on the crash reporting tool, you will find them in the occurrences page of a crash below the crash details. Check the screenshot below to find them

<figure><img src="https://files.readme.io/e13a5ab-Repro_Steps_2.png" alt="Location of Reprosteps inside a Crash Report"><figcaption><p>Location of Reprosteps inside a Crash Report</p></figcaption></figure>

<figure><img src="https://files.readme.io/b0d726f-Repro_Steps_3.png" alt="Location of Reprosteps inside a Bug Report"><figcaption><p>Location of Reprosteps inside a Bug Report</p></figcaption></figure>

#### Understanding the Setup

Repro Steps are organized by the different screens in your app that users interact with. Each screen view visited by the user contains a set of chronological steps, giving you a clear picture of what led to the reported issue.

#### Understanding Logged Data and Captured Events

Logged data captures user interactions, such as swipes, scrolls, taps, and more. It provides insights into how users engage with your app. The captured events track app states, including background/foreground transitions, activity changes, and memory warnings.

#### How can you enable Repro steps?

Repro Steps is by default enabled with screenshots for bug reporting, and enabled without screenshots for crash reporting. So do you need to change anything here? If yes, you can use the following properties:

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.setReproStepsFor(.all, with: .enable)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq setReproStepsFor:LCQIssueTypeAll withMode:LCQUserStepsModeEnable];
```
{% endcode %}
{% endtab %}
{% endtabs %}

You can change the value of the Issue Type.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
//Bug Reporting and Crash Reporting  
.all  
//Bug Reporting Only  
.bug  
//Crash Reporting Only  
.crash
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
//Bug Reporting and Crash Reporting
LCQIssueTypeAll
//Bug Reporting Only
LCQIssueTypeBug
//Crash Reporting Only
LCQIssueTypeCrash
```
{% endcode %}
{% endtab %}
{% endtabs %}

You can change the value of the User Steps Mode.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
//Enable with Screenshots  
.enable  
//Enable with NO Screenshots  
.enabledWithNoScreenshots  
//Disable  
.disable
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
//Enable with Screenshots
LCQUserStepsModeEnable
//Enable with NO Screenshots
LCQUserStepsModeEnabledWithNoScreenshots
//Disable
LCQUserStepsModeDisable
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Examples

#### **Enable with Screenshots for both Bug Reporting and Crash Reporting:**

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.setReproStepsFor(.all, with: .enable)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq setReproStepsFor:LCQIssueTypeAll withMode:LCQUserStepsModeEnable];
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### **Enable with No Screenshots for Crash Reporting.**

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.setReproStepsFor(.crash, with: .enabledWithNoScreenshots)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq setReproStepsFor:LCQIssueTypeCrash withMode:LCQUserStepsModeEnabledWithNoScreenshots];
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### **Completely disable for both Bug Reporting and Crash Reporting.**

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
Luciq.setReproStepsFor(.all, with: .disable)
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
[Luciq setReproStepsFor:LCQIssueTypeAll withMode:LCQUserStepsModeDisable];
```
{% endcode %}
{% endtab %}
{% endtabs %}
