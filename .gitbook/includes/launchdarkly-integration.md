---
title: launchdarkly-integration
---

## Integrate Luciq with Launchdarkly

With the integration, you will be able to monitor and control your feature flags from within Luciq in addition to various automations that can be set up on feature flags.

## SDK Setup

Whenever you use a feature flag in Launchdarkly, make sure to call Luciq’s addFeatureFlag API, explained here. This ensures that any feature flags in any session are correctly counted and monitored from both within Luciq and Launchdarkly.

Example of the code snippet

{% code title="Kotlin" %}
```kotlin
LDClient.init(application, ldConfig, context)

// Boolean flag
val BOOLEAN_FLAG_KEY = "sample-flag"

val featureEnabled = LDClient.get().boolVariation(BOOLEAN_FLAG_KEY, false)
if (featureEnabled) {
    Luciq.addFeatureFlag(LCQFeatureFlag(BOOLEAN_FLAG_KEY))
    // logic to execute if flag enabled
} else {
    Luciq.removeFeatureFlag(BOOLEAN_FLAG_KEY)
}

// Multivariats flag
val STRING_FLAG_KEY = "sample-string-flag"

val stringFlag = LDClient.get().stringVariation(STRING_FLAG_KEY, null)

if (stringFlag != null) {
    Luciq.addFeatureFlag(LCQFeatureFlag(STRING_FLAG_KEY, stringFlag))
} else {
    Luciq.removeFeatureFlag(STRING_FLAG_KEY)
}
```
{% endcode %}

Another approach would be using the following snippet which allows Luciq to listen to all feature flags coming of Launchdarkly’s client. However, this may result in inaccurate data if you are not using the same enabled feature flags in you code.

{% code title="Kotlin" %}
```kotlin
LDClient.init(application, ldConfig, context)
// Get all mobile enabled feature flags
for ((key, value) in LDClient.get().allFlags()) {
    if (value.type == LDValueType.BOOLEAN && value.booleanValue()) {
        Luciq.addFeatureFlag(LCQFeatureFlag(key))
    } else if (value.type == LDValueType.STRING || value.type == LDValueType.NUMBER) {
        Luciq.addFeatureFlag(LCQFeatureFlag(key, value.toString().replace("\"", "")))
    }
}
```
{% endcode %}

## Dashboard Setup

Within the Settings tab, you will find Launchdarkly integration in the list of integrations available.

{% stepper %}
{% step %}
### Add Launchdarkly integration token

Get your launchDarkly integration token and add it.

![](<../assets/4f19d3e3176e0ec965b263572bc196eb5b6cbda212c10e82c9f81bd75c77092a integrations launchdarkly 5.png>)
{% endstep %}

{% step %}
### Select project and environment

Select your project and environment that you want to control feature flags in.

![](<../assets/5809af15b4496009286ac29ab1d8f745ab3690931eaf698e3c7c467001045412 integrations launchdarkly 2.png>)
{% endstep %}

{% step %}
### Test your integration

At this point, we just need to test your integration so that we're sure everything is working smoothly.

![](<../assets/559c6c3fc8eef8cba129e39ebadcc45114c5eaaafeee42030227b42ae767be45 image.png>)
{% endstep %}

{% step %}
### Name and finish

All done! Your integration is now set up, just give your integration a name and you're ready to go.

![](<../assets/3c54937ef5d2adabe58534fcff9ad051e0795b5462d0f993a49743d399087781 image.png>)
{% endstep %}
{% endstepper %}

## Control Feature Flags

After the setup, you can now create rules on a specific feature flag to turn it off whenever it passes a certain threshold of a specific metric.

![](<../assets/939d298ed5b9591ab0051dedab90879fe503a0fd3a6a33bff7607b4fb95186ee image.png>)

{% hint style="info" %}
Notes:

* To use the action of Turn off using Launchdarkly, you must add a condition of feature flag names.
* The action of Turn off using launchdarkly sends a value of OFF to Launchdarkly for the specific feature flag that passed the threshold added.
{% endhint %}

## Get Launchdarkly API token

{% stepper %}
{% step %}
Go to Settings → Authorization page: https://app.launchdarkly.com/settings/authorization

From Access Tokens section, click create token.

![](<../assets/258f6464ac081851fc9b84e43b3439e31f11466ef1b51cad8308352b77d0a229 image.png>)
{% endstep %}

{% step %}
Enter the integration name, make sure to select Writer role, and select API version to 20240415, then Save.

![](<../assets/83eb7ce image.png>)
{% endstep %}

{% step %}
Copy the generated token before leaving the page, to use it in integration step.
{% endstep %}
{% endstepper %}
