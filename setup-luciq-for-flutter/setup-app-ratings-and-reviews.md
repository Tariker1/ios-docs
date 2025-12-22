# Setup App Ratings & Reviews

#### &#x20;Custom App Rating Prompt

If you’re using a custom app rating prompt to ask users to rate your app, please make sure to call the below API once the user clicks on the CTA that redirects to the store.

{% tabs %}
{% tab title="Dart" %}
```dart
Luciq.willRedirectToStore();
```
{% endtab %}
{% endtabs %}

When the above API is used, we will be able to detect the suspected sessions for the reviews submitted through the custom prompt. This will give you valuable insights into what happened during the session.
