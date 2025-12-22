---
description: >-
  Capture the time it takes for your Flutter widgets to load and identify slow
  loading widgets.
icon: spinner-scale
---

# Setup Screen Loading

Luciq records the time it takes your widgets to load from the start `init()` method until the completion of the `build()` method, which marks the screen being fully rendered and visible on the screen.

A visualization of Flutter’s screen loading and rendering process showing the points at which Luciq marks the start and end of screen loading.

### Features

#### Spans

Luciq automatically captures all network calls and iOS database queries your app makes during your widget loading. Analyzing the latency of these APIs can help you find root causes for a slow screen loading.

{% hint style="success" %}
Pro Tip: You can click on any network trace in the spans table to view the full details of that network call!
{% endhint %}

#### Patterns

Your screen loading data is automatically segmented by various user and device attributes. Comparing your loading performance across these different dimensions can help you spot if specific segments of your user base are facing issues or help you reproduce the issue during debugging.

You can drill down into any segment by quickly adding it as a filter or viewing all occurrences of that segment. If you hover over any dimension, quick actions for adding it to filter or seeing all occurrences appear.

#### Occurrences

If you prefer to view individual occurrences, you can click “View Occurrences” to see all occurrences of screen loading. You can see the details of the individual occurrence such as latency, app version, device, etc., and a span timeline that shows all the network occurrences recorded during the loading.

### Instrumentation

The instrumentation required depends on the navigator used by your app.

Luciq supports automatic (one per app) instrumentation for some navigation methods. There is also a manual approach you can use for any non-supported navigation methods/libraries.

The following navigators support the one-time instrumentation:

* [Navigator 1.0 (Named Routes)](setup-screen-loading.md#navigator-10-named-routes)
* [Flutter Modular](setup-screen-loading.md#flutter-modular)

For any other navigators, see the [manual instrumentation](setup-screen-loading.md#manual-instrumentation).

{% hint style="warning" %}
We’re working to support more navigators automatically.

If you’d like us to support your navigation method in the future, please reach out to our support team and let us know what navigator you use.
{% endhint %}

#### Navigator 1.0 (Named Routes)

If you’re using the default Flutter Navigator 1.0 and named routes, you'll need to:

{% stepper %}
{% step %}
#### Add the navigation observer

Add the `LuciqNavigatorObserver()` to your app’s `navigatorObservers`.
{% endstep %}

{% step %}
#### Wrap your routes

Wrap your routes in the `APM.wrapRoutes()` wrapper. This will allow the Luciq SDK to automatically capture all the screens defined in your named routes.

If you want to exclude certain routes from being captured, add the `exclude:[]` parameter to `APM.wrapRoutes()`, which takes a list of strings marking route names you want excluded.
{% endstep %}
{% endstepper %}

Here’s an example:

{% code title="Dart" %}
```dart
MaterialApp(
  navigatorObservers: [LuciqNavigatorObserver()], // Our navigation observer
  routes: APM.wrapRoutes({ // The routes wrapper
    '/': (context) => HomePage(),
    '/settings': (context) => SettingsPage(),
    '/profile': (context) => ProfilePage(),
    '/traffic': (context) => TrafficPage(),
  }, exclude: ['/', '/traffic']), // Excluded routes
  ...
)
```
{% endcode %}

The screen loading time of wrapped screens will be captured automatically when you push it to the navigation stack:

{% code title="Dart" %}
```dart
Navigator.pushNamed(context, "/settings");
```
{% endcode %}

#### Flutter Modular

If you’re using the [Flutter Modular v5](https://pub.dev/packages/flutter_modular), you need to install the [Luciq Flutter Modular package](https://github.com/Luciq/luciq_flutter_modular).

{% stepper %}
{% step %}
#### Installation

Add `luciq_flutter_modular` to your `pubspec.yaml` file.

{% code title="YAML" %}
```yaml
dependencies:
  luciq_flutter_modular:
```
{% endcode %}

Then install the package:

{% code title="Shell" %}
```bash
flutter pub get
```
{% endcode %}
{% endstep %}

{% step %}
#### Instrumentation

Wrap your main `module:` in the `LuciqModule()` wrapper in the `main()` method:

{% code title="Dart" %}
```dart
void main() {
  ...
  runApp(
    ModularApp(
      module: LuciqModule(AppModule()), // Our Wrapper
      child: const MyApp(),
    ),
  );
}
```
{% endcode %}

Add the `LuciqNavigatorObserver()` to your App’s `router()` in your `main()` method:

{% code title="Dart" %}
```dart
@override
Widget build(BuildContext context) {
  return MaterialApp.router(
    routeInformationParser: Modular.routeInformationParser,
    routerDelegate: Modular.routerDelegate
      ..setObservers([LuciqNavigatorObserver()]), // Our navigator observer
    title: 'Flutter Modular Demo',
    ...
  );
}
```
{% endcode %}

The Luciq SDK will automatically capture all screens within the wrapped module.
{% endstep %}
{% endstepper %}

#### Manual Instrumentation

If you’re using any other navigation method, you can measure the loading of any widget in your app by wrapping it in the `LuciqCaptureScreenLoading` widget during navigation as shown below:

{% code title="Dart" %}
```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const LuciqCaptureScreenLoading( // Our wrapper
      screenName: SecondScreen.screenName,
      child: SecondScreen(),
    ),
    settings: const RouteSettings(name: SecondScreen.screenName), // should match the [screenName] property
  ),
);
```
{% endcode %}

{% hint style="info" %}
The `screenName` property of `LuciqCaptureScreenLoading` needs to match the route name specified in the `RouteSettings`.
{% endhint %}

### End Screen Loading

If you don’t want to consider the screen “loaded” until after a specific point (e.g. a specific element loading or a splash screen ending), you can extend the screen loading capture time beyond the default definition:

{% code title="Dart" %}
```dart
APM.endScreenLoading();
```
{% endcode %}

### Disable/Enable Screen Loading

If APM is enabled, our SDK starts collecting data about your screen loading time by default. If needed, you can toggle this on and off after the SDK is initialized:

{% code title="toggle_screen_loading.dart" %}
```dart
APM.setScreenLoadingEnabled(boolean);
```
{% endcode %}
