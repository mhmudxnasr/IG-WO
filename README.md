# Instagram Reels Tab Removal Patch

This repository contains information and a patch to remove the Reels tab from the Instagram Android application.

## Overview

The Reels tab is removed by modifying the `InstagramMainActivity` smali code to skip the creation and addition of the `CLIPS` tab during the navigation bar construction loop.

## How it Works

The patch intercepts the tab iteration loop in `com.instagram.mainactivity.InstagramMainActivity` and checks if the current tab is `A09` (Clips) from the `LX/3aj` enum. If it is, the loop increment is called immediately, skipping the UI creation for that tab.

## Tools Required

- [Apktool](https://github.com/iBotPeaches/Apktool)
- [Uber-APK-Signer](https://github.com/patrickfav/uber-apk-signer)
- JDK 17+

## Usage Instructions

1. Decompile the target Instagram APK using `apktool`.
2. Apply the smali patch to `com.instagram.mainactivity.InstagramMainActivity.smali`.
3. Rebuild the APK using `apktool`.
4. Sign the APK using `uber-apk-signer`.

## Disclaimer

This project is for educational purposes only. Modifying third-party applications may violate their terms of service.
