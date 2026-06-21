# Changelog

## [0.12.4] - 2026-06-21
### Fixed
- **Swift compile error:** Added explicit `self.` for critical alert helper calls inside escaping closures (`isCriticalAlertEntitlementMissing`, `shouldRequestCriticalAlertAuthorization`, `iosCriticalAlertAuthorizationPermissions`).

## [0.12.3] - 2026-06-21
### Fixed
- **Critical Alerts iOS false positive:** When base notifications were already granted, iOS could report `criticalAlertSetting == .notSupported` before the first explicit request even with a valid Apple entitlement. The permission flow now distinguishes a missing entitlement from this iOS quirk and calls `requestAuthorization` with Alert, Sound, Badge, and CriticalAlert as required by Apple.

## [0.12.2] - 2026-06-21
### Added
- **`getPermissionStatuses()`** and `NotificationPermissionStatus` enum for explicit permission status mapping (`granted`, `denied`, `notDetermined`, `notSupported`).
### Fixed
- **Critical Alert permission flow:** When base notifications were already granted, requesting `CriticalAlert` could skip the system dialog and open Settings without ever calling `requestAuthorization(options: [.criticalAlert])`, so the Critical Alerts toggle never appeared in iOS Settings.
- **IAC-001:** `areNotificationsGloballyAllowed` now handles `.provisional` and `.ephemeral` authorization statuses.
- **IAC-007:** Permission rationale branch now inspects `listToShowRationale.first` instead of `permissionsNeeded.first`.

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
