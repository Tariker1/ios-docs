---
description: >-
  This page contains an overview of the information available in the App Ratings
  & Review section of the Luciq Docs for Android apps.
---

# App Ratings & Reviews

To start using App Ratings and Reviews, navigate to the App Reviews page on your dashboard from the side navigation bar and choose your app’s bundle ID or package name. Luciq will then automatically fetch your existing app store reviews and detect new reviews your app receives.

{% hint style="warning" %}
**Min Required SDK Version**

App Ratings & Reviews is supported starting Android SDK version 12.1.0.
{% endhint %}

<figure><img src="https://files.readme.io/a6c01b77de29a258d16122574e8b4f05657d46753c67c2cfaf8617948c2a4720-android-app-reviews-1.png" alt="" width="375"><figcaption></figcaption></figure>

Once you confirm your bundle ID, you’ll be able to track, monitor, and debug App Reviews and Ratings.

## Track App Reviews

In the App Reviews page in the side navigation bar, you’ll find a list of all reviews your app received, where you'll be able to view the following metadata:

* Rating
* Review
* Date
*   App Version

    <figure><img src="https://files.readme.io/aa70be18a08991cdfb74da1f338c1af1ae2864b01e886754fbe79de64f3b6d82-android-app-reviews-2.png" alt="" width="375"><figcaption></figcaption></figure>

<br>

## Monitor App Ratings

From the App Overview page, you’ll be able to monitor your overall app rating per country to see how your ratings are distributed and see a chart for the Rating over time.

By clicking on view all reviews button, you’ll be redirected to the App Reviews page to see a list of all your reviews.

<figure><img src="https://files.readme.io/80bce178259328db991dbd8de85b8181e474c324e9ab0dede6bcbe583c357010-android-app-reviews-3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://files.readme.io/ed557c0f347f737806630d7686b6452ed9be656d62d235b8954b6df34c076108-android-app-reviews-4.png" alt=""><figcaption></figcaption></figure>

## Monitor App Ratings and Reviews for each Release

From the releases page, you’ll be able to see the Average Rating for each release. This average rating is calculated based on the star rating associated with each review the user wrote on the store for this app version.

<figure><img src="https://files.readme.io/14efc6e265bf3fa2a2fc3f9a49b0487158217c38aa6d99a6804ec68ae8fbc932-android-app-reviews-5.png" alt="" width="375"><figcaption></figcaption></figure>

From the release details page, you'll be able to see a breakdown of your App Rating based on the number of stars.

In the comparison table, you’ll be able to see the current version rating and compare it across different releases.

<figure><img src="https://files.readme.io/9adcc5a6c6756d537d5931ffa09a949abc747f0a2c98ac758d98700a03c650e3-android-app-reviews-6.png" alt="" width="375"><figcaption></figcaption></figure>

Once you navigate to the summary tab, you'll be able to see an AI-generated summary of the reviews for this release to get an idea about the end user sentiment.

<figure><img src="https://files.readme.io/db7154448ebe962d73bdf277b6caae4e7513c67ce139eb7f365d339a435f62be-android-app-reviews-7.png" alt="" width="375"><figcaption></figcaption></figure>

## Debug App Reviews

Tracking your app's ratings and reviews is only the first step. Combining Ratings and Reviews with Luciq's Session Replay allows you to view a list of the sessions related to a specific review and replay them to understand the experience that led to that review.

### How It Works

#### Native In-App Prompt

If you’re using the native in-app rating API, Our SDK will automatically detect the suspected sessions that are related to the reviews you receive on the dashboard.

<figure><img src="https://files.readme.io/8f9920f4c97ebf3ab3d70cbf94580324e428e66e6ad04eb42065c81204e44d96-android-app-reviews-8.png" alt="" width="375"><figcaption></figcaption></figure>

Once you click on **"View Session"** CTA, you'll be redirected to the list of suspected sessions we matched for this review.

<figure><img src="https://files.readme.io/43bebe838f738c33086a4af161a6b9a49e0d365cc6d6417f839d4d6379c069e5-android-app-reviews-9.png" alt="" width="375"><figcaption></figcaption></figure>

When you click on session details, you'll be able to replay the session associated with that review and see all the needed debugging data that would help you resolve the issue.

<figure><img src="https://files.readme.io/004c7239c9f37c91ea9fd7420fb5ecc893680227cee905e5d45b17056ab51109-android-app-reviews-10.png" alt="" width="375"><figcaption></figcaption></figure>

<br>
