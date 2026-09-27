<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-security-experience-settings-windows -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Settings for the Windows Security experience profile in Microsoft Intune

Important

On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

This article details the settings in the Windows Security experience profile for the *Windows 10 and later* platform for endpoint security Antivirus policy. Beginning on April, 5 2022, the *Windows 10 and later* platform was replaced by the *Windows* platform. Although you can no longer create new instances of the original profile, you can continue to edit and use your existing profiles.

**Windows Security**:

- **Enable tamper protection to prevent Microsoft Defender being disabled**  
  [Prevent changes to security settings with Tamper Protection](https://go.microsoft.com/fwlink/?linkid=2066083)

  - **Not configured** \(*default*\) - When the *Enable* or *Disable* state exists on a client, deploying *Not configured* has no impact on the setting.
  - **Enable** - Enable the Tamper Protection restriction. To change the state from either enabled or disabled, deploy the opposite setting to have effect.
  - **Disable** - Disable the Tamper Protection restrictions. To change the state from either enabled or disabled, deploy the opposite setting to have effect.


  **Hide the Virus and threat protection area in the Windows Security app**  
  CSP: [DisableVirusUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablevirusui)


  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The virus and threat protection area in the Windows Security app is hidden from end-users. Virus and threat protection-related notifications are suppressed.
  - **No** - Behavior is the same as *Not configured*.


  When this setting is configured as *No* or *Not configured*, the following setting is available:


  - **Hide the Ransomware data recovery option in the Windows Security app**  
    CSP: [HideRansomwareDataRecovery](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-hideransomwaredatarecovery)

    This setting is only available when *Hide the Virus and threat protection area in the Windows Security app* is set to *No* or *Not configured*.

    - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
    - **Yes** - The ransomware data recovery area in the Windows Security app is hidden from end-users. Ransomware related notifications are suppressed.
    - **No** - Behavior is the same as *Not configured*.

- **Hide the Account protection area in the Windows Security app**  
  CSP: [DisableAccountProtectionUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableaccountprotectionui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The account protection area in the Windows Security app is hidden from end-users. Account protection-related notifications are suppressed.
  - **No** - Behavior is the same as *Not configured*.

- **Hide the Firewall and network protection area in the Windows Security app**  
  CSP: [DisableNetworkUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenetworkui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The firewall and network protection area in the Windows Security are hidden from end-users. Firewall and network protection-related notifications are suppressed.
  - **No** - Behavior is the same as *Not configured*.

- **Hide the App and browser control area in the Windows Security app**  
  CSP: [DisableAppBrowserUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disableappbrowserui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The app and browser control area in the Windows Security is hidden from end-users. App and browser control related notifications are suppressed.
  - **No** - Behavior is the same as *Not configured*.

- **Hide the Device security area in the Windows Security app**  
  CSP: [DisableDeviceSecurityUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disabledevicesecurityui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The hardware protection area in the Windows Security app is hidden from end-users. Hardware protection-related notifications will be suppressed.
  - **No** - Behavior is the same as *Not configured*.

- **Hide the Device performance and health area in the Windows Security app**  
  CSP: [DisableHealthUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablehealthui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The device performance and health area in the Windows Security app are hidden from end-users. Device performance and health-related notifications ware suppressed
  - **No** - Behavior is the same as *Not configured*.

- **Hide the Family options area in the Windows Security app**  
  CSP: [DisableFamilyUI](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablefamilyui)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to allow user access and notifications.
  - **Yes** - The family options area in the Windows Security app is hidden from end-users. Also, notifications related to family options are suppressed.
  - **No** - Behavior is the same as *Not configured*.

- **Windows Security app notifications**  
  CSP: [DisableNotifications](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disablenotifications)

  Use this setting to block Windows Security notifications to your users for all of the preceding feature settings. Alternatively, you can manage the Windows Security app notifications per feature by using the proceeding settings.

  - **Not configured** \(*default*\) - This setting doesn't enforce a block of any settings and all Windows Security app notifications that are not controlled by another setting are allowed.
  - **Block non-critical notification** - Notifications such as scan completions are blocked.
  - **Block all notifications** - Critical and non-critical notifications are blocked for all Windows Security features.

- **Hide the Windows Security icon from the notification area**  
  CSP: [HideWindowsSecurityNotificationAreaControl](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

  For this setting to take effect, the user needs to either sign out and back in, or reboot the computer.

  - **Not configured** \(*default*\) - The setting returns the client to the default, which is to show the icon.
  - **Yes** - Hide the Windows Security icon from the notification area.
  - **No** - Behavior is the same as *Not configured*.

- **Disable the Clear TPM option in the Windows Security app**  
  CSP: [DisableClearTpmButton](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

  - **Not configured** \(*default*\) - The setting returns to the client default, which allows access to the button.
  - **Yes** - Disable access to the clear TPM button in the Windows Security app.
  - **No** - Behavior is the same as *Not configured*.

- **Prompt users to update TPM firmware if vulnerability is discovered**  
  CSP: [DisableTpmFirmwareUpdateWarning](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter)

  - **Not configured** \(*default*\) - The setting returns to the client default, which is to not prompt users.
  - **Yes** - Allow Windows to prompt end-users when a potential vulnerability is found in their TPM firmware. Users are then encouraged to run firmware updates to resolve the vulnerability.
  - **No** - Behavior is the same as *Not configured*.

- **Organization's support contact information**  
  CSP: [EnableCustomizedToasts](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-enablecustomizedtoasts)

  Declare where you would like your IT organization information displayed in the Windows Security app and notifications.

  - **Not configured** \(*default*\)
  - **Display in app and in notifications**
  - **Display only in app**
  - **Display only in notifications**
