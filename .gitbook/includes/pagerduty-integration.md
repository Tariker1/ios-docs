---
title: pagerduty-integration
---

## Setting up the integration

{% stepper %}
{% step %}
### Create a Custom Event Transformer in PagerDuty

To set up your PagerDuty integration, create a Custom Event Transformer in PagerDuty, which will allow you to map Luciq events to a PagerDuty Incident.

Link: https://developer.pagerduty.com/docs/ZG9jOjExMDI5NTc5-custom-event-transformer
{% endstep %}

{% step %}
### Edit the transformer code

Once the Custom Event Transformer is created, edit the code portion to look something like this (feel free to change this to customize it for your needs):

{% code title="transformer.js" %}
```javascript
var body = PD.inputRequest.body

var normalized_event = {
  event_type: PD.Trigger,
  description: `Luciq | ${body.application} | ${body.trace} ${body.trigger_operator}`,
  details: PD.inputRequest,
  client: "Luciq",
  client_url: body.url
};

PD.emitGenericEvents([normalized_event]);
```
{% endcode %}
{% endstep %}

{% step %}
### Add the PagerDuty webhook URL

Simply add the PagerDuty webhook URL to which Luciq should forward your alerts.

![](<../assets/e79f17e9bf9c33fe52c0c8fe2cb8c4d3bb4778494a6368f9db7ab26860ef433e pagerduty 2.png>)
{% endstep %}

{% step %}
### Test the integration

At this point, test your integration so that you're sure everything is working smoothly.

![](<../assets/500f0adf262fb69b90d5378ef6207016741413d815e2aaa6860a08455504b7fa pagerduty 1.png>)
{% endstep %}

{% step %}
### Finish and name your integration

All done! Your integration is now set up — give your integration a name and you're ready to go.

![](<../assets/a8c28177eb8b5e84f65f5c18e1e31d984649ebfc39b6fd54dbadfa8c0159af9a pagerduty 3.png>)
{% endstep %}
{% endstepper %}

## JSON model

{% code title="JSON" %}
```json
{
  "application": "String", // Luciq App Name, 
  "platform": "String", // the App Platform (IOS, ...)
  "title": "String", // Rule title
  "app_version": "String", // The App Version, Example: 1.0.1,...
  "metric": "String", //the Metric that the incident is related to, Example: Screen Loading, App Launches, ..
  "trace": "String", //Crash Cause: exception name, Filename, and line, or Group name example Hot/cold App Launch
  "trigger": "String", // The Alert Trigger, Example: Crash-free sessions in the last 24 hours
  "trigger_operator": "String", // [Tigger] + [Tigger operator] + [Trigger value] + [Time frame]
  "conditions": [ //[Alert conditions] 
    {
      "key": "String",
      "operator": "String",
      "value": "String"
    }
  ],
  "conditions_operation": "String", // the conditions are ANDed or ORed
  "current_value": "String",// the Actual value of the metric at the time of the incident
  "url": "String" // in case the rule is a crashes rule, URL will be the Crash URL, other wise it will be the incident url
}
```
{% endcode %}
