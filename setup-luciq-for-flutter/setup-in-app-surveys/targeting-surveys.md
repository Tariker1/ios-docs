---
description: >-
  Detailed here is how you can target specific users for your In-App Surveys as
  well as related APIs for your Flutter apps.
---

# Targeting Surveys

You can define criteria that your users have to meet in order for your surveys to appear in their app. This can be done through both automatic and manual targeting. The available targeting types vary based on the survey or announcement template you're using.

### Auto Targeting

After choosing the survey type you want to create, you can target specific audiences using custom conditions.

When you select **Auto Targeting**, you can define criteria for who should receive the survey. Your users matching the conditions you set will automatically see the survey. In addition to default attributes like App Version, OS, Email, Sessions Count, Last Seen, Country, etc., you can set conditions for custom user attributes or user events that you have created. Multiple different criteria of any type can be added.

You can specify the who, when, and frequency of the survey.

{% stepper %}
{% step %}
#### Who

Used to automatically target specific users. You can target users with specific attributes or users that have performed specific events.
{% endstep %}

{% step %}
#### When

Specify when the survey should show to your users. By default, this is set to 10 seconds after the application launches. This can be set so that the survey shows the moment a specific event occurs.
{% endstep %}

{% step %}
#### Frequency

The number of times the user sees the survey within a certain period. By default, this is once every 30 days. The number of days can be edited and you can set it so that the survey only appears once and never again afterward.
{% endstep %}
{% endstepper %}

Depending on the template you use, different options will be available to use for automatic targeting.

* Custom/NPS/App Rating: these three templates can automatically target using default attributes, custom attributes, and user events.

{% hint style="info" %}
Targeting using App Version

Starting from version 8.5.0, the accepted app versions can be any of the ones with the following formats:

* x.y.z (ex: 1.4.2)
* x.y.z.w (ex: 1.4.2.7)
* x.y.z\[any string] (ex: 1.4.2april2016) — this format can only be used with equals to and can't be set to greater or less than
{% endhint %}

#### Variant Targeting

Starting from SDK version x.x.x, variant targeting is available, enabling you to display surveys to users based on app variants (e.g. free, premium, beta).

Variant targeting in Auto Targeting rules supports `equals` and `not equals` operators only.

This feature is case-sensitive and must be explicitly set in your app.

To set the app variant at runtime:

{% code title="Dart" %}
```dart
// Dart
Luciq.setAppVariant("variant");
```
{% endcode %}

Or while initializing the SDK:

{% code title="Dart" %}
```dart
// Dart
Luciq.init(
  token: "token",
  invocationEvents: [],
  appVariant: "variant", // sets the app variant
);
```
{% endcode %}

#### Controlling Auto Targeting

You can have auto targeting surveys shown automatically at the start of a user's session or show them manually.

**Showing Automatically**

By default, a survey will automatically be presented to users who meet your conditions in their first session after you publish the survey within 10 seconds of opening your app. If you have multiple surveys running and a user meets the conditions for more than one survey, they will be shown each survey one by one.

**Showing Manually**

You can also customize when you want to show your auto-targeting surveys. To do this, first disable automatic showing using the following API:

{% code title="" %}
```dart
Surveys.setAutoShowingEnabled(false);
```
{% endcode %}

Then, present the surveys using the APIs below.

To get all available surveys (each returned survey has getTitle() and show() methods):

```dart
final titles = Surveys.getAvailableSurveys();
```

To show any of the available surveys to the user:

```dart
Surveys.showSurveyIfAvailable();
```

Auto-targeting surveys are shown once only, unless specified otherwise in the targeting section of the survey.

#### Targeting Through CSV

If you'd like to target a list of specific user emails, you can upload a CSV in the targeting step. Requirements:

* Each email should be in a separate row.
* No more than 100,000 entries.
* File size less than 5 MB.

Once the file is uploaded, the dashboard will take care of the rest.

### Manual Targeting Surveys

You can also use **Manual Targeting** to show your surveys to specific audiences, and these surveys can be re-shown any number of times.

Each created survey has a unique token that you can refer to in your code, as explained below.

#### Controlling Manual Targeting Surveys

When you want to target your surveys to specific users (for example, only users who opt-in), manually targeted surveys might be the best method. Use the following API to show a survey with a specific token:

{% code title="Dart" %}
```dart
Surveys.showSurvey("TOKEN");
```
{% endcode %}

You can also check if a specific user has responded to a survey through this API:

{% code title="Dart" %}
```dart
final hasResponded = Surveys.hasRespondedToSurvey("SURVEY_TOKEN");
```
{% endcode %}

This API is particularly useful since you can manually show a survey multiple times to the same user.
