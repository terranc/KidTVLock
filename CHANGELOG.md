# Changelog

All notable changes to 童视锁 (KidTvLock) are documented in this file.

## [Unreleased]

## [0.3.9] - 2026-06-24

### Added
- Add a help QR entry on the guide screen that opens the usage guide on mobile,
  with a TV-focused overlay, close control, and press-scale feedback.

## [0.3.8] - 2026-06-21

### Changed
- Update release title to "Kid TV Lock v{version}" format for GitHub releases
- Update app icon

## [0.3.7] - 2026-06-20

### Added
- Add an ADB post-install interface for provisioning an initial directional password
  without overwriting an existing password.

## [0.3.6] - 2026-06-19

### Fixed
- Update the limited viewing accessibility button to show "停用限时观看" after
  the Kid TV Lock accessibility service is enabled.

### Changed
- Refresh Trellis Android development specs with source-backed project contracts
  for app structure, state storage, error handling, logging, quality checks, and
  HOME/accessibility behavior.

## [0.3.5] - 2026-06-18

### Fixed
- Fixed Umeng custom event reporting for accessibility settings failures by using
  object-style event parameters and normal analytics scenario/lifecycle hooks
- Added realtime debug deep-link handling for Umeng integration testing

### Changed
- Added debug-only guide button reporting to verify the custom event pipeline without
  affecting release builds

## [0.3.4] - 2026-06-17

### Changed
- Redesigned guide screen: widened the primary action button and grouped the two
  secondary buttons (limited viewing / disable uninstall protection) into a compact
  side-by-side row for a clearer visual hierarchy
- Renamed the accessibility action to "开启限时观看" with a "通过无障碍功能实现" caption below
- Moved the version label to the bottom-left corner of the screen

### Fixed
- Accessibility button is no longer wrongly hidden on ROMs that mis-report the settings
  intent as unavailable (e.g. Xiaomi TV); it now always shows and verifies on click

### Added
- Report device info via Umeng custom event when accessibility settings cannot be opened,
  to help diagnose ROM compatibility

## [0.3.3] - 2026-06-16

### Added
- Delayed HOME candidate activation via activity-alias (avoids HOME chooser popup on fresh install)

## [0.3.2] - 2026-06-16

### Changed
- Retry launcher detection after saved component fails for improved reliability

## [0.3.1] - 2026-06-16

### Added
- Accessibility relock for temporary unlock expiry (triggers relock via accessibility service when alarm fires)
- Route relock through HOME gate for improved compatibility

### Changed
- Refined temporary unlock relock scheduling logic

## [0.3.0] - 2026-06-16

### Added
- Default HOME gate mode for improved Xiaomi TV compatibility (detects and blocks default launcher)
- Navigator and PasswordManager APIs for extensible launcher integration
- Real launcher selection flow with vendor-specific auto-start settings

### Changed
- Refined unlock session handling for better reliability across TV vendors

### Fixed
- Passcode dot drawables now render consistently across devices (added `<size>` attribute)
- Fixed QR code crash on older Android TV devices when entering guide page

### Removed
- Umeng push notification SDK (TV devices don't require push functionality)

## [0.2.7] - 2026-06-13

### Added
- Phone binding QR code now fully functional with real QR generation
- NDK ABI filters to reduce APK size (armeabi-v7a, arm64-v8a, armeabi)

### Changed
- Enable resource shrinking for release builds
- Replace PNG launcher assets with WebP format for smaller APK
- Update English QR binding prompt text

### Removed
- "Coming soon" placeholder text and overlay for QR code
- Unused bools.xml resource files

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
