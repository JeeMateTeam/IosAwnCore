# Changelog

## [0.12.1] - 2026-06-21
### Added
- **iOS critical alerts support:** `CriticalAlertUtils`, `interruptionLevel.critical`, and `UNNotificationSound.defaultCritical` when Apple entitlement and user permission are available, with graceful fallback otherwise.
- **Notification content `criticalAlert` flag** on the iOS native layer.
### Fixed
- **`NotificationChannelModel.toMap()`** exported `locked` instead of `criticalAlerts`.
- **Permission filter** for `OverrideDnD` when critical alerts entitlement is not supported.

## [0.12.0] - 2026-06-16
### Changed
- Swift Package Manager support and iOS 15 minimum deployment alignment.
