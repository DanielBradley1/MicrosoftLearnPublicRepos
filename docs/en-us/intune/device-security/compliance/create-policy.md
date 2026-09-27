<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/compliance/create-policy -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Create a compliance policy in Microsoft Intune

Device compliance policies are a key feature when using Intune to protect your organization's resources. In Intune, you can create rules and settings that devices must meet to be considered compliant, such as a minimum OS version. If the device isn't compliant, you can block access to data and resources by using [Conditional Access](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview).

You can also take actions for noncompliance, such as sending a notification email to the user. For an overview of what compliance policies do, and how they're used, see [get started with device compliance](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview).

This article:

- Lists the prerequisites and steps to create a compliance policy.
- Shows you how to assign the policy to your user and device groups.
- Describes other features, including scope tags to "filter" your policies, and steps you can take on devices that aren't compliant.
- Lists the check-in refresh cycle times when devices receive policy updates.

## Requirements

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - Microsoft Intune subscription
> - If you use Conditional Access, then you need Microsoft Entra ID P1 or P2 edition. [Microsoft Entra pricing](https://azure.microsoft.com/pricing/details/active-directory/) lists what you get with the different editions. Intune compliance doesn't require Microsoft Entra ID.

> - Android device administrator
> - Android AOSP
> - Android Enterprise
> - iOS
> - Linux - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
> - macOS
> - Windows

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/enrollment.svg) **Enrollment methods**

> - Enroll devices in Intune \(required to see the compliance status\)
> - Enroll devices to one user, or enroll without a primary user. Single devices can't be enrolled to multiple users.

In addition to compliance settings that are built in to Intune, the following platforms support adding custom compliance settings to compliance policies:

- Linux

  - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
  - RedHat Enterprise Linux 9 or 10

- Windows

Before you can add custom settings, you must prepare a custom JSON file that defines the settings you want to base your custom compliance on, and a script that runs on devices to detect the settings defined in the JSON.

For more information about using custom compliance settings, including supported platforms, prerequisites, and how to configure the *Custom Compliance* category while creating a policy, see [Use custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/custom-settings).

## Create the policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Under **Manage devices**, select **Compliance**. Then choose **Create policy**.
4. Select a **Platform** for this policy from the following options:

   - **Android device administrator**
   - **Android \(AOSP\)**
   - **Android Enterprise**
   - **iOS/iPadOS**
   - **Linux** - \(Ubuntu Desktop, version 24.04 LTS or 26.04 LTS, RedHat Enterprise Linux 9, or RedHat Enterprise Linux 10\)
   - **macOS**
   - **Windows 10 and later**
   - **Windows 8.1 and later**


   For *Android Enterprise*, also select a **Profile type**. Your options:


   - **Fully managed, dedicated, and corporate-owned work profile**
   - **Personally-owned work profile**


   Then select **Create** to open the configuration page.

5. On the **Basics** tab, enter a **Name** that helps you identify this policy later. For example, a good policy name is **Mark iOS/iPadOS jailbroken devices as not compliant**.

   Optionally, enter a **Description** for the policy.
6. On the **Compliance settings** tab, expand the available categories, and configure settings for your policy. The following articles describe the available compliance settings for each platform:

   - [Android device administrator](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-administrator-settings)
   - [Android \(AOSP\)](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-aosp-settings)
   - [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-enterprise-settings)
   - [iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-ios-ipados-settings)
   - [Linux](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-linux-settings)
   - [macOS](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-macos-settings)
   - [Windows 8.1 and later](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-windows-8-1-settings)
   - [Windows](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-windows-settings)

7. Optionally, add custom settings for supported platforms.

   Tip

   This step is optional and supported for the following platforms:

   - Linux

     - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
     - RedHat Enterprise Linux 9 or 10

   - macOS
   - Windows Before you can add custom settings to a policy, upload a detection script to Intune, and have a JSON file that defines the settings you want to use for compliance. For more information, see [Custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/custom-settings).


   On the **Compliance settings** page, expand the **Custom Compliance** category:


   **For Windows**:


   1. On the *Compliance settings* page, expand **Custom Compliance** and set *Custom compliance* to **Require**.
   2. For *Select your discovery script*, select **Click to select**, and then enter the name of a script that you previously added to the Microsoft Intune admin center. This script must be uploaded before you begin to create the policy. Choose **Select** to continue to the next step.
   3. For *Upload and validate the JSON file with your custom compliance settings*, select the folder icon, and then find and add the JSON file for Windows that you want to use with this policy. For assistance with the JSON, see [Create a JSON for custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-custom-json).


   **For Linux and macOS**:


   1. On the *Compliance settings* page, select **Add settings** to open the **Settings picker**.
   2. Select **Custom Compliance**. Then close the settings picker.
   3. Switch **Require Custom Compliance** to **True**.
   4. For **Select your discovery script**, select **Select a script**. Then select a script that’s been previously added to the Microsoft Intune admin center. This script must be uploaded before you begin to create the policy.
   5. For **Select your rules file**, select the folder icon and then locate and add the JSON file that you want to use with this policy. For assistance with the JSON, see [Create a JSON for custom compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-custom-json).


   Wait while Intune validates the JSON. Problems that need to be fixed appear onscreen. After validation of the JSON contents, the rules from the JSON appear in table format.

