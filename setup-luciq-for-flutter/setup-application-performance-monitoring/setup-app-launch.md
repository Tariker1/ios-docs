---
description: >-
  This page covers Luciq's app launch definition, its apdex calculation, how to
  set your custom target, and all the details you need to know about the app
  launch metric on your Flutter apps.
icon: rocket-launch
---

# Setup App Launch

Luciq automatically measures your **cold app launch** latency, which is the time between when your user launches the app from scratch and when it is responsive and accepting touch events.

***

### End App Launch

If you'd like to define a specific point in time where the app launch can be considered complete (for example, when the app is actually interactable), you can use the End App Launch API to set that point. You will then see this data alongside the automatic cold and hot app launches that were captured.

To use the End App Launch API, call:

{% code title="APM.endAppLaunch()" %}
```dart
APM.endAppLaunch()
```
{% endcode %}

### How Is The App Launch Time Calculated?

**iOS**

It starts with the process start time and stops by the end of the first run loop. This interval accounts for any launch-blocking logic in your code as well as the time before your app classes are loaded. It includes loading dynamic frameworks and resolving any dynamic references made in the binary.

**Android**

It starts after Luciq's `ContentProvider` is created and ends when `onActivityResumed()` is called for the first time.

### App Launch Apdex

Luciq calculates an Apdex score for your app launch that reflects how satisfying your app launch time is. Your Apdex score ranges between 0 and 1; a higher value means better performance and, hence, a better user experience:

* Apdex score ≥ 0.94 — **Excellent**
* Apdex score ≥ 0.85 and < 0.94 — **Good**
* Apdex score ≥ 0.7 and < 0.85 — **Fair**
* Apdex score ≥ 0.5 and < 0.7 — **Poor**
* Apdex score < 0.5 — **Unacceptable**

#### How Is The App Launch Apdex Calculated?

When an app launch occurrence is collected, it is flagged based on a pre-defined target (T). An app launch occurrence is considered:

* **Satisfying:** duration ≤ T
* **Tolerable:** duration > T and ≤ 4T
* **Frustrating:** duration > 4T

Based on the bucketing above:

* Total occurrences = Satisfying occurrences + Tolerable occurrences + Frustrating occurrences
* Apdex score = (Satisfying occurrences + 0.5 \* Tolerable occurrences) / Total occurrences

#### How Can You Control Your App Launch Target?

By default, the target is set to **0.5 seconds**; however, you can change this number from your dashboard. You can also control whether Cold App Launch affects your app apdex from the dashboard.

{% hint style="info" %}
Please note that updating your app launch target does **not** affect already stored occurrences — only future occurrences will be flagged using the new target.
{% endhint %}

***

### Disabling/Enabling App Launch Tracking

If APM is enabled, the SDK starts collecting app launch time data by default. To toggle collection after the SDK is initialized, call:

{% code title="Dart" %}
```dart
// Enable Cold App Launch
APM.setColdAppLaunchEnabled(true);
```
{% endcode %}

{% code title="Dart" %}
```dart
// Disable Cold App Launch
APM.setColdAppLaunchEnabled(false);
```
{% endcode %}
