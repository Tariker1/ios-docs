---
title: azure-devops-integration
---

{% hint style="info" %}
We only support one-way sync integration with Azure DevOps — changing statuses or assignees on Azure DevOps won't reflect on Luciq.
{% endhint %}

Forward your bug reports to your Azure DevOps workspace by following these simple steps.

{% stepper %}
{% step %}
## Navigate to Integrations

Open Luciq's Settings and go to the Integrations page. Click _Create_ on the Azure DevOps integration.

![](<../assets/4d53ea7 image.png>)
{% endstep %}

{% step %}
## Fill integration form

In the integration form, you'll need to provide:

* PAT Token
* Organization URL

![](<../assets/20aad6a01086100eea355ada5ea806190fa3d6f99034703d4fc9b5efb147c8f3 azure devops 2.png>)
{% endstep %}

{% step %}
## Create a PAT Token (Personal Access Token)

To create a new PAT Token in Azure DevOps:

* Head over to Azure DevOps.
* Click on User Settings from the menu.
* Choose "Personal Access Token", or navigate to this URL:\
  https://dev.azure.com/{ORGANIZATION}/\_usersSettings/tokens

![](<../assets/9ce1ed31d86c29ae19109e5a0f633ff1b2e064b033a0246e8acf2c1cb2ba8ec9 image.png>)
{% endstep %}

{% step %}
## Configure the token

Click on New Token, ensuring the new token has either full access or read-and-write access to work items.
{% endstep %}

{% step %}
## Enter credentials in Luciq

Fill in your PAT Token and Organization URL in the integration form.

![](<../assets/20aad6a01086100eea355ada5ea806190fa3d6f99034703d4fc9b5efb147c8f3 azure devops 2.png>)
{% endstep %}

{% step %}
## Test and create

Test the connection and create your integration.

![](<../assets/1030b583e46613a04d835fbe9cd5c2d81331b4e7782c3095ce5ab6ffc372894c azure devops 5.png>)
{% endstep %}

{% step %}
## Configure forwarding and rules

From the final page you can:

* Choose automatic forwarding of all bug reports or forward manually.
* Set Rules & Alerts based on conditions before forwarding.

![](<../assets/a114a81a8f41b45321db1bc457be1fc4b87cfcfd5fda6828dc83b28f660de9eb azure devops 7.png>)
{% endstep %}
{% endstepper %}
