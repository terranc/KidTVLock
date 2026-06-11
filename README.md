# 童视锁 (KidTvLock)
<img width="160" height="160" alt="ChatGPT Image 2026年6月7日 02_55_51 (1)" src="https://github.com/user-attachments/assets/66330bdc-a279-449b-8368-cd9244997636" />

[English](README.md) · [简体中文](README-zh.md) · [繁體中文](README-zh-TW.md)

An Android TV parental control app that locks the TV behind a directional-pad passcode, preventing unsupervised watching. Works on Android TV and TV boxes with a remote control — no touchscreen required.

## Features

- **6-digit D-pad password** — set and enter your passcode using only the remote's directional keys (Up/Down/Left/Right)
- **Auto-lock on boot & wake** — locks the screen automatically when the TV powers on or wakes from sleep
- **Overlay lock** — displays a full-screen overlay on top of any app, works even when launched via the app list
- **Password shake feedback** — a shake animation on wrong password entry gives clear visual feedback
- **App update checking** — detects new versions and prompts for in-app download and installation
- **QR code for phone binding** — scan a QR code with your phone to generate temporary unlock codes (30min or 60min)
- **Self-start permission guide** — walks you through granting the auto-start and overlay permissions required for reliable locking

## How It Works

1. [Download the latest APK](https://github.com/terranc/KidTVLock/releases/latest) and install on your Android TV or TV box (not sure how? let [ChatGPT](https://chatgpt.com/?q=How%20to%20install%20APK%20on%20Android%20TV) or [Doubao](https://www.doubao.com/chat/url-action?action=%7B%22pluginId%22%3A%22Send_Message%22%2C%22payload%22%3A%7B%22text%22%3A%22How%20to%20install%20APK%20on%20Android%20TV%22%7D%7D) guide you)
2. Open the app and follow the setup guide to grant **auto-start** and **overlay display** permissions
3. Set a 6-directional passcode using the remote's D-pad
4. The next time the TV boots or wakes, you'll see the lock screen — enter the passcode to unlock

## Optional Uninstall Protection

If you want to prevent the app from being secretly uninstalled to bypass the lock, users who can do a one-time computer setup can enable uninstall protection with ADB. Before starting, install Android Platform Tools on your computer and make sure the `adb` command is available in your terminal. Need help installing it? Ask [ChatGPT](https://chatgpt.com/?q=Show%20me%20step%20by%20step%20how%20to%20install%20Android%20Platform%20Tools%20on%20my%20computer%20and%20verify%20that%20the%20adb%20command%20works.) or [Doubao](https://www.doubao.com/chat/url-action?action=%7B%22pluginId%22%3A%22Send_Message%22%2C%22payload%22%3A%7B%22text%22%3A%22Show%20me%20step%20by%20step%20how%20to%20install%20Android%20Platform%20Tools%20on%20my%20computer%20and%20verify%20that%20the%20adb%20command%20works.%22%7D%7D) for step-by-step guidance.

Steps:

1. Install the APK on the TV.
2. On the TV, enable **Developer options** and turn on **ADB debugging** or **Network debugging**.
3. Connect from your computer and confirm the device is connected:

   ```bash
   adb connect TV_IP:5555
   adb devices
   ```

   You can find `TV_IP` in the TV network settings. If you use USB ADB instead of network ADB, plug in the TV/box and only run `adb devices`.

   If `adb devices` shows the TV plus an emulator or another device, specify the TV in the following commands. For example:

   ```bash
   adb -s TV_IP:5555 shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   adb -s TV_IP:5555 shell dpm list-owners
   ```

   In this case, you can use the two commands above for step 4 and step 5.

4. Enable uninstall protection:

   ```bash
   adb shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   ```

5. Verify whether it is enabled:

   ```bash
   adb shell dpm list-owners
   ```

   If the result shows `com.terranc.kidtvlock/.receiver.DeviceAdminReceiver`, uninstall protection is enabled.

To uninstall after enabling protection, open KidTvLock, enter the permanent password, then tap **Disable uninstall protection** on the QR code page. After protection is disabled, uninstall the app from the TV's system settings.

If any step fails, KidTvLock can still be used as a regular app, but uninstall protection is not enabled.

## Requirements

- Android TV or TV box with a D-pad remote control
- Android 5.0 or later

## License

Proprietary. All rights reserved.
