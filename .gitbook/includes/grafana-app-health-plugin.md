---
title: grafana-app-health-plugin
---

The Luciq Grafana Plugin allows you to visualize mobile metrics alongside other metrics from different sources, such as product analytics and revenue metrics, all within a single pane of glass. Our pre-built dashboard captures all the essential mobile metrics, providing a comprehensive overview of your app's health without leaving Grafana.

Below are instructions on how to install, configure, and navigate through the app health plugin.

## Install the Luciq Plugin

{% stepper %}
{% step %}
### Open Grafana’s plugin directory

Search for "Luciq."

![](<../assets/ca3e7321351a83dfba930e9addc4a560765bf890b25b938f28bb540a50f35657 image.png>)
{% endstep %}

{% step %}
### Install the [Luciq Plugin](https://grafana.com/grafana/plugins/instabug-instabug-app/)

![](<../assets/b069ac5ecb0eddc90988962cea55dde6e4339429983d967a5a64252d7e65a830 image.png>)
{% endstep %}
{% endstepper %}

## Configure the Luciq Plugin

{% hint style="info" %}
After the plugin is installed, navigate to the **Configuration** tab. It may take a couple of minutes for the Configuration tab to appear while the plugin finishes installing. If it doesn't appear right away, refresh the page after a few minutes.
{% endhint %}

* Make sure the plugin is enabled.

![](<../assets/6e4a8d0ea97a806593da37ec1542763ae8091122cad2471f7e83d87c8f97d6dc image.png>)

**Prerequisites:**

* Ensure Grafana version 10.0.0 or higher is installed.
* Install the [Infinity Plugin](https://grafana.com/grafana/plugins/yesoreyeram-infinity-datasource/) (v2.4.0 or higher).

**Configuration:**

{% stepper %}
{% step %}
### If Infinity Plugin is missing

If the Infinity Plugin is not installed, you'll receive a prompt to install it before proceeding.
{% endstep %}

{% step %}
### Contact Luciq support for configuration fields

Contact the Luciq support team at [support@luciq.ai](mailto:support@luciq.ai) to receive the necessary configuration fields:

* API Link
* Dashboard URL
* Authentication Token
* Email
{% endstep %}

{% step %}
### Apply settings

Once you have these fields, input the provided information in the plugin configuration page and click on “Apply Settings”.

![](<../assets/8a25b56f0f62a6fd5964300ca077b56516b5d296d8a872f025ad8b25d50b9b7b image.png>)
{% endstep %}
{% endstepper %}

## Access the Pre-built Dashboard

* After configuration, go to the **Dashboards** tab. The Luciq dashboard will be automatically imported.
* Open the Luciq App Health dashboard to view the health metrics for all your Luciq apps directly within Grafana.

![](<../assets/d32fff0ba29fe649166f5ece04cfbfa74b084d5515fbd2b09dcfc1a1d02496c1 image.png>)

## Luciq Grafana Dashboard Walkthrough

{% stepper %}
{% step %}
### Filters available

You can filter by the following:

* App
* Environment
* Platform (for cross-platform applications)
* Date
{% endstep %}

{% step %}
### Drill down into metrics

Gain a comprehensive overview of your app's stability and performance through our high-level metrics. To delve deeper into a specific metric, click the redirection icon to open the Luciq dashboard with the same applied filters for further analysis.

<figure><img src="../assets/image (53).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