8. On the **Actions for noncompliance** tab, select a sequence of actions to apply automatically to devices that don't meet this compliance policy.

   You can add multiple actions, and configure schedules and details for some actions. For example, you might change the schedule of the default action *Mark device noncompliant* to occur after one day. You can then add an action to send an email to the user when the device isn't compliant to warn them of that status. You can also add actions that lock or retire devices that remain noncompliant.

   For information about the actions you can configure, see [Add actions for noncompliant devices](https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-noncompliance-actions), including how to create notification emails to send to your users.

   Another example includes the use of Locations where you add at least one location to a compliance policy. In this case, the default action for noncompliance applies when you select at least one location. If the device isn't connected to any of the selected locations, it's considered not compliant. You can configure the schedule to give your users a grace period, such as one day.
9. On the **Scope tags** tab, select tags to help filter policies to specific groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. After you add the settings, you can also add a scope tag to your compliance policies.

   For information on using scope tags, see [Use scope tags to filter policies](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).
10. On the **Assignments** tab, assign the policy to your groups.

    Select **Add groups**, and then assign the policy to one or more groups. The policy applies to these groups when you save the policy after the next step.

    Policies for Linux don't support user-based assignments and can only be assigned to device groups.
11. On the **Review + create** tab, review the settings and select **Create** when ready to save the compliance policy.

    Intune evaluates the users or devices targeted by your policy for compliance when they check in with Intune.

## Refresh cycle times

Intune uses different refresh cycles to check for updates to compliance policies. If the device recently enrolled, the check-in runs more frequently. [Policy and profile refresh cycles](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals) lists the estimated refresh times.

At any time, users can open the Company Portal app, and sync the device to immediately check for policy updates.

### Client-driven compliance evaluation

For supported Windows devices, Intune supports client-driven compliance evaluation. With this capability, a device can detect certain local state changes and proactively request a compliance re-evaluation, rather than waiting for the next scheduled check-in cycle.

State changes that can trigger a client-driven compliance evaluation include changes to device configuration, security posture, and other settings that affect a device's compliance state. For more information, see [How compliance calculation is triggered on Windows devices](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-windows-settings#compliance-recalculation-triggers).

### Assign an InGracePeriod status

The InGracePeriod status for a compliance policy is a value. This value is determined by the combination of a device's grace period, and a device's actual status for that compliance policy.

Specifically, if a device has a NonCompliant status for an assigned compliance policy, and:

- The device has no grace period assigned to it, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's expired, then the assigned value for the compliance policy is NonCompliant
- The device has a grace period that's in the future, then the assigned value for the compliance policy is InGracePeriod

The following table summarizes these points:

| Actual compliance status | Value of assigned grace period | Effective compliance status |
| --- | --- | --- |
| NonCompliant | No grace period assigned | NonCompliant |
| NonCompliant | Yesterday's date | NonCompliant |
| NonCompliant | Tomorrow's date | InGracePeriod |

For more information about monitoring device compliance policies, see [Monitor Intune Device compliance policies](https://learn.microsoft.com/en-us/intune/device-security/compliance/monitor-policy).

### Assign a resulting compliance policy status

If a device has multiple compliance policies, and the device has different compliance statuses for two or more of the assigned compliance policies, then a single resulting compliance status is assigned. This assignment is based on a conceptual severity level assigned to each compliance status. Each compliance status has the following severity level:

| Status | Severity |
| --- | --- |
| Unknown | 1 |
| NotApplicable | 2 |
| Compliant | 3 |
| InGracePeriod | 4 |
| NonCompliant | 5 |
| Error | 6 |

When a device has multiple compliance policies, Intune assigns the highest severity level of all the policies to that device.

For example, a device has three compliance policies assigned to it: one Unknown status \(severity = 1\), one Compliant status \(severity = 3\), and one InGracePeriod status \(severity = 4\). The InGracePeriod status has the highest severity level, so the device is given the InGracePeriod compliance status.

Important

Discovery script output is limited to 2048 characters. If the output exceeds this limit, it may be truncated, resulting in invalid JSON and error 65009 during compliance evaluation. To avoid this, keep outputs concise or split large rule sets across multiple policies.

## Next steps

[Monitor your policies](https://learn.microsoft.com/en-us/intune/device-security/compliance/monitor-policy).
