---
title: datadog-integration
---

## Visualize Luciq App Health in Datadog

Easily monitor your app’s performance and stability directly within Datadog by using our prebuilt **Luciq Blueprint**. This guide walks you through setting up the integration via HTTP, allowing you to visualize app health metrics like crash-free sessions, frustration-free sessions, and more.

![](<../assets/6ae541275ec409443348d753c747bee93607cc358ba08f6320ef2be7aa0fb2c5 datadog 1.png>)

### 📌 Prerequisites

* A Datadog account with access to **App Builder**.
* An Luciq account with access to your project's **App Health dashboard**.
* Luciq API token and email (reach out to [support@luciq.ai](mailto:support@luciq.ai) to obtain these).

### 🛠️ Steps to Set Up the Integration

{% stepper %}
{% step %}
## Navigate to App Builder

From the left-hand navigation in Datadog, go to **Actions > App Builder**.

![](<../assets/47f7439d60bdc1d2f7eb5dab895d678b237dc77de43bf014b7721d981144e3cd Screenshot_2025 05 11_at_4.56.35_PM.png>)
{% endstep %}

{% step %}
## Select “Blueprints”

Click on the **Blueprints** tab at the top to access available integrations.

![](<../assets/fa43a69cf43bf907ee064d61fe61d0f3b7bd94e3442f1bb4ad7bd5ff443aeb7b image 20250511 135553.png>)
{% endstep %}

{% step %}
## Search for Luciq

In the search bar, type **Luciq** and select the blueprint titled **Explore Luciq Sessions**.

![](<../assets/1e470c1f6e07b3e744e8bd48ab2667a8967dee4e57faf14aa024b65bc90146b1 image 20250511 135702.png>)
{% endstep %}

{% step %}
## Click “Set up your connection”

Click the blueprint card to open the editor. On the left side, select **New Connection**.

![](<../assets/f8ced529ef256637f8210c41dc11cfedc9f1a04a82135786baab1b6d2e3d945a image 20250511 135716.png>)
{% endstep %}

{% step %}
## Choose HTTP Connection

Select **HTTP Connection** as the integration method.

![](<../assets/be8d15672ed09c14ba2e26ba5552979045dfacf766863bc99380d3c966f980b3 image 20250511 135800.png>)
{% endstep %}

{% step %}
## Fill in Connection Details

In the modal, enter the following:

* **Base URL**: `https://dashboard-api.instabug.com`
* **Authentication Type**: `Token Auth`
* Add two token fields:
  * `token` → Luciq API token
  * `email` → Your registered Luciq email
* Then under **Request Headers**, add:\
  `authorization: Token token="{{ token }}", email="{{ email }}"`

![](<../assets/47ba0dba2c3815df3213b4ed2e804ef58e9519fb2ca269e453063a8237729a6b image 20250511 135832.png>)

Click **Next, Confirm Access**.
{% endstep %}

{% step %}
## Set Access Permissions

Choose who can access this connection (e.g., only you, the org, or a team), then click **Create**.

![](<../assets/30ff06ae47dd834282837a679dc4175bb501c131965c3ee3c7941ef35b938b0d image 20250511 135904.png>)

You should now see a success message indicating the connection was created.
{% endstep %}
{% endstepper %}

### ✅ You’re Done!

Once the connection is active, Datadog will begin visualizing live Luciq metrics like:

* Crash-free sessions
* Frustration-free sessions
* Session breakdowns over time

You can now fully monitor app health using Datadog’s native dashboards powered by Luciq data.

{% hint style="info" %}
### 🧠 Need Help?

If you run into issues, please reach out to [support@luciq.ai](mailto:support@luciq.ai) or your dedicated CSM.
{% endhint %}
