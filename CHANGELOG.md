# Changelog

All notable changes to 童视锁 (KidTvLock) are documented in this file.

## [0.1.1] - 2026-06-07

### Added
- TV vendor autostart settings support for broader device compatibility

### Changed
- Updated target SDK and tests
- Signing config updated with JKS keystore format

### Fixed
- Converted QR sample to valid PNG format
- Disabled ExpiredTargetSdkVersion lint for side-loaded APK distribution

## [0.1.0] - 2026-06-07

### Added
- Multi-language README (English, 简体中文, 繁體中文) with language navigation

### Changed
- README simplified to user-facing content only
- Release mode preference saved for automated GitHub releases

## [0.0.1] - 2026-06-07

### Added
- 6-digit D-pad directional password lock for Android TV
- Auto-lock on device boot and screen wake (BOOT_COMPLETED receiver)
- Full-screen overlay lock service (works from any app, including app-list launches)
- Password setup wizard with confirmation flow
- Change-password and reset-password flows
- Password shake animation on wrong input
- App update checker with download prompt dialog and install handler
- Settings screen with auto-start and overlay permission guides
- Wake-launch strategy (relaunch on wake, refresh launcher assets)
- Guide screen with version display and QR code placeholder for phone binding
- Two-layer color token system (`palette.xml` + `colors.xml`) with semantic naming
- Spotify-inspired dark-stage UI theme (no pure black, green accent only, pill buttons)
- Direction keycap style with inlaid shadow and focus-ring support
- Launcher banner and adaptive icon assets
- Unit tests with Robolectric, MockK, and pattern-based testing

### Changed
- Migrated package from `com.tvlock` to `com.terranc.kidtvlock`
- Target SDK capped at 24 to support overlay permission on older TV boxes
- Unified all colors under semantic tokens; raw hex values isolated to `palette.xml`
