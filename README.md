Adverline Android SDK
==================

Supported creative formats:
* Banners
* Interstitials


## Requirements

This SDK requires Android 4.0 or later, and Android SDK version 14 or higher.


## Installation

In order to include the SDK, insert the following in your build.gradle file:

```text
repositories {
  maven {
    url = 'https://github.com/adverline/mobile-sdk-android/raw/master'
  }
}
dependencies {
  compile 'com.adverline.opensdk:adverline-sdk:1.0.5'
}
```


## Permissions

The following permissions are required:

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
```


## Configuration

You only need to set this once in your app:

```java
SDK.IDApplication = "12345";
```

And the following imports are required in every activity where you'll want to show ads:

```java
import com.adverline.opensdk.*;
import com.adverline.opensdk.formats.*;
import com.adverline.opensdk.listeners.*;
import com.adverline.opensdk.views.*;
```


## Show Banners

```java
// MY_LAYOUT is the ID of the Linear Layout which whill be holding the ad
final LinearLayout ll = (LinearLayout) findViewById(R.id.MY_LAYOUT);

Slot bannerAd = new Slot(this, Format.BANNER);
bannerAd.loadRequest();

ll.addView(bannerAd);
```


## Show Interstitials

```java
Slot interstitialAd = new Slot(this, Format.INTERSTITIAL);
interstitialAd.loadRequest();
```


## Listeners

The following listeners are available.

```java
Slot bannerAd = new Slot(this, Format.BANNER);

bannerAd.setSlotListener(new SlotListener() {
  @Override
  public void onAdLoadingFailed(View view) {
    // ad loading failed (eg. no ad, network error, etc.)
  }

  @Override
  public void onAdLoaded(AdvView view) {
    // ad loaded
  }

  @Override
  public void onAdClicked(View view) {
    // ad clicked
  }

  @Override
  public void onAdRefreshed(View view) {
    // ad refreshed (unused)
  }

  @Override
  public void onAdClosed(View view) {
    // ad closed (interstitials)
  }

  @Override
  public void onAdShown(View view) {
    // ad shown
  }
});

bannerAd.loadRequest();
```
