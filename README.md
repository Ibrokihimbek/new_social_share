
# new_social_share

Wide variety of sharing options you'll need to share directly to certain popular apps or just share with default native share.

## Introduction

Works on both platforms `Android` and `iOS`

It provides you with most of the popular sharing options.  
With this plugin, you can share on Instagram stories and Facebook stories and also copy to the clipboard.

## Acknowledgment

This package, **new_social_share**, is based on the original work by [ShekarMudaliyar](https://pub.dev/packages/social_share). Many thanks to the creator for their valuable contribution, which inspired the development of this upgraded and enhanced version.

## Usage

### Android Configuration

#### Paste the following attribute in the `manifest` tag in the `android/app/src/main/AndroidManifest.xml`:

```
xmlns:tools="http://schemas.android.com/tools"
```

##### For example:

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          package="your package...">
```

#### Add this piece of code in the `manifest/application` in the `android/app/src/main/AndroidManifest.xml`:

```
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="${applicationId}.com.ibrohim.new_social_share.new_social_share"
    android:exported="false"
    android:grantUriPermissions="true"
    tools:replace="android:authorities">
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/filepaths" />
</provider>
```

#### Create a xml file named `filepaths.xml` in the `app/src/main/res/xml` folder and paste this code in the file :

```
<?xml version="1.0" encoding="utf-8"?>
<paths xmlns:android="http://schemas.android.com/apk/res/android">
    <cache-path name="image" path="/"/>
</paths>
```

### iOS Configuration

#### Add this to your `Info.plist` to use share on Instagram and Facebook stories:

```
<key>LSApplicationQueriesSchemes</key>
<array>
<string>instagram-stories</string>
<string>facebook-stories</string>
<string>facebook</string>
<string>instagram</string>
<string>twitter</string>
<string>whatsapp</string>
<string>tg</string>
</array>
```

### Add this if you are using share on Facebook. For this, you have to create an app on https://developers.facebook.com/ and get the App ID:

```
<key>FacebookAppID</key>
<string>xxxxxxxxxxxxxxx</string>
```

#### shareInstagramStory

```
SocialShare.shareInstagramStory(imageFile.path, "#ffffff",
                              "#000000", "https://deep-link-url");
```

#### shareInstagramStorywithBackground

```
SocialShare.shareInstagramStorywithBackground(image.path, "https://deep-link-url",
                              backgroundImagePath: backgroundimage.path);
```

#### shareFacebookStory

For iOS:

```
SocialShare.shareFacebookStory(image.path,"#ffffff","#000000",
                              "https://deep-link-url","facebook-app-id");
```

For Android (appID is mandatory if using shareFacebookStory or else it won’t work):

```
SocialShare.shareFacebookStory(image.path,"#ffffff","#000000",
                              "https://deep-link-url","facebook-app-id",
                              appId: "xxxxxxxxxxxxx");
```

#### copyToClipboard

```
SocialShare.copyToClipboard("This is Social Share plugin");
```

#### shareTwitter

```
//without hashtags
SocialShare.shareTwitter("This is Social Share plugin");

//with hashtags
SocialShare.shareTwitter(
    "This is Social Share twitter example",
    hashtags: ["hello", "world", "foo", "bar"]);

//with hashtags and link
SocialShare.shareTwitter(
    "This is Social Share twitter example",
    hashtags: ["hello", "world", "foo", "bar"], url: "https://your-url-here/");
```

#### shareSms

```
//without url link in message
SocialShare.shareSms("This is Social Share Sms example");

//with url link in message
SocialShare.shareSms("This is Social Share Sms example", url: "https://your-url-here/");
```

#### shareWhatsapp

```
SocialShare.shareWhatsapp("Hello World");
```

#### shareTelegram

```
SocialShare.shareTelegram("Hello World");
```

#### shareOptions

This will open the default native share options:

```
//without an image
SocialShare.shareOptions("Hello world");

//with an image
SocialShare.shareOptions("Hello world", imagePath: image.path);
```

#### checkInstalledAppsForShare

```
SocialShare.checkInstalledAppsForShare();
```
