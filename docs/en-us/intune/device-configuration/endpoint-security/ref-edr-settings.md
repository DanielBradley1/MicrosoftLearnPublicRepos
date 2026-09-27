<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-edr-settings -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Endpoint detection and response policy settings for endpoint security in Intune

Important

On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Note

The information in this article applies only to the settings in the Endpoint detection and response profile for the *Windows 10 and later* platform for endpoint security Endpoint detection and response policy.

Beginning on April 5, 2022, the *Windows 10 and later* platform was replaced by the *Windows* platform. Although you can no longer create a new instance of this older profile, you can continue to edit and use an existing instances of this profile. The settings details in this article apply only to the deprecated profiles.

View the settings you can configure in profiles for [Endpoint detection and response policy](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/deploy-edr) in the endpoint security node of Intune.

Applies to:

- Windows

  Important

  On October 14, 2025, [Windows 10 reached end of support](https://learn.microsoft.com/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

Supported platforms and profiles:

- **Windows**: Use this platform for policy you deploy to Windows devices managed with Intune.

  - Profile: **Endpoint detection and response \(MDM\)**

- **Windows \(ConfigMgr\)**: Use this platform for policy you deploy to devices managed by Configuration Manager.

  - Profile: **Endpoint detection and response \(ConfigMgr\)**

## Endpoint detection and response \(MDM\)

**Endpoint detection and response**:

- **Microsoft Defender for Endpoint client configuration package type**

  Upload a signed configuration package that will be used to onboard the Microsoft Defender for Endpoint client.

  - **Not configured** \(*default*\)
  - **Onboarding blob**
  - **Offboarding blob**


  When set to *Onboarding blob*, you can configure the following settings:


  - **Defender for Endpoint onboarding blob** Click **Select onboarding file** to open the *Select onboarding File* pane, where you specify a `.onboarding` file.


  When set to *Offboarding blob*, you can configure the following settings:


  - **Defender for Endpoint offboarding blob** Click **Select offboarding file** to open the *Select offboarding File* pane, where you specify a `.offboarding` file.

- **Sample sharing for all files**

  Returns or sets the Microsoft Defender for Endpoint Sample Sharing configuration parameter. Sample Sharing sends a file to Microsoft for deep analysis. Organizations can disable sample sharing on specific devices that are considered too sensitive.

  - **Not configured** \(*default*\)
  - **Yes**

- **Expedite telemetry reporting frequency**

  - **Not configured** \(*default*\)
  - **Yes** - Increase the Microsoft Defender for Endpoint telemetry reporting frequency.

## Endpoint detection and response \(ConfigMgr\)

**Endpoint detection and response**:

- **Sample sharing for all files**

  Returns or sets the Microsoft Defender for Endpoint Sample Sharing configuration parameter.

  - **Not configured** \(*default*\)
  - **Yes**

- **Expedite telemetry reporting frequency**

  - **Not configured** \(*default*\)
  - **Yes** - Increase the Microsoft Defender for Endpoint telemetry reporting frequency.

## Next steps

[Endpoint security policy for EDR](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/deploy-edr)
