<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/ -->
<!-- Sitemap-Last-Modified: 2026-08-06 -->

# Device actions

In today's hybrid work environment, IT professionals manage and secure devices across diverse locations and platforms—often without physical access. Microsoft Intune's device actions provide a powerful toolkit to meet this challenge. These actions enable IT pros to respond quickly to incidents, enforce compliance, and maintain productivity, all from the cloud. Whether it's locking a lost device, resetting a password, or triggering a malware scan, device actions help ensure that users stay protected and supported—wherever they are.

## When device actions are useful

Device actions are especially valuable in scenarios where time and access are limited. For example:

- A device is reported lost or stolen—IT can remotely wipe or lock it to protect sensitive data.
- A device is malfunctioning—IT can restart it or run diagnostics without needing to be on-site.
- A device needs to receive a payload immediately—IT can trigger a sync to apply the latest policies.
- A malware alert is raised—security teams can initiate a Defender Antivirus scan remotely.

These capabilities reduce downtime, improve security posture, and streamline support operations.

## Prerequisites

Each action has its own prerequisites, which the respective documentation details. In general:

- Devices must be enrolled in Intune.
- Devices must be connected to the Internet to receive remote commands.
- Some actions might require specific Intune roles or permissions.

## Available device actions

Microsoft Intune supports device actions across multiple platforms. The availability of specific actions depends on the platform and the device's configuration. This cross-platform support ensures that IT pros can manage a diverse device ecosystem with consistent tools and workflows.

