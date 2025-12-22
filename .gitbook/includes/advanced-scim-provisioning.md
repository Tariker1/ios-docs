---
title: advanced-scim-provisioning
---

{% hint style="info" %}
To enable role and app access mapping during user provisioning, you will need to create a custom attribute for Instabug application integration on OKTA.
{% endhint %}

## Setting up custom attributes

{% stepper %}
{% step %}
### Login to OKTA admin console
{% endstep %}

{% step %}
### Navigate to Directory > Profile Editor

Click Instabug User

<figure><img src="../assets/image (44).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Click on +Add mappings
{% endstep %}

{% step %}
### Create a custom attribute for role mapping

Follow the following configurations:

1. Data type = String
2. Display name = Instabug Role
3. Variable name = instabugRole
4. Check the “Enum” box
5. Add a list of Instabug roles

<figure><img src="../assets/image (45).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Create a custom attribute for application access

Follow the following configurations:

1. Data type = String
2. Display name = Instabug Applications
3. Variable name = instabugApplications
4. \[Optional] Check the “Enum” box
5. \[Optional] Add a list of your Luciq app names – Must be exact names

<figure><img src="../assets/image (47).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure attribute mappings for Luciq user:

1. After clicking Save
2. Click Mappings
3. Then click OKTA User to Instabug

<figure><img src="../assets/image (48).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### From the drop-down – Choose InstabugRole

<figure><img src="../assets/image (49).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Repeat the previous step for InstabugApplications
{% endstep %}
{% endstepper %}

***

## Assigning Roles and App Access To Users

* After completing the configuration successfully, when you add a new user to Luciq for provisioning, you will be prompted to select the Role and Application access for each user.
* These attributes will be optional.
* Go to Applications
* Select Instabug
* Click on Assign > Assign to People
* Select a user to add then click assign
* Select Role from dropdown
* Select Apps to assign to the user

<figure><img src="../assets/image (50).png" alt=""><figcaption></figcaption></figure>
