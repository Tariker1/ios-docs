# Updating The SDK

{% stepper %}
{% step %}
#### Update the version in pubspec.yaml

Modify the `luciq_flutter` dependency version in your `pubspec.yaml`.

Before:

{% code title="YAML" %}
```yaml
luciq_flutter: ^18.0.0
```
{% endcode %}

After:

{% code title="YAML" %}
```yaml
luciq_flutter: ^19.0.0
```
{% endcode %}
{% endstep %}

{% step %}
#### Install the updated dependency

Run the following command to fetch the new SDK version:

{% code title="Shell" %}
```bash
flutter pub get
```
{% endcode %}
{% endstep %}
{% endstepper %}
