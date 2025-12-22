---
description: Covered here are APIs relevant to crash reporting for your Flutter app.
---

# Reporting Crashes

{% hint style="info" %}
It is highly recommended to mention in your privacy policy that you may be collecting logging data in order to assist with troubleshooting crashes.
{% endhint %}

### Flutter Crash Types

{% stepper %}
{% step %}
#### Fatal Crash

Fatal crashes refer to an error or issue that causes the app to terminate unexpectedly, meaning the app completely shuts down and is no longer usable until the user restarts it. These crashes interrupt the user experience, as the app cannot recover from the issue on its own and must be relaunched.

Fatal crashes are the most severe type of crashes, and they generate crash reports that help developers investigate what caused the app to crash. Typically, they occur due to unhandled errors, system conflicts, or serious resource issues.

Here are the types of fatal crashes:

* Dart exceptions: Crashes caused by unhandled exceptions in Dart code, which is the primary language used for Flutter development. Examples include NoSuchMethodError, StateError, or FormatException.
* Platform-specific crashes: Since Flutter apps often interact with native Android and iOS layers, crashes originating from the platform side (iOS or Android) can also occur. These would be categorized under native iOS or Android crash types (e.g., signal-based crashes for iOS or ANRs for Android).
{% endstep %}

{% step %}
#### ANR (Application Not Responding)

When the main thread is blocked for too long, leading to an ANR error. This is an Android-specific type where the system prompts the user to either wait or force close the app.
{% endstep %}

{% step %}
#### OOM

Out-of-memory crashes occur when the app uses more memory than the device can provide, causing the system to terminate the app to free up resources. Common causes of OOM crashes include:

* Memory leaks
* Heavy resource usage
* Retaining too many objects
{% endstep %}

{% step %}
#### Non-Fatal

Non-fatal crashes refer to an error or issue that occurs in the app but doesn’t cause the app to completely shut down or crash. Instead, the app encounters a problem, such as an exception or unexpected behavior, but is able to continue running without quitting. Non-fatal crashes are useful for developers because they provide insights into bugs or problems that need fixing before they turn into full-blown crashes.
{% endstep %}
{% endstepper %}

With Luciq [Crash Reporting](https://www.luciq.ai/product/crash-reporting) there are two ways to have your application report a crash, either automatically or manually. After the crash is sent to your dashboard, you can sort and filter for specific crashes easily.

### Automatic Crash Reporting

If you enable Crash Reporting, crashes will automatically be reported to and viewable from the crashes page of your Luciq dashboard.

You'll also see the trends covering the previous 7 days, including:

* Crash-free sessions: the percentage of sessions that ran and concluded without any fatal errors.
* Crash-free users: the percentage of users that haven't encountered any fatal errors.
* Crashing sessions: the number of sessions that ran and concluded with a fatal error.
* Affected users: the number of unique users who had one or more sessions that ended with a fatal error.
* Total number of occurrences: by hovering on it, you’ll get a breakdown of the number of fatal sessions, the number of OOM sessions, the number of ANR sessions, and the number of non-fatal sessions.

If there is a sharp decline in the crash-free sessions rate, an email will be sent to notify you.

{% hint style="warning" %}
Crash reporting will not function correctly if the device is connected to Xcode. When it is, Xcode catches all the exceptions and they will not be sent to your dashboard.
{% endhint %}

#### Setting Up Automatic Crash Reporting

You'll need to follow the below step in order to turn on automatic crash reporting in our Flutter SDK. Replace `void main() => runApp(MyApp());` with the following snippet:

{% code title="Dart" %}
```dart
void main() {
  runZonedGuarded(() {
    WidgetsFlutterBinding.ensureInitialized();
    Luciq.init(
      token: 'APP_TOKEN',
      invocationEvents: [InvocationEvent.floatingButton],
    );
    FlutterError.onError = (FlutterErrorDetails details) {
      Zone.current.handleUncaughtError(details.exception, details.stack!);
    };
    runApp(MyApp());
  }, CrashReporting.reportCrash);
}
```
{% endcode %}

{% hint style="warning" %}
Crashes will only be reported in release mode and not in debug mode.
{% endhint %}

### Manual Crash Reporting

You can offer your users Luciq [Bug Reporting](https://www.luciq.ai/product/bug-reporting) to report bugs. However, you can use the following method and API to manually report any error or exception that you handle in your code and assign it a severity level.

#### Report Exception

To report exceptions manually, use the following method:

{% code title="Dart" %}
```dart
CrashReporting.reportHandledCrash(error, stackTrace);
```
{% endcode %}

{% hint style="info" %}
Min Required SDK version: Customizing crash level and custom grouping is supported starting Flutter SDK v13.1.1.
{% endhint %}

#### Add Level to Exception

You can set different severity levels for manually reported exceptions using the following API:

{% code title="Dart" %}
```dart
try {
  throw Exception();
} catch (exception, stacktrace) {
  CrashReporting.reportHandledCrash(exception, stacktrace,
    level: NonFatalExceptionLevel.critical);
}
```
{% endcode %}

Here are the different severity levels available. In case no level is indicated, the default level would be error.

{% code title="Dart" %}
```dart
NonFatalExceptionLevel.info;
NonFatalExceptionLevel.error;
NonFatalExceptionLevel.warning;
NonFatalExceptionLevel.critical;
```
{% endcode %}

#### Grouping

When an already existing crash occurs once more for any user, that crash is reported as an occurrence in the original entry. However, in order to calculate whether a crash already exists and needs to be grouped, Luciq generates a fingerprint based on attributes used in the grouping logic.

The default Luciq grouping algorithm uses a mix of the exception and stack trace information. In some cases, you might want to change how the issues are grouped together using fingerprints.

#### Custom Fingerprinting

{% hint style="warning" %}
Please note that using custom fingerprinting will override Luciq's default grouping by sending a fingerprint string.
{% endhint %}

In the event that you'd like to report the exception manually with a custom grouping fingerprint in mind, you can use the below API:

{% code title="Dart" %}
```dart
try {
  throw Exception();
} catch (exception, stacktrace) {
  CrashReporting.reportHandledCrash(exception, stacktrace,
    userAttributes: userAttributeMap,
    fingerprint: 'grouping fingerprint',
    level: NonFatalExceptionLevel.info);
}
```
{% endcode %}

### Crashes List

This section contains a list of all the crashes that have been reported by your application. The title of each crash is usually the most significant line in the stack trace.

Next to each crash in the list, you can find the following details, all of which can be used to sort the crashes:

* Occurrences: The number of times this crash has occurred and a bar graph representing its occurrences over the past seven days.
* Users: The number of users affected by this crash.
* Min ver.: The oldest app version that was affected by this crash.
* Max ver.: The latest app version that was affected by this crash.
* Last seen: The last time an occurrence of this crash was reported.

You can then filter for crashes that match any of the following criteria:

* App version
* Date
* Device
* OS
* User attributes
* Type
* Status
* Assignee
* Team
* Tags
* Current view
* Experiments
