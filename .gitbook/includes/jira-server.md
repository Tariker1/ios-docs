---
title: jira-server
---

{% stepper %}
{% step %}
Insert your **username**, **password**, and **URL**.

![](<../assets/015983fd0ea3476488e0adfd5520288649bddd826be0bf74b8c5a9d36d79bf3a integrations jira server 1.png>)
{% endstep %}

{% step %}
Pick the **project** you want to forward to as well as the **assignee**. Fields can be mapped from Luciq to Jira fields. You can also choose which information is forwarded from your Luciq dashboard to Jira.

![](<../assets/30fa62c296a4f84faa3078f5da016fbf4f079c8cd3e56e34459167cb703ee288 integrations jira server 2.png>)
{% endstep %}

{% step %}
At this point, we just need to test your integration so that we're sure everything is working smoothly.

![](<../assets/b833799deb758536ee0bd6ae2c38e4c105b0bfa398eaf5193d8731a2cefb69b7 integrations jira server 3.png>)
{% endstep %}

{% step %}
All done! Your integration is now set up and ready to go. From this final page, you can allow automatic forwarding (don't worry, though, these can be reconfigured at any time!)
{% endstep %}

{% step %}
Start receiving issues on the spot on your Jira dashboard.

![](<../assets/4743a8a4da822cfaa875d39eb6b44382c421fd8f20a2814f76915da86b7738f9 integrations jira server 4.png>)

With this integration, bugs and feedback can be converted manually into issues on Jira with just a click.
{% endstep %}
{% endstepper %}

## Mapping Custom Fields

This section covers how to map Jira custom fields to fields from the Luciq dashboard.

{% stepper %}
{% step %}
Create the custom field on Jira

![](<../assets/60a73ad55aa899334da388ae3d8ec997921a1aade14122be97800af312090019 integrations jira server 5.png>)
{% endstep %}

{% step %}
Choose a type for the field you've created in the previous step.

![](<../assets/87af96f2a730e07fe016b145eb0fa40291a843df11d4842d0b8d46096dbebe87 integrations jira server 6.png>)
{% endstep %}

{% step %}
Reconfigure your Jira integration

![](<../assets/737e528b52d4b459701c075bd2f0f034f644b12cef546c64f84c8a416daa850e integrations jira server 7.png>)
{% endstep %}

{% step %}
Map the Jira custom fields to the corresponding Luciq fields (make sure they have the same type).

![](<../assets/5e4710bca20a5ab43468e704e374f358423b05e299f87498638868d4da1ece98 integrations jira server 8.png>)
{% endstep %}

{% step %}
Test your integration

![](<../assets/3703242edba82efb73591b71eb5a921c9138d59a2d840f9d24dd49b4c0113616 integrations jira server 9.png>)
{% endstep %}

{% step %}
Finished — All done!

![](<../assets/189f7d47aff922bb31c3be7b66745e88b89485f23b4d053902c14055e2d438bb integrations jira server 10.png>)
{% endstep %}
{% endstepper %}

## PAT Tokens

PAT stands for Personal Access Token. Use the PAT token, generated from Jira Server, to add a layer of authentication on Luciq ↔︎ Jira Server integration.

Using a PAT token is more secure than authenticating an integration with a username and password.

Setup steps

{% stepper %}
{% step %}
Navigate to your Luciq dashboard.
{% endstep %}

{% step %}
Navigate to your app’s Settings page.
{% endstep %}

{% step %}
Navigate to the Integrations tab.
{% endstep %}

{% step %}
Launch a new Jira Server integration wizard.
{% endstep %}

{% step %}
Toggle from Basic Authentication to PAT Token
{% endstep %}

{% step %}
Enter your PAT Token and Jira Site URL.

![](<../assets/cbda8e4 image.png>)
{% endstep %}

{% step %}
Navigate to [this link](https://confluence.atlassian.com/enterprise/using-personal-access-tokens-1026032365.html) to create a PAT Token on Jira.
{% endstep %}

{% step %}
Copy the created PAT Token to the PAT Token field on Luciq’s wizard.
{% endstep %}

{% step %}
Continue setting up the integration normally.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
## Limitations

* Token Expiry:
  * The token expiry date is controlled from the Jira side, not from Luciq.
  * If a token is created with a specific expiry date, it must be updated on Luciq’s dashboard before expiry, otherwise, there is a risk of not forwarding some data between Luciq and Jira during the period of non-validity of the PAT Token provided until it’s updated.
{% endhint %}

### Editing Current Integrations

Currently, editing already existing integrations is not supported so a new one will need to be created.
