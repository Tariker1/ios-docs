---
description: >-
  Explained here is how to symbolicate your crashes to get more details from the
  stack trace for your Flutter apps.
---

# Symbolication/Deobfsucation

### Deobfuscating Dart Crashes

In order to start deobfuscating Dart related crashes, you'll first need to follow the steps in the following URL to deobfuscate your app: https://docs.flutter.dev/deployment/obfuscate

#### Android Deobfuscation

For Android, you'll need to follow the steps below to upload the required mapping files:

{% stepper %}
{% step %}
#### Fetch the symbol file

Obtain the symbol file for your Android build.
{% endstep %}

{% step %}
#### Get your API\_KEY

Reach out to our support team to get your `API_KEY`.
{% endstep %}

{% step %}
#### Upload the mapping file

Upload the mapping file using the following endpoint:

{% code title="cURL" %}
```curl
https://api.instabug.com/api/web/public/flutter-symbol-files/android
{
"api_key": "string",
"application_token": "string",
"file": ""
}
//Sample
curl --location --request POST 'https://api.instabug.com/api/web/public/flutter-symbol-files/android' \
--header 'Accept: */*' \
--header 'User-Agent: LuciqDemo/1.0 CFNetwork/1107.1 Darwin/18.7.0' \
--header 'Host: api.instabug.com' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'Accept-Language: en-us' \
--header 'Connection: Keep-Alive' \
--form 'file=@"/path/symbols.zip"' \
--form 'application_token="Token";type=text/plain' \
--form 'api_key="Key";type=text/plain'
```
{% endcode %}
{% endstep %}
{% endstepper %}

#### iOS Deobfuscation

For iOS, you'll need to follow the steps below to upload the required mapping files:

{% stepper %}
{% step %}
#### Fetch the symbol file

Obtain the symbol file for your iOS build.
{% endstep %}

{% step %}
#### Get your API\_KEY

Reach out to our support team to get your `API_KEY`.
{% endstep %}

{% step %}
#### Upload the mapping file

Upload the mapping file using the following endpoint:

{% code title="cURL" %}
```curl
https://api.instabug.com/api/web/public/flutter-symbol-files/ios
{
"api_key": "string"
"application_token": "string",
"file": "",
"app_version_name": "1.0",
"app_version_code": "11",
}
//Sample
curl --location --request POST 'https://api.instabug.com/api/web/public/flutter-symbol-files/ios' \
--header 'Accept: */*' \
--header 'User-Agent: LuciqDemo/1.0 CFNetwork/1107.1 Darwin/18.7.0' \
--header 'Host: api.instabug.com' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'Accept-Language: en-us' \
--header 'Connection: Keep-Alive' \
--form 'file=@"/path/symbols.zip"' \
--form 'application_token="Token";type=text/plain' \
--form 'api_key="Key";type=text/plain' \
--form 'app_version_name="App version"' \
--form 'app_version_code="Build number"'
```
{% endcode %}
{% endstep %}
{% endstepper %}

#### Native iOS Crash Reporting

For iOS native crashes and details regarding symbolication and uploading dSYMs, please refer to the native iOS crash reporting documentation here: ios-symbolication

#### Native Android Crash Reporting

For Android native crashes and details regarding obfuscation and uploading mapping files, please refer to the documentation here: android-obfuscation
