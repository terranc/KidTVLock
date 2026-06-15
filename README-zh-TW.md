# 童視鎖 (KidTvLock)

<img width="160" height="160" alt="ChatGPT Image 2026年6月7日 02_55_51 (1)" src="https://github.com/user-attachments/assets/66330bdc-a279-449b-8368-cd9244997636" />

[English](README.md) · [简体中文](README-zh.md) · [繁體中文](README-zh-TW.md)

Android TV 家長控制應用，使用方向鍵密碼鎖定電視，防止孩子獨自觀看。支援 Android TV 和電視盒子，透過遙控器操作——無需觸控螢幕。

## 功能

- **6 位方向鍵密碼** — 僅用遙控器方向鍵（上/下/左/右）設定和輸入密碼
- **開機/喚醒自動鎖定** — 電視開機或從休眠喚醒時自動彈出鎖定畫面
- **全螢幕鎖定** — 電視開機或喚醒時接管螢幕，必須輸入密碼才能使用
- **密碼錯誤抖動回饋** — 輸入錯誤密碼時觸發抖動動畫，提供清晰的視覺回饋
- **應用更新檢測** — 發現新版本後彈出更新提示，支援應用內下載和安裝
- **手機掃碼綁定** — 用手機掃描 QR 碼產生臨時解鎖密碼（30分鐘或60分鐘）
- **權限設定引導** — 引導使用者完成權限設定，確保鎖定功能正常運行

## 使用方法

1. 在 Android TV 或電視盒子上安裝 APK（不知道如何安裝應用？讓 [ChatGPT](https://chatgpt.com/?q=%E6%99%BA%E8%83%BD%E7%94%B5%E8%A7%86%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%20APK) 指導你）
2. 開啟應用，按照引導授予所需權限
3. 使用遙控器方向鍵設定 6 位方向密碼
4. 下次電視開機或喚醒時，將看到鎖定畫面——輸入密碼即可解鎖

## 可選防卸載模式

如果想避免 App 被偷偷卸載而繞過鎖定限制。有動手能力、可以用電腦做一次設定的你，可以透過 ADB 開啟防卸載模式。操作前請先確保電腦已經安裝 Android Platform Tools，並且終端機裡可以執行 `adb` 指令。不會安裝的話，可以讓 [ChatGPT](https://chatgpt.com/?q=%E8%AB%8B%E4%B8%80%E6%AD%A5%E6%AD%A5%E6%95%99%E6%88%91%E5%9C%A8%E9%9B%BB%E8%85%A6%E4%B8%8A%E5%AE%89%E8%A3%9D%20Android%20Platform%20Tools%EF%BC%8C%E4%B8%A6%E7%A2%BA%E8%AA%8D%20adb%20%E6%8C%87%E4%BB%A4%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E3%80%82) 一步步指導安裝。

操作步驟：

1. 在電視上安裝 APK。
2. 在電視上開啟**開發者選項**，開啟 **ADB 偵錯**或**網路偵錯**。
3. 在電腦終端機連線電視，並確認裝置已連線：

   ```bash
   adb connect 電視IP:5555
   adb devices
   ```

   `電視IP` 可以在電視的網路設定裡查看。如果使用 USB ADB，不需要 `adb connect`，接線後執行 `adb devices` 即可。

   如果 `adb devices` 裡同時出現電視和模擬器等多個裝置，後面的指令需要指定電視，例如：

   ```bash
   adb -s 電視IP:5555 shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   adb -s 電視IP:5555 shell dpm list-owners
   ```

   這種情況下，可以直接用上面兩條指令完成第 4 步和第 5 步。

4. 開啟防卸載模式：

   ```bash
   adb shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   ```

5. 驗證是否開啟：

   ```bash
   adb shell dpm list-owners
   ```

   如果結果裡看到 `com.terranc.kidtvlock/.receiver.DeviceAdminReceiver`，表示防卸載模式已經啟用。

啟用後如需卸載，請主動開啟童視鎖，輸入永久密碼，在 QR 碼頁面點擊**解除防卸載**。解除後，再到電視系統設定中卸載 App。

如果某一步失敗，童視鎖仍然可以作為普通 App 使用，但不會啟用防卸載能力。

## 系統需求

- Android TV 或電視盒子，配備方向鍵遙控器
- Android 5.0 及以上

## 授權條款

專有軟體，保留所有權利。
