---
title: "SMS"
description: "Learn how to use the .NET MAUI ISms interface in Microsoft.Maui.ApplicationModel.Communication to open the default SMS application. The text message can be preloaded with a message and recipient."
ms.date: 09/02/2022
no-loc: ["Microsoft.Maui", "Microsoft.Maui.ApplicationModel.Communication"]
---

# SMS

This article describes how you can use the .NET Multi-platform App UI (.NET MAUI) `ISms` interface to open the default SMS app and preload it with a message and recipient.

The default implementation of the `ISms` interface is available through the `Sms.Default` property. Both the `ISms` interface and `Sms` class are contained in the `Microsoft.Maui.ApplicationModel.Communication` namespace.

## Get started

To access the SMS functionality, the following platform specific setup is required.

<!-- markdownlint-disable MD025 -->
# [Android](#tab/android)

If your project's Target Android version is set to **Android 11 (R API 30)** or higher, you must update your _Android Manifest_ with queries that use Android's [package visibility requirements](https://developer.android.com/preview/privacy/package-visibility).

In the _Platforms/Android/AndroidManifest.xml_ file, add the following `queries/intent` nodes the `manifest` node:

```xml
<queries>
  <intent>
    <action android:name="android.intent.action.VIEW" />
    <data android:scheme="smsto"/>
  </intent>
</queries>
```

# [iOS\macOS](#tab/ios)

No additional setup required.

# [Windows](#tab/windows)

No additional setup required.

-----
<!-- markdownlint-enable MD025 -->

## Create a message

The SMS functionality works by creating a new `SmsMessage` object, and calling the `ComposeAsync` method. You can optionally include a message and zero or more recipients.

:::code language="csharp" source="../snippets/shared_1/CommsPage.xaml.cs" id="sms_send":::
