# Support Tools Integration

To debug support tickets effortlessly, all you have to do is extract the session URL from Luciq and send it as a custom attribute to your preferred support tools. This enables your support team to view Session Replays for every reported issue to help debug the issue. You can use the below API to extract the session URL.

{% tabs %}
{% tab title="Dart" %}
```dart
SessionReplay.getSessionReplayLink();
```
{% endtab %}
{% endtabs %}

#### Intercom Example

To automatically include the Session URL with each support ticket received via Intercom, simply integrate the following code snippet into your application. This will send the session URL to the recent events section.

{% tabs %}
{% tab title="Dart" %}
```dart
 final result = await SessionReplay.getSessionReplayLink();
    if (result != null) {
      await Intercom.instance.loginUnidentifiedUser();
      await Intercom.instance.logEvent('session-replay-url', {"url": result});
    }
```
{% endtab %}
{% endtabs %}
