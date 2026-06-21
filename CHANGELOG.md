# Changelog

## [Unreleased]
### Added
- **iOS critical alerts support:** `CriticalAlertUtils`, `interruptionLevel.critical`, and `UNNotificationSound.defaultCritical` when Apple entitlement and user permission are available, with graceful fallback otherwise.
- **`getPermissionStatuses()`** and `NotificationPermissionStatus` enum for explicit permission status mapping (`granted`, `denied`, `notDetermined`, `notSupported`).
### Fixed
- **Critical Alert permission flow:** When base notifications were already granted, requesting `CriticalAlert` could skip the system dialog and open Settings without calling `requestAuthorization(options: [.criticalAlert])`, so the Critical Alerts toggle never appeared in iOS Settings.
- **`NotificationChannelModel.toMap()`** exported `locked` instead of `criticalAlerts`, corrupting persisted channels.
- **Notification content `criticalAlert` flag** is now read on the iOS native layer.
- **Permission filter** for `OverrideDnD` when critical alerts entitlement is not supported.
- **IAC-001:** `areNotificationsGloballyAllowed` now handles `.provisional` and `.ephemeral` authorization statuses.
- **IAC-007:** Permission rationale branch now inspects `listToShowRationale.first` instead of `permissionsNeeded.first`.
