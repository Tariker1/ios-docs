---
title: jira-cloud
---

## [Jira Cloud](https://luciq.ai/integrations/jira)

Allow your users and beta testers to report bugs and send feedback directly from your app and have them automatically logged into your Jira project. Luciq offers a **two-way integration** when the integration is done through Jira, meaning that the status and comments on the Jira ticket will also be reflected on the bug report on your Luciq dashboard.

### Through Jira Add-On

{% stepper %}
{% step %}
### Add your Jira board link

To set up your Jira Cloud integration, simply add the link to your Jira board, where you will see your incoming reports.

![](<../assets/f131b4500dbdd3390d9f884fb0ae7ccea77969db3a10aa15ca87df705b164201 integrations jira cloud 1.png>)
{% endstep %}

{% step %}
### Explore apps on your Jira board

On your Jira board, from the Apps section, click on "Explore more apps".

![](<../assets/02089ce7005268435d98482565b1b460246768fd7ac104e9d5f38e1e3cd16f6d integrations jira cloud 2.png>)
{% endstep %}

{% step %}
### Search for Luciq

Search "Luciq" from the search window and click on the add-on.

![](<../assets/46575529c8229378707aff7bc303270639e9162d10a7104a8502a5362849081d image.png>)
{% endstep %}

{% step %}
### Install the Add-On

After selecting our Add-On app, click on the Get App button.
{% endstep %}

{% step %}
### Configure the Add-On

Click on "Configure" which is found within the prompt after installing the add-on from Jira's side.

![](<../assets/120dc1e90ac552753774ca768610133884158d21fa7fb15dbbe2c7f0cdfb1ba3 image.png>)
{% endstep %}

{% step %}
### Login to Luciq

Login using your Luciq dashboard credentials in order to have it synced with your dashboard.
{% endstep %}

{% step %}
### Select project settings

Select the project, issue type, assignee, and any custom fields you have setup.

![](<../assets/871d475e0f9822e4a958ae338979c27cb0c589e2f76551f1e8cb1ef6b13ecb9f integrations jira cloud 5.png>)
{% endstep %}

{% step %}
### Test the integration

At this point, we just need to test your integration so that we're sure everything is working smoothly.

![](<../assets/8a59dbcc230902f3067c485d839e346b6774a1b164d529da9e8f2547963764e6 integrations jira cloud 6.png>)
{% endstep %}

{% step %}
### Finish setup

All done! Your integration is now set up and ready to go. From this final page, you can allow automatic forwarding (this can be reconfigured at any time) as well as synced status.

![](<../assets/19050100f1e47c279860484452b9635ada486037e0eaaaea44ec907ce2e9b095 integrations jira cloud 10.png>)
{% endstep %}
{% endstepper %}

***

## Through Luciq

{% stepper %}
{% step %}
### Enter Jira credentials

Insert your **Jira Email**, **API Token** (which can be retrieved from [here](https://id.atlassian.com/manage/api-tokens)), and **URL**.

![](<../assets/35b45336725fbf8a90988c50c07d9ab4a70b35f011f03382124b50c854fd05f2 integrations jira cloud 7.png>)
{% endstep %}

{% step %}
### Pick project and map fields

Pick the **project** you want to forward to as well as the **assignee**. Fields can be mapped from Luciq to Jira fields. You can also choose which information is forwarded from your Luciq dashboard to Jira.

![](<../assets/20e8fb9c6463031f7aeda35006c523364a8145efbc60b948f96420fabe78f959 integrations jira cloud 8.png>)
{% endstep %}

{% step %}
### Test the integration

At this point, we just need to test your integration so that we're sure everything is working smoothly.

![](<../assets/6f1650b8e6f59ab5420de8c367ac259326e3fcba077800b58a15d5e038f9b340 integrations jira cloud 9.png>)
{% endstep %}

{% step %}
### Finish setup and enable two-way sync

All done! Your integration is now set up and ready to go. From this final page, you can allow two-way integration (if Luciq is already installed on your Jira dashboard) and allow for automatic forwarding (these can be reconfigured at any time).

![](<../assets/19050100f1e47c279860484452b9635ada486037e0eaaaea44ec907ce2e9b095 integrations jira cloud 10.png>)
{% endstep %}

{% step %}
### Start receiving issues

Start receiving issues on the spot on your Jira dashboard.

![](<../assets/7e4876c Jira_Cloud_ _Sample_Bug.png>)

With this integration, bugs and feedback can be converted manually into issues on Jira with just a click.
{% endstep %}
{% endstepper %}

***

## Mapping Custom Fields

This section covers how to map Jira custom fields to fields from the Luciq dashboard.

{% stepper %}
{% step %}
### Create the custom field in Jira

![](<../assets/11df27e 0233a184 ac78 488f a0d5 95d3c4b9f748.png>)
{% endstep %}

{% step %}
## Choose a type

Choose a type for the field you've created in the previous step.

![](<../assets/93c2093 image2.png>)
{% endstep %}

{% step %}
## Reconfigure the Jira integration

Reconfigure your Jira integration.

![](<../assets/7aaaf58 image3.png>)
{% endstep %}

{% step %}
## Map fields

Map the Jira custom fields to the corresponding Luciq fields (make sure they have the same type).

![](<../assets/4317395 image4.png>)
{% endstep %}

{% step %}
### Test your integration

Test your integration.

![](<../assets/b040bc1758503eb2abde05a049c4b694e7f54c45be5f140316f702a31bf6ac25 integrations jira cloud 16.png>)
{% endstep %}

{% step %}
### Finish

All done!

![](<../assets/2cc6a595a2ff998ebc58bf8a401ae1e5f67219e27e2228d4be77651738adf43f integrations jira cloud 17.png>)
{% endstep %}

{% step %}
### Forwarded bug appearance

This is how the forwarded bug report should look on Jira.

![](<../assets/7a41166 image7.png>)
{% endstep %}
{% endstepper %}

***

## Priority Sync

Once you enable two-way sync for the priority, any change done to the priority field in our dashboard will be reflected in Jira and vice versa.

Two-way sync for the priority will only work if you are using the default priorities in Jira. If you are using custom priorities, the bug will be forwarded to Jira successfully, but the priority will not be synced.

### **Priority Mapping**

| Luciq Priorities | Jira Priorities |
| ---------------- | --------------- |
| NA               | Medium          |
| Trivial          | Lowest          |
| Minor            | Low             |
| Major            | High            |
| Blocker          | Highest         |
