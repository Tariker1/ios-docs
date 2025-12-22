---
description: Measure the loading performance of your WebViews with Web Vitals.
---

# WebViews Screen Loading

{% hint style="warning" %}
### Min Required SDK Version

WebViews screen loading is supported starting iOS SDK version `12.9.2`&#x20;
{% endhint %}

WebViews are components that embed web content within native mobile applications. They can be an easy and cost-effective alternative to redesigning some pages from scratch for your mobile app.

Luciq automatically captures the time it takes for your WebViews to load. This includes both the time to load the native screen that hosts the WebView and the time it takes the WebView itself to load along with its content.

<figure><img src="../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Luciq only detects WebViews that fill the **majority (<75%)** of the native screens they are hosted in. Smaller WebViews such as banners or small ads will not be captured.
{% endhint %}

{% hint style="info" %}
Luciq only supports the `WKWebView` class of the `WebKit` framework.
{% endhint %}

### Web Vitals

Web Vitals are a suite of user-centric performance metrics developed by Google that measure the loading speed, interactivity, and visual stability of web pages. Google considers **Core Web Vitals** to be the most important of these metrics and should be “tracked by every developer for every website”, including **First Input Delay (FID)**.

**First Input Delay (FID)** measures interactivity or the time between the user first trying to interact with the page and the webpage starting to process that interaction. You can learn more about Web Vitals [here](https://web.dev/articles/vitals#core-web-vitals).

{% hint style="info" %}
For iOS applications, only First Input Delay (FID) Core Web Vital is supported by Apple.
{% endhint %}

Luciq automatically captures First Input Delay (FID) and displays it for all detected WebViews in in your application. FID is benchmarked according to Google’s [recommendations](https://web.dev/articles/vitals#core_web_vitals).

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Time shown on the top of the Screen Loading pages is the P75 of First Input Delay (FID)</p></figcaption></figure>

### Spans

Because total Screen Loading time only tells half the story, you can see in the Spans breakdown how each span contributes to the total screen loading time. The WebViews Loading span shows the time it took to load the WebView and its content, along with the WebView URL for quick identification or debugging. You can also check all the other spans associated with the native components of the screen, such as native loading stages or network calls, so you can find the bottleneck wherever it may be.

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Network calls originating from **within the WebView** will not be captured as they are invisible to the SDK. Only network calls originating from the native app itself will be shown.
{% endhint %}

### Disabling/Enabling WebViews Tracking

If APM and Screen Loading are enabled, the SDK automatically collects data about your WebViews loading time. If needed, you can always toggle this on and off by updating the relevant flag after the SDK is initialized.

{% tabs %}
{% tab title="Swift" %}
{% code overflow="wrap" %}
```swift
//Disable WebViews Tracking
APM.webViewTrackingEnabled = false
//Enable WebViews Tracking
APM.webViewTrackingEnabled = true
```
{% endcode %}
{% endtab %}

{% tab title="Objective-C" %}
{% code overflow="wrap" %}
```objectivec
//Disable WebViews Tracking
[LCQAPM setWebViewTrackingEnabled:NO];
//Enable WebViews Tracking
[LCQAPM setWebViewTrackingEnabled:YES];
```
{% endcode %}
{% endtab %}
{% endtabs %}
