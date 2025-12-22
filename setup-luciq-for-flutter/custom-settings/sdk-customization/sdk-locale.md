---
description: >-
  This section covers how to change the language of the SDK in your app as well
  as the content of all Luciq messages that your users see for Flutter apps.
---

# SDK Locale

### Setting the Locale

The SDK will automatically use the current locale of your user's device; however, you can override it with the following method.

{% code title="Dart" %}
```dart
Luciq.setLocale(LCQLocale.french);
```
{% endcode %}

Here are the possible locale values.

{% code title="Dart" %}
```dart
LCQLocale.arabic
LCQLocale.azerbaijani
LCQLocale.chineseSimplified
LCQLocale.chineseTraditional
LCQLocale.czech
LCQLocale.danish
LCQLocale.dutch
LCQLocale.english
LCQLocale.french
LCQLocale.german
LCQLocale.italian
LCQLocale.japanese
LCQLocale.korean
LCQLocale.polish
LCQLocale.portugueseBrazil
LCQLocale.portuguesePortugal
LCQLocale.romanian
LCQLocale.russian
LCQLocale.spanish
LCQLocale.swedish
LCQLocale.turkish
LCQLocale.indonesian
LCQLocale.slovak
LCQLocale.norwegian
LCQLocale.hungarian
LCQLocale.finnish
```
{% endcode %}

{% hint style="info" %}
At the moment, the Luciq dashboard only supports English. Changing the SDK locale will not change the language of your dashboard.
{% endhint %}

### Overriding String Values

You can also override each string shown to your users individually using the following method.

{% code title="Dart" overflow="wrap" %}
```dart
Luciq.setValueForStringWithKey("Please enter a correct email address", CustomTextPlaceHolderKey.invalidEmailMessage);
```
{% endcode %}

<details>

<summary>Possible key values</summary>

```dart
CustomTextPlaceHolderKey.shakeHint
CustomTextPlaceHolderKey.swipeHint
CustomTextPlaceHolderKey.invalidEmailMessage
CustomTextPlaceHolderKey.invocationHeader
CustomTextPlaceHolderKey.reportQuestion
CustomTextPlaceHolderKey.reportBug
CustomTextPlaceHolderKey.reportFeedback
CustomTextPlaceHolderKey.emailFieldHint
CustomTextPlaceHolderKey.commentFieldHintForBugReport
CustomTextPlaceHolderKey.commentFieldHintForFeedback
CustomTextPlaceHolderKey.commentFieldHintForQuestion
CustomTextPlaceHolderKey.addImageFromGallery
CustomTextPlaceHolderKey.addExtraScreenshot
CustomTextPlaceHolderKey.conversationsListTitle
CustomTextPlaceHolderKey.audioRecordingPermissionDenied
CustomTextPlaceHolderKey.conversationTextFieldHint
CustomTextPlaceHolderKey.voiceMessagePressAndHoldToRecord
CustomTextPlaceHolderKey.voiceMessageReleaseToAttach
CustomTextPlaceHolderKey.reportSuccessfullySent
CustomTextPlaceHolderKey.successDialogHeader
CustomTextPlaceHolderKey.addVideo
CustomTextPlaceHolderKey.videoPressRecord
CustomTextPlaceHolderKey.betaWelcomeMessageWelcomeStepTitle
CustomTextPlaceHolderKey.betaWelcomeMessageWelcomeStepContent
CustomTextPlaceHolderKey.betaWelcomeMessageHowToReportStepTitle
CustomTextPlaceHolderKey.betaWelcomeMessageHowToReportStepContent
CustomTextPlaceHolderKey.betaWelcomeMessageFinishStepTitle
CustomTextPlaceHolderKey.betaWelcomeMessageFinishStepContent
CustomTextPlaceHolderKey.liveWelcomeMessageTitle
CustomTextPlaceHolderKey.liveWelcomeMessageContent
CustomTextPlaceHolderKey.surveysStoreRatingThanksTitle
CustomTextPlaceHolderKey.surveysStoreRatingThanksSubtitle
CustomTextPlaceHolderKey.reportBugDescription
CustomTextPlaceHolderKey.reportFeedbackDescription
CustomTextPlaceHolderKey.reportQuestionDescription
CustomTextPlaceHolderKey.requestFeatureDescription
CustomTextPlaceHolderKey.discardAlertTitle
CustomTextPlaceHolderKey.discardAlertMessage
CustomTextPlaceHolderKey.discardAlertCancel
CustomTextPlaceHolderKey.discardAlertAction
CustomTextPlaceHolderKey.addAttachmentButtonTitleStringName
CustomTextPlaceHolderKey.reportReproStepsDisclaimerBody
CustomTextPlaceHolderKey.reportReproStepsDisclaimerLink
CustomTextPlaceHolderKey.reproStepsProgressDialogBody
CustomTextPlaceHolderKey.reproStepsListHeader
CustomTextPlaceHolderKey.reproStepsListDescription
CustomTextPlaceHolderKey.reproStepsListEmptyStateDescription
CustomTextPlaceHolderKey.reproStepsListItemTitle
CustomTextPlaceHolderKey.okButtonText
CustomTextPlaceHolderKey.audio
CustomTextPlaceHolderKey.image
CustomTextPlaceHolderKey.screenRecording
CustomTextPlaceHolderKey.messagesNotificationAndOthers
CustomTextPlaceHolderKey.insufficientContentTitle
CustomTextPlaceHolderKey.insufficientContentMessage
```

</details>
