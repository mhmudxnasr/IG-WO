# Instagram Reels Tab Removal Patch

This repository contains the patched Instagram APK and instructions on how the patch was applied.

## Download

You can find the patched APK in the [Releases](https://github.com/mhmudxnasr/IG-WO/releases) section of this repository.

## Patch Details

The Reels tab was removed by modifying `com.instagram.mainactivity.InstagramMainActivity.smali`. 

The patch intercepts the loop that constructs the bottom navigation bar and skips the `CLIPS` tab (represented by the `A09` instance of the `LX/3aj` enum).

```diff
     .line 6930
     check-cast v4, LX/3aj;
 
+    sget-object v0, LX/3aj;->A09:LX/3aj;
+
+    if-ne v4, v0, :cond_skip_reels
+
+    add-int/lit8 v10, v10, 0x1
+
+    goto :goto_3c
+
+    :cond_skip_reels
+
     .line 6931
     .line 6932
     invoke-virtual {v1}, Lcom/instagram/mainactivity/InstagramMainActivity;->A1O()Landroid/view/ViewGroup;
```

## Installation Instructions

> [!IMPORTANT]
> Because the APK has been resigned with a debug key, you **must** uninstall the original Instagram application from your device before installing the patched version.

1.  Download `instagram_patched-aligned-debugSigned.apk` from the Releases section.
2.  Uninstall the existing Instagram app.
3.  Install the patched APK.
4.  Open the app and verify that the Reels (Clips) tab is no longer present.

## Tools Used

- [Apktool](https://github.com/iBotPeaches/Apktool)
- [Uber-APK-Signer](https://github.com/patrickfav/uber-apk-signer)