Select one of the following tabs to learn more about the available device actions for each platform:

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/windows.svg)](#tabpanel_1_windows)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/apple-mobile.svg)](#tabpanel_1_apple-mobile)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/macos.svg)](#tabpanel_1_macos)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/android.svg)](#tabpanel_1_android)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/chromeos.svg)](#tabpanel_1_chromeos)

| Icon | Action | Description |
| :---: | --- | --- |
| ![autopilot-reset-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/autopilot-reset.svg) | [Autopilot reset](https://learn.microsoft.com/en-us/intune/device-management/actions/autopilot-reset) | Restores a device to its original settings and removes personal files, apps, and settings. |
| ![bitlocker-key-rotation-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/bitlocker-key-rotation.svg) | [BitLocker key rotation](https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-bitlocker-keys) | Rotates the BitLocker recovery key for a device. |
| ![collect-diagnostics-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/collect-diagnostics.svg) | [Collect diagnostics](https://learn.microsoft.com/en-us/intune/device-management/actions/collect-diagnostics) | Collects diagnostic logs from a device and uploads the logs to Intune. |
| ![delete-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/delete.svg) | [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| ![fresh-start-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/fresh-start.svg) | [Fresh Start](https://learn.microsoft.com/en-us/intune/device-management/actions/fresh-start) | Reinstalls the latest version of Windows on a device and removes apps that the manufacturer installed. |
| ![full-scan-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/full-scan.svg) | [Full Scan](https://learn.microsoft.com/en-us/intune/device-management/actions/full-scan) | Initiates a full scan of the device by Microsoft Defender Antivirus. |
| ![locate-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/locate-device.svg) | [Locate device](https://learn.microsoft.com/en-us/intune/device-management/actions/locate) | Shows the approximate location of a device on a map. |
| ![pause-config-refresh-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/pause-config-refresh.svg) | [Pause Config Refresh](https://learn.microsoft.com/en-us/intune/device-management/actions/pause-config-refresh) | Pauses ConfigRefresh to run remediation on a device for troubleshooting or maintenance or to make changes. |
| ![quick-scan-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/quick-scan.svg) | [Quick Scan](https://learn.microsoft.com/en-us/intune/device-management/actions/quick-scan) | Initiates a quick scan of the device by Microsoft Defender Antivirus. |
| ![new-remote-assistance-session-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/new-remote-assistance-session.svg) | [New remote assistance session](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-assist) | Allows you to remotely control a device by using [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/) or [TeamViewer](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy). |
| ![rename-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rename-device.svg) | [Rename device](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| ![restart-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restart.svg) | [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| ![retire-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/retire.svg) | [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| ![rotate-local-admin-password-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rotate-local-admin-password.svg) | [Rotate Local admin password](https://learn.microsoft.com/en-us/intune/device-security/laps/deploy-policy#manually-rotate-passwords) | Changes the local administrator password for a device and stores the password in Intune. |
| ![run-remediation-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/run-remediation.svg) | [Run remediation](https://learn.microsoft.com/en-us/intune/device-management/actions/run-remediation) | Initiates on demand Proactive Remediation |
| ![sync-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/sync.svg) | [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| ![update-defender-security-intelligence-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/update-defender-intelligence.svg) | [Update Windows Defender security intelligence](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-defender-antivirus/manage-protection-updates-windows-defender-antivirus) | Updates the security intelligence files for Microsoft Defender Antivirus. |
| ![wipe-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/wipe.svg) | [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

Tip

For Intel vPro devices, Intune also integrates with Intel vPro Fleet Services to provide hardware-level remote management capabilities, including out-of-band management that works even when the operating system is unresponsive or the device is powered off.

| Icon | Action | Description | iOS | iPadOS | tvOS | visionOS |
| :---: | --- | --- | :---: | :---: | :---: | :---: |
| ![delete-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/delete.svg) | [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| ![disable-activation-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/disable-activation-lock.svg) | [Disable Activation Lock](https://learn.microsoft.com/en-us/intune/device-management/actions/disable-activation-lock) | Removes the Activation Lock from a device that's enrolled with a device enrollment manager \(DEM\) account. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![locate-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/locate-device.svg) | [Locate device](https://learn.microsoft.com/en-us/intune/device-management/actions/locate) | Shows the approximate location of a device on a map. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![logout-current-user-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/logout-current-user.svg) | [Logout current user](https://learn.microsoft.com/en-us/intune/device-management/actions/logout-user) | Signs out the current user from a Shared iPad. |  | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![lost-mode-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/lost-mode.svg) | [Lost mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) | Locks a device with a custom message and disables sound and vibration. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![new-remote-assistance-session-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/new-remote-assistance-session.svg) | [New remote assistance session](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-assist) | Allows you to remotely control a device by using [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/) or [TeamViewer](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy). | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![play-lost-mode-sound-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/play-lost-mode-sound.svg) | [Play Lost Mode sound](https://learn.microsoft.com/en-us/intune/device-management/actions/play-lost-mode-sound) | Plays Lost Mode sound on a lost device to help locate it. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![remote-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remote-lock.svg) | [Remote lock](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-lock) | Locks a device and resets its password. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| ![remove-apps-and-configurations-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remove-apps-and-configurations.svg) | [Remove apps and configurations](https://learn.microsoft.com/en-us/intune/device-management/actions/remove-apps-config) | Temporarily removes applications and configuration from a device. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![remove-user-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remove-user.svg) | [Remove user](https://learn.microsoft.com/en-us/intune/device-management/actions/remove-user) | Deletes a user from the cache of a Shared iPad. |  | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![rename-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rename-device.svg) | [Rename device](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |
| ![remove-passcode-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remove-passcode.svg) | [Remove passcode](https://learn.microsoft.com/en-us/intune/device-management/actions/remove-passcode) | Removes the device passcode. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| ![restart-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restart.svg) | [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |
| ![retire-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/retire.svg) | [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| ![send-custom-notification-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/send-custom-notification.svg) | [Send custom notification](https://learn.microsoft.com/en-us/intune/device-management/actions/send-custom-notification) | Sends a custom notification message to a device that can be viewed in the Company Portal app. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![shut-down-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/shut-down.svg) | [Shut down](https://learn.microsoft.com/en-us/intune/device-management/actions/shutdown) | Shuts down a device. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![sync-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/sync.svg) | [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |
| ![update-cellular-data-plan-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/update-cellular-data-plan.svg) | [Update cellular data plan](https://learn.microsoft.com/en-us/intune/device-management/actions/update-cellular-data-plan) | Updates the cellular data plan settings for a device that uses an eSIM profile. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |  |  |
| ![wipe-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/wipe.svg) | [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) | ![Supported](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) |

| Icon | Action | Description |
| :---: | --- | --- |
| ![delete-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/delete.svg) | [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| ![disable-activation-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/disable-activation-lock.svg) | [Disable Activation Lock](https://learn.microsoft.com/en-us/intune/device-management/actions/disable-activation-lock) | Removes the Activation Lock from a device that's enrolled with a device enrollment manager \(DEM\) account. |
| ![new-remote-assistance-session-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/new-remote-assistance-session.svg) | [New remote assistance session](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-assist) | Allows you to remotely control a device by using [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/) or [TeamViewer](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy). |
| ![remote-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remote-lock.svg) | [Remote lock](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-lock) | Locks a device and resets its password. |
| ![rename-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rename-device.svg) | [Rename device](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| ![restart-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restart.svg) | [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| ![retire-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/retire.svg) | [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| ![rotate-filevault-recovery-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rotate-filevault-recovery.svg) | [Rotate FileVault recovery key](https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-filevault-recovery-key) | Rotates the FileVault recovery key. |
| ![rotate-recovery-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rotate-recovery-lock.svg) | [Rotate Recovery Lock passcode](https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-recovery-lock-passcode) | Rotates the Recovery Lock passcode. |
| ![sync-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/sync.svg) | [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| ![wipe-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/wipe.svg) | [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

| Icon | Action | Description |
| :---: | --- | --- |
| ![delete-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/delete.svg) | [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| ![locate-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/locate-device.svg) | [Locate device](https://learn.microsoft.com/en-us/intune/device-management/actions/locate) | Shows the approximate location of a device on a map. |
| ![new-remote-assistance-session-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/new-remote-assistance-session.svg) | [New remote assistance session](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-assist) | Allows you to remotely control a device by using [Remote Help](https://learn.microsoft.com/en-us/intune/remote-help/) or [TeamViewer](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy). |
| ![play-lost-mode-sound-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/play-lost-mode-sound.svg) | [Play lost device sound](https://learn.microsoft.com/en-us/intune/device-management/actions/play-lost-mode-sound) | Plays a sound on a lost device to help locate it. |
| ![remote-lock-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remote-lock.svg) | [Remote lock](https://learn.microsoft.com/en-us/intune/device-management/actions/remote-lock) | Locks a device and resets its password. |
| ![remove-apps-and-configurations-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/remove-apps-and-configurations.svg) | [Remove apps and configurations](https://learn.microsoft.com/en-us/intune/device-management/actions/remove-apps-config) | Temporarily removes applications and configuration from a device. |
| ![rename-device-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/rename-device.svg) | [Rename device](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| ![reset-passcode-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/reset-passcode.svg) | [Reset passcode](https://learn.microsoft.com/en-us/intune/device-management/actions/reset-passcode) | Resets the device passcode. |
| ![restart-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restart.svg) | [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| ![restore-managed-home-screen-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restore-managed-home-screen.svg) | [Restore managed home screen](https://learn.microsoft.com/en-us/intune/device-management/actions/restore-managed-home-screen) | Restores the managed home screen on a device. |
| ![retire-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/retire.svg) | [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| ![send-custom-notification-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/send-custom-notification.svg) | [Send custom notification](https://learn.microsoft.com/en-us/intune/device-management/actions/send-custom-notification) | Sends a custom notification message to a device that can be viewed in the Company Portal app. |
| ![suspend-managed-home-screen-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/suspend-managed-home-screen.svg) | [Suspend managed home screen](https://learn.microsoft.com/en-us/intune/device-management/actions/suspend-managed-home-screen) | Suspends the managed home screen on a device. |
| ![sync-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/sync.svg) | [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| ![wipe-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/wipe.svg) | [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

Note

To manage ChromeOS devices with Intune, you must first [set up the Chrome Enterprise connector](https://learn.microsoft.com/en-us/intune/device-enrollment/configure-chrome-enterprise-connector) and enroll devices by using the Google Admin console. This integration allows you to manage ChromeOS devices alongside other platforms in Intune.

| Icon | Action | Description |
| :---: | --- | --- |
| ![retire-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/retire.svg) | [Deprovision](https://learn.microsoft.com/en-us/intune/device-management/actions/deprovision) | Removes Google Admin policies from a ChromeOS device that you no longer use. |
| ![lost-mode-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/lost-mode.svg) | [Lost mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) | Locks a lost or stolen ChromeOS device and displays a custom message and contact info configured in the Google Admin Console. In Chrome Enterprise, this action is referred to as **Disabled**. |
| ![restart-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/restart.svg) | [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| ![wipe-icon](https://learn.microsoft.com/en-us/intune/device-management/actions/icons/wipe.svg) | [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Erases data from the device. You can choose to remove only user profiles or perform a full factory reset \(Powerwash\). A factory reset is required before re-enrollment. |

## Execute a device action from the Intune admin center

Every device action has its own steps, which the respective documentation details. In general:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, a row displays available device actions. Each icon represents a specific action \(such as **Restart**, **Wipe**, or **Locate device**\). Depending on your screen resolution or window size, the overflow menu \(**...**\) might hide some actions.
4. Select the desired action.
5. Complete any required fields, then confirm the action.

Note

The **Retire**, **Wipe**, and **Delete** actions take precedence over all other actions. A device with multiple pending actions only carries out a Retire, Wipe, or Delete. The system ignores all other pending actions.

## Daily tenant limits

Intune limits the number of Wipe, Retire, and Delete device actions that can be submitted in a tenant each day.

| Device action | Daily limit per tenant |
| --- | ---: |
| Wipe | 500 |
| Retire | 1,000 |
| Delete | 1,000 |

The limit for each action is cumulative across all submission methods, including actions for individual devices, bulk device actions, and Microsoft Graph API requests. To request a change to one of these limits, [contact Microsoft support](https://learn.microsoft.com/en-us/intune/fundamentals/it-pro-support/get-support-admin-center).

## Check the status of the action

To check the status of the action, select **Devices** > [**Device actions**](https://go.microsoft.com/fwlink/?linkid=2109431#view/#view/Microsoft_Intune_Devices/DeviceActionList.ReactView).

Note

For **MDM devices**, deleting a device immediately hides it from the admin center and initiates a **Retire**. A status of **Completed** on a delete action means the process is complete on the server side; it doesn't confirm that the client device finished the **Retire**.

## Bulk device actions

Managing devices at scale is a common challenge for IT pros, especially in environments like schools, enterprises, or frontline operations. Microsoft Intune supports bulk device actions, so IT admins can perform tasks on up to 100 devices at the same time. This capability streamlines operations, reduces manual effort, and ensures consistent policy enforcement across large device fleets.

Note

Bulk Wipe, Retire, and Delete requests count toward the [daily tenant limit](#daily-tenant-limits) for each action.

For example, at the end of a school year, IT admins can use bulk wipe to securely reset student devices before reassigning them for the next term. This approach saves time and ensures that sensitive data is removed efficiently across all devices.

Select one of the following tabs to learn more about the available bulk device actions for each platform:

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/windows.svg)](#tabpanel_2_windows)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/apple-mobile.svg)](#tabpanel_2_apple-mobile)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/macos.svg)](#tabpanel_2_macos)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/android.svg)](#tabpanel_2_android)

- 

  [![](https://learn.microsoft.com/en-us/intune/media/icons/16/chromeos.svg)](#tabpanel_2_chromeos)

| Bulk action | Description |
| --- | --- |
| [Autopilot reset](https://learn.microsoft.com/en-us/intune/device-management/actions/autopilot-reset) | Restores a device to its original settings and removes personal files, apps, and settings. |
| [Collect diagnostics](https://learn.microsoft.com/en-us/intune/device-management/actions/collect-diagnostics) | Collects diagnostic logs from a device and uploads the logs to Intune. |
| [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| [Rename](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to the factory settings and removes all data and settings. |

| Bulk action | Description |
| --- | --- |
| [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| [Rename](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| [Send custom notification](https://learn.microsoft.com/en-us/intune/device-management/actions/send-custom-notification) | Sends a custom notification message to a device that can be viewed in the Company Portal app. |
| [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| [Update cellular data plan](https://learn.microsoft.com/en-us/intune/device-management/actions/update-cellular-data-plan) | Updates the cellular data plan settings for a device that uses an eSIM profile. |
| [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

| Bulk action | Description |
| --- | --- |
| [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| [Rename device](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| [Retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) | Removes company data and settings from a device, and leaves personal data intact. |
| [Sync](https://learn.microsoft.com/en-us/intune/device-management/actions/sync) | Syncs a device with Intune to apply the latest policies and configurations. |
| [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

| Bulk action | Description |
| --- | --- |
| [Activate eSIM](https://learn.microsoft.com/en-us/intune/device-management/actions/update-cellular-data-plan#activate-esims-on-multiple-android-enterprise-devices) | Activates eSIMs on supported corporate-owned Android Enterprise devices. |
| [Delete](https://learn.microsoft.com/en-us/intune/device-management/actions/delete) | Removes a device from Intune management, removes any company data, and retires the device. |
| [Rename](https://learn.microsoft.com/en-us/intune/device-management/actions/rename) | Changes the device name in Intune. |
| [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Restores a device to its factory settings and removes all data and settings. |

| Bulk action | Description |
| --- | --- |
| [Deprovision](https://learn.microsoft.com/en-us/intune/device-management/actions/deprovision) | Removes Google Admin policies from a ChromeOS device that you no longer use. |
| [Lost mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) | Locks a lost or stolen ChromeOS device and displays a custom message and contact info configured in the Google Admin Console. In Chrome Enterprise, this action is referred to as **Disabled**. |
| [Restart](https://learn.microsoft.com/en-us/intune/device-management/actions/restart) | Restarts a device. |
| [Wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) | Erases data from the device. You can choose to remove only user profiles or perform a full factory reset \(Powerwash\). A factory reset is required before re-enrollment. |

## Execute a bulk device action

Each bulk action has its own steps. The documentation for each action provides detailed instructions. In general, follow these steps:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices) > [**Bulk device actions**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_Devices/BulkActionWizardBlade).
2. On the **Basics** page, select an **OS** and **Device action** from the dropdowns. Some device actions have more options or fields to fill in. Select **Next**.
3. On the **Devices** page, select up to the maximum number of devices that the action supports. Select **Next**.
4. On the **Review + create** page, select **Create**.

## Next steps

Device actions in Intune empower IT pros to manage devices efficiently and securely—whether individually or at scale. Explore the documentation linked in this article to learn more about each action and how to integrate them into your device management workflows.
