---
title: webhook-integration
---

## Setting up the Integration

{% stepper %}
{% step %}
## Add your Webhook URL

To set up your Webhook integration, add the link to which Luciq should forward your reports. You can also choose which details get forwarded.

![](<../assets/a35b8b313157576ba326297abeacde5323a9f6e7894d80e5ede5d3d902a5664a integrations webhook 2.png>)
{% endstep %}

{% step %}
## Select products and test

Select the products that you would like to integrate with, whether Bugs & Crashes or APM, and test your integration so that everything is working smoothly.

![](<../assets/3dbd97637fcce7903cb178dc332392c13a39499f2dca7e1bc699f9ec2c242a93 integrations webhook 4.png>)
{% endstep %}

{% step %}
## Finish and enable forwarding

All done! Your integration is now set up and ready. From this final page, you can allow automatic forwarding (this can be reconfigured at any time).

![](<../assets/df4f62575c778bff8c4f6045c3e88e83ab60cf40481ffd7c2688a4bb4afa1470 integrations webhook 3.png>)
{% endstep %}
{% endstepper %}

Below, you can find more details about the JSON payloads that you will receive.

## Crashes' JSON model:

{% code title="JSON" %}
```json
{
    "Exception": "String",
    "Number": "Number",
    "URL": "String",
    "Status": "String",
    "Email": "",
    "Reported At": "String",
    "Location": "String",
    "Device": "String",
    "Memory": "String",
    "Storage": "String",
    "Connectivity": "string",
    "Battery": "string",
    "App Version": "string",
    "Duration": "number",
    "User Data": "String",
    "Console Log": "Text",
    "Luciq Log": "Text",
    "User Steps": "Text",
    "User Attributes": {},
    "Current View": "String",
    "Locale": "en_US",
    "Orientation": "landscape",
    "Screen Size": "String",
    "Density": "string",
    "Image Attachments": []
}
```
{% endcode %}

## Bugs' JSON model:

{% code title="JSON" %}
```json
{
  "Title": "String",
  "Reported At": "String",
  "Email": "String",
  "Private URL": "String",
  "Categories": "String",
  "Tags": "String",
  "App Version": "String",
  "Device": "String",
  "Location": "String",
  "Duration": Integer,
  "Screen Size": "String",
  "Density": "String",
  "User Attributes": {

  },
  "User Data": "String",
  "User Steps": "String",
  "Luciq Log": "String",
  "Console Log": "String",
  "Locale": "String",
  "Image Attachments": [

  ],
  "Non Image Attachments": [

  ],
  "Type": "bug",
  "URL": "String"
}
```
{% endcode %}

## APMs' JSON model:

{% code title="JSON" %}
```json
{
  "title": "String",
  "trace": "String",
  "trigger": "String",
  "trigger_operator": "String",
  "test_value": "Number",
  "duration": "String",
  "conditions": [
    {
      "key": "String",
      "operator": "String",
      "value": "String"
    }
  ],
  "current_value": "String",
  "metric": "String",
  "application": "String",
  "platform": "String",
  "url": "String"
}
```
{% endcode %}

## Using Secret Tokens

Ensure your server is only receiving the expected Luciq requests for security reasons.

{% stepper %}
{% step %}
## Creating a secret

Create a random alphanumeric secret that’s at least 16 characters and has a maximum of 64 characters.

Here’s a sample secret: `d8yyxj7srjqf5xyih8ay`

Note: please make sure to save this secret.
{% endstep %}

{% step %}
## Bind the secret with Webhooks

Create a Webhook integration on Luciq then enter the secret you created in the **“Secret token”** field.

![](<../assets/91621a5ed92316b03532b5a2f58b024933e688f005daaa0394449a6d46220203 integrations webhook 1.png>)
{% endstep %}

{% step %}
## Save the integration

After saving the integration, each request that is sent from this integration will have an extra field in the header called `x-lcq-signature-256`.
{% endstep %}

{% step %}
## Authenticate incoming requests

Once your server receives the response from Luciq, do the following:

* Hash the response body using the Secret token you created.
* Use the sha256 algorithm for hashing.
* Compare the result of the hash with the header `x-lcq-signature-256`.
{% endstep %}

{% step %}
## Verify the signature

* If the results are equal, then it means it’s sent from Luciq.
* If they are not equal, then it’s not sent from Luciq.
{% endstep %}
{% endstepper %}
