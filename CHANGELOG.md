# Changelog

All notable changes to 童视锁 (KidTvLock) are documented in this file.

## [0.2.6] - 2026-06-12

### Added
- Integrate Umeng SDK for analytics, push notifications, and APM monitoring
- Add Umeng push services and receivers in Android manifest
- Add ProGuard rules to keep Umeng SDK classes

### Changed
- Reorganize Trellis development skills across agent platforms

## [0.2.5] - 2026-06-12

### Changed
- Update release sync guidance and installation guide links in documentation
- Clarify AI translation tool links for English, Simplified Chinese, and Traditional Chinese

### Fixed
- Show the guide screen immediately after password verification without waiting for update checks
- Load the phone binding QR code asynchronously after the guide screen opens

## [0.2.4] - 2026-06-12

### Added
- Add optional uninstall protection for ADB-managed Device Owner installations
- Add a QR page action to disable uninstall protection after permanent password verification

### Changed
- Expand README guidance for enabling, verifying, and removing uninstall protection
- Document Android Platform Tools setup help and multi-device ADB command usage

## [0.2.3] - 2026-06-10

### Changed
- Use foreground service startup for wake monitor to improve reliability

### Fixed
- Restore normal debug build temporary unlock duration (3 minutes)
- Fix password leave recovery behavior

## [0.2.2] - 2026-06-10

### Changed
- Update lock service domain URLs

## [0.2.1] - 2026-06-09

### Changed
- Convert WakeEventMonitorService to a foreground service for improved reliability

### Fixed
- Minor documentation updates

## [0.2.0] - 2026-06-08

### Added
- Offline temporary unlock functionality with phone binding QR code
- 8-digit directional temporary passcode mode (30min and 60min duration options)
- Temporary passcode verification with time-window tolerance (5-min windows, ±1 drift)
- Automatic re-lock scheduling when temporary unlock expires
- Arrow direction display in temporary passcode mode for input verification
- Multi-language support (English, Simplified Chinese, Traditional Chinese)
- Trellis workflow integration for consistent development process
- Test scripts for fetching binding information from TV

### Changed
- Debug builds use 3-minute temporary unlock duration for faster testing
- Improved thread safety in password attempt tracking (commit() instead of apply())
- Added Android 12+ exact alarm permission check for re-lock scheduling

### Fixed
- Resolved build errors from worktree merge (missing strings, unresolved references)
- Fixed temporary unlock API inconsistencies between Python script and TV app
- Corrected test expectations to match actual UI behavior and string resources

### Security
- Added error handling for PasswordManager creation failures
- Implemented fallback for AlarmManager scheduling without exact alarm permission

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
