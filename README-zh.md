# 童视锁 (KidTvLock)

<img width="160" height="160" alt="ChatGPT Image 2026年6月7日 02_55_51 (1)" src="https://github.com/user-attachments/assets/66330bdc-a279-449b-8368-cd9244997636" />

[English](README.md) · [简体中文](README-zh.md) · [繁體中文](README-zh-TW.md)

Android TV 家长控制应用，使用方向键密码锁定电视，防止孩子独自观看。支持 Android TV 和电视盒子，通过遥控器操作——无需触屏。

## 功能

- **6 位方向键密码** — 仅用遥控器方向键（上/下/左/右）设置和输入密码
- **开机/唤醒自动锁定** — 电视开机或从休眠唤醒时自动弹出锁屏界面
- **悬浮窗锁定** — 在任何应用上层显示全屏锁定覆盖层，从应用列表启动同样生效
- **密码错误抖动反馈** — 输入错误密码时触发抖动动画，提供清晰的视觉反馈
- **应用更新检测** — 发现新版本后弹出更新提示，支持应用内下载和安装
- **手机扫码绑定** — 用手机扫描二维码生成临时解锁口令（30分钟或60分钟）
- **自启动权限引导** — 引导用户授权自启动和悬浮窗权限，确保锁定可靠运行

## 使用方法

1. 在 Android TV 或电视盒子上安装 APK（不知道如何安装应用？让 [ChatGPT](https://chatgpt.com/?q=%E6%99%BA%E8%83%BD%E7%94%B5%E8%A7%86%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%20APK) 或 [豆包](https://www.doubao.com/chat/url-action?action=%7B%22pluginId%22%3A%22Send_Message%22%2C%22payload%22%3A%7B%22text%22%3A%22%E6%99%BA%E8%83%BD%E7%94%B5%E8%A7%86%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%20APK%22%7D%7D) 指导你）
2. 打开应用，按照引导授予**自启动**和**悬浮窗显示**权限
3. 使用遥控器方向键设置 6 位方向密码
4. 下次电视开机或唤醒时，将看到锁屏界面——输入密码即可解锁

## 可选防卸载模式

如果想避免App 被偷偷卸载而绕过锁屏限制。有动手能力、可以用电脑做一次配置的你，可以通过 ADB 开启防卸载模式。操作前请先确保电脑已经安装 Android Platform Tools，并且终端里可以执行 `adb` 命令。不会安装的话，可以让 [ChatGPT](https://chatgpt.com/?q=%E8%AF%B7%E4%B8%80%E6%AD%A5%E6%AD%A5%E6%95%99%E6%88%91%E5%9C%A8%E7%94%B5%E8%84%91%E4%B8%8A%E5%AE%89%E8%A3%85%20Android%20Platform%20Tools%EF%BC%8C%E5%B9%B6%E7%A1%AE%E8%AE%A4%20adb%20%E5%91%BD%E4%BB%A4%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E3%80%82) 或 [豆包](https://www.doubao.com/chat/url-action?action=%7B%22pluginId%22%3A%22Send_Message%22%2C%22payload%22%3A%7B%22text%22%3A%22%E8%AF%B7%E4%B8%80%E6%AD%A5%E6%AD%A5%E6%95%99%E6%88%91%E5%9C%A8%E7%94%B5%E8%84%91%E4%B8%8A%E5%AE%89%E8%A3%85%20Android%20Platform%20Tools%EF%BC%8C%E5%B9%B6%E7%A1%AE%E8%AE%A4%20adb%20%E5%91%BD%E4%BB%A4%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8%E3%80%82%22%7D%7D) 一步步指导安装。

操作步骤：

1. 在电视上安装 APK。
2. 在电视上打开**开发者选项**，开启 **ADB 调试**或**网络调试**。
3. 在电脑终端连接电视，并确认设备已连接：

   ```bash
   adb connect 电视IP:5555
   adb devices
   ```

   `电视IP` 可以在电视的网络设置里查看。如果使用 USB ADB，不需要 `adb connect`，插线后执行 `adb devices` 即可。

   如果 `adb devices` 里同时出现电视和模拟器等多个设备，后面的命令需要指定电视，例如：

   ```bash
   adb -s 电视IP:5555 shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   adb -s 电视IP:5555 shell dpm list-owners
   ```

   这种情况下，可以直接用上面两条命令完成第 4 步和第 5 步。

4. 开启防卸载模式：

   ```bash
   adb shell dpm set-device-owner com.terranc.kidtvlock/.receiver.DeviceAdminReceiver
   ```

5. 验证是否开启：

   ```bash
   adb shell dpm list-owners
   ```

   如果结果里看到 `com.terranc.kidtvlock/.receiver.DeviceAdminReceiver`，说明防卸载模式已经启用。

启用后如需卸载，请主动打开童视锁，输入永久密码，在二维码页面点击**解除防卸载**。解除后，再到电视系统设置中卸载 App。

如果某一步失败，童视锁仍然可以作为普通 App 使用，但不会启用防卸载能力。

## 系统要求

- Android TV 或电视盒子，配有方向键遥控器
- Android 5.0 及以上

## 许可证

专有软件，保留所有权利。
