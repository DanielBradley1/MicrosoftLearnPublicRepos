<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Assign policies in Microsoft Intune

When you create an Intune policy, it includes all the settings you added and configured within the policy. When the policy is ready to be deployed, the next step is to "assign" the policy to your user or device groups. When you assign the policy, the users and devices receive your policy, and the settings you entered are applied.

In Intune, you can create and assign the following policies:

- App protection policies
- App configuration policies
- Compliance policies
- Conditional Access policies
- Device configuration profiles
- Enrollment policies

This article shows you how to assign a policy, includes some information on using scope tags, describes when to assign policies to user groups or device groups, and more.

This feature applies to:

- Android
- iOS/iPadOS
- macOS
- Linux
- Windows

## Before you begin

- Be sure you have the correct role that can assign policies and profiles. For more information, go to [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).
- Consider using [Microsoft Copilot in Intune](https://learn.microsoft.com/en-us/intune/copilot/). Some benefits include:

  - When you create a policy and configure settings, Copilot provides more information on each setting and find potential conflicts.
  - When you assign a policy, Copilot can tell you the groups the policy is assigned to and help you understand the effect of the policy.


  For more information, go to [Copilot in Intune](https://learn.microsoft.com/en-us/intune/copilot/).

## Assign a policy to users or groups

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration**. All the profiles are listed.
3. Select the profile you want to assign > **Properties** > **Assignments** > **Edit**:

   For example, to assign a device configuration profile:

   1. Go to **Devices** > **Manage devices** > **Configuration**. All the profiles are listed.
   2. Select the policy you want to assign > **Properties** > **Assignments** > **Edit**:

      ![Screenshot that shows how to select assignments to deploy the profile to users and groups in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/device-configuration/media/assign-device-profile/properties-select-assignments.png)

4. Under **Included groups** or **Excluded groups**, choose **Add groups** to select one or more Microsoft Entra groups. If you intend to deploy the policy broadly to all applicable devices, select **Add all users** or **Add all devices**.

   Note

   If you select "All Devices" and "All Users", the option to add additional Microsoft Entra groups disables.
5. Select **Review + Save**. This step doesn't assign your policy.
6. Select **Save**. When you save, your policy is assigned. Your groups will receive your policy settings when the devices check in with the Intune service.

## Assignment features you should know and use

- Use **[assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview)** to assign a policy based on rules you create. You can create assignment filters for:

  - App configuration policies
  - App protection policies
  - App assignments
  - Compliance policies
  - Device configuration profiles


  For more information, go to:


  - [Use assignment filters when assigning your apps, policies, and profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview)
  - [Platforms, policies, and app types supported by assignment filters in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/filters/ref-supported-workloads)

- **[Policy sets](https://learn.microsoft.com/en-us/intune/fundamentals/policy-sets)** create a group or collection of existing apps and policies. When the policy set is created, you can assign the policy set from a single place in the Microsoft Intune admin center.

  For more information, go to [Use policy sets to group collections of management objects in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/policy-sets).
- **[Scope tags](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags)** are a great way to filter policies to specific groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information, go to [Use RBAC and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).
- On Windows devices, you can add **[applicability rules](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile#applicability-rules)** so the policy only applies to a specific OS version or a specific Windows edition. For more information, go to [Applicability rules](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile#applicability-rules).

## User groups vs. device groups

Many users ask when to use user groups and when to use device groups. The answer depends on your goal. Here's some guidance to get you started.

### Device groups

If you want to apply settings on a device, regardless of who's signed in, then assign your policies to a devices group. Settings applied to device groups always go with the device, not the user.

For example:

- Device groups are useful for managing devices that don't have a dedicated user. These devices can print tickets, scan inventory, be shared by shift workers & health workers, and so on. Put these devices in a devices group and assign your policies to this devices group.

  For example, you can enroll userless iOS/iPadOS devices using [Shared iPad](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/shared-ipad) or [Microsoft Entra Shared Device Mode](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-shared-device-mode). Then, add these devices to a devices group. When you're ready to assign policies, assign the policies to this devices group.
- You create a [Device Firmware Configuration Interface \(DFCI\) Intune profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-dfci-windows) that updates settings in the BIOS. For example, you configure this policy to disable the device camera, or lock down the boot options to prevent users from booting up another OS. This policy is a good scenario to assign to a devices group.
- On some specific Windows devices, you always want to control some Microsoft Edge settings, regardless of who's using the device. For example, you want to block all downloads, limit all cookies to the current browsing session, and delete the browsing history. For this scenario, put these specific Windows devices in a devices group. Then, create a [settings catalog policy in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/), add these device settings, and then assign this policy to the devices group.

To summarize, use device groups when you don't care who's signed in on the device, or if anyone signs in. You want your settings to always be on the device.

### User groups

Policy settings applied to user groups always go with the user, and go with the user when signed in to their many devices. It's normal for users to have many devices, such as a Surface Pro for work, and a personal iOS/iPadOS device. And, it's normal for a person to access email and other organization resources from these devices.

If a user has multiple devices on the same platform, then you can use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) on the group assignment. For example, a user has a personal iOS/iPadOS device, and an organization-owned iOS/iPadOS. When you assign a policy for that user, you can use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to target only the organization-owned device.

Follow this general rule: If a feature belongs to a user, such as email or user certificates, then assign to user groups.

For example:

- You want to put a Help Desk icon for all users on all their devices. In this scenario, put these users in a users group, and assign your Help Desk icon policy to this users group.
- A user receives a new organization-owned device. The user signs in to the device with their domain account. The device is automatically registered in Microsoft Entra ID, and automatically managed by Intune. This policy is a good scenario to assign to a users group.
- Whenever a user signs in to a device, you want to control features in apps, such as OneDrive or Office. In this scenario, assign your OneDrive or Office policy settings to a users group.

  For example, you want to disable all ActiveX controls in your Office apps. You can create a [settings catalog policy in Intune](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/), configure this setting, and then assign this policy to a users group.

To summarize, use user groups when you want your settings and rules to always go with the user, whatever device they use.

### Azure Virtual Desktop multi-session

You can use Intune to manage Windows multi-session remote desktops created with Azure Virtual Desktop, just like you manage any other shared Windows client device. When you assign policies to user groups or devices, Azure Virtual Desktop multi-session is a special scenario. With virtual machines, device CSPs must target device groups. User CSPs must target user groups.

For more information, go to [Use Azure Virtual Desktop multi-session with Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop-multi-session).

### Windows CSPs and their behavior

The policy settings for Windows devices are based on the [configuration service providers \(CSPs\)](https://learn.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference). These settings map to registry keys or files on the devices.

Here's what you need to know about Windows CSPs:

- Intune exposes these CSPs so you can configure these settings and assign them to your Windows devices. These settings are configurable using the built-in templates and using the [settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/). In the settings catalog, you see that some settings apply to the user scope and some settings apply to the device scope.

  For information on how user scoped and device scoped settings are applied to Windows devices, go to [Settings catalog: Device scope vs. user scope settings](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/#device-scope-vs-user-scope-settings).
- When a policy is removed or no longer assigned to a device, different things can happen, depending on the settings in the policy. Each CSP can handle the policy removal differently.

  For example, a setting might keep the existing value, and not revert back to a default value. Each CSP controls the behavior. For a list of Windows CSPs, see [configuration service provider \(CSP\) reference](https://learn.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference).

  To change a setting to a different value, create a new policy, configure the setting to **Not configured**, and assign the policy. When the policy applies to the device, users should have control to change the setting to their preferred value.
- When configuring these settings, we suggest deploying to a pilot group. For more Intune rollout advice, see [create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide).

## Exclude groups from a policy assignment

Intune device configuration policies let you include and exclude groups from policy assignment.

As a best practice:

- Create and assign policies specifically for your user groups. Use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to include or exclude devices of those users.
- Create and assign different policies specifically for your device groups.

For more information on groups, see [Add groups to organize users and devices](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-groups).

### Principles of including and excluding groups

When you assign your policies and policies, apply the following general principles:

- Think of **Included groups** or **Excluded groups** as a starting point for the users and devices that will receive your policies. The Microsoft Entra group is the limiting group, so use the smallest group scope possible. Use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to limit or refine your policy assignment.
- Assigned Microsoft Entra groups, also known as static groups, can be added to Included groups or Excluded groups.

  Typically, you statically assign devices into a Microsoft Entra group if they're pre-registered in Microsoft Entra ID, like with Windows Autopilot. Or, if you want to combine devices for a one-off, ad-hoc deployment. Otherwise, it might not be practical to statically assign devices into a Microsoft Entra group.
- Dynamic Microsoft Entra user groups can be added to Included groups or Excluded groups.
- Excluded groups can be groups with users or groups with devices.
- Dynamic Microsoft Entra device groups can be added to Included groups. But, dynamic group membership requires processing time before devices appear in the group. In time-sensitive scenarios, use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to target specific devices directly at check-in, and assign your policies to user groups or the *All devices* virtual group.

  Tip

  If your dynamic device group rule targets properties like OS type, manufacturer, model, ownership, or device category, consider using an [assignment filter](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) instead. Filters evaluate device properties directly at check-in without depending on group membership processing. For guidance, go to [Performance recommendations for grouping, targeting, and filtering](https://learn.microsoft.com/en-us/intune/fundamentals/filters/performance-recommendations).

  If you continue to use dynamic groups, optimize your rules for efficiency. For more information, go to:

  - [Create simpler and faster rules for dynamic membership groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-rule-more-efficient)
  - [Understand and manage dynamic group processing](https://learn.microsoft.com/en-us/entra/identity/users/manage-dynamic-group#optimize-rule-efficiency)


  For example, you want policies assigned to devices as soon as they enroll. In this latency-sensitive situation, create an [assignment filter](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to target the devices you want, and assign the policy with this assignment filter to user groups. Don't assign to device groups.


  In a userless scenario, create an [assignment filter](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) to target the devices you want, and assign the policy with the assignment filter to the "All devices" group.

- Avoid adding dynamic Microsoft Entra device groups to Excluded groups. Latency in dynamic device group calculation at enrollment can cause undesirable results. For example, unwanted apps and policies might be deployed before the excluded group membership is populated.

### Support matrix

Use the following matrix to understand support for excluding groups:

- ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg): Supported
- ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg): Not supported
- ![info-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/info-gray.svg): Partially supported

[![Screenshot that shows the supported options to include or exclude groups from a policy assignment.](https://learn.microsoft.com/en-us/intune/device-configuration/media/assign-device-profile/include-exclude-user-device-groups-matrix.png)](https://learn.microsoft.com/en-us/intune/device-configuration/media/assign-device-profile/include-exclude-user-device-groups-matrix.png#lightbox)

| Scenario | Support |
| --- | --- |
| 1 | ![info-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/info-gray.svg) Partially supported  <br>  <br>Assigning policies to a dynamic device group while excluding another dynamic device group is supported. But, it's not recommended in scenarios that are sensitive to latency. Any delay in exclude group membership calculation can cause policies to be offered to devices. In this scenario, we recommend using [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) instead of dynamic device groups for excluding devices.  <br>  <br>For example, you have a device policy that's assigned to **All devices**. Later, you have a requirement that new marketing devices don't receive this policy. So, you create a dynamic device group called **Marketing devices** based on the `enrollmentProfilename` property \(`device.enrollmentProfileName -eq "Marketing_devices"`\). In the policy, you add the **Marketing devices** dynamic group as an excluded group.  <br>  <br>A new marketing device enrolls in Intune for the first time, and a new Microsoft Entra device object is created. The dynamic grouping process puts the device into the **Marketing devices** group with a possible delayed calculation. At the same time, the device enrolls into Intune, and starts receiving all applicable policies. The Intune policy can be deployed before the device is put in the exclusion group. This behavior results in an unwanted policy \(or app\) being deployed to the **Marketing devices** group.  <br>  <br>As a result, it's not recommended to use dynamic device groups for exclusions in latency sensitive scenarios. Instead, use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview). |
| 2 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a dynamic device group while excluding a static device group is supported. |
| 3 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a dynamic device group while excluding user groups \(both dynamic and static\) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 4 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a dynamic device group and excluding user groups \(both dynamic and static\) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 5 | ![info-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/info-gray.svg) Partially supported  <br>  <br>Assigning a policy to a static device group while excluding a dynamic device group is supported. But, it's not recommended in scenarios that are sensitive to latency. Any delay in exclude group membership calculation can cause policies to be offered to devices. In this scenario, we recommend using [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) instead of dynamic device groups for excluding devices. |
| 6 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a static device group and excluding a different static device group is supported. |
| 7 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a static device group and excluding user groups \(both dynamic and static\) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 8 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a static device group and excluding user groups \(both dynamic and static\) isn't supported. Intune doesn't evaluate user-to-device group relationships, and devices of the included users aren't excluded. |
| 9 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a dynamic user group and excluding device groups \(both dynamic and static\) isn't supported. |
| 10 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a dynamic user group and excluding device groups \(both dynamic and static\) isn't supported. |
| 11 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a dynamic user group while excluding other user groups \(both dynamic and static\) is supported. |
| 12 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a dynamic user group while excluding other user groups \(both dynamic and static\) is supported. |
| 13 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a static user group while excluding device groups \(both dynamic and static\) isn't supported. |
| 14 | ![error-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/error.svg) Not supported  <br>  <br>Assigning a policy to a static user group while excluding device groups \(both dynamic and static\) isn't supported. |
| 15 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a static user group while excluding other user groups \(both dynamic and static\) is supported. |
| 16 | ![check-icon](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Supported  <br>  <br>Assigning a policy to a static user group while excluding other user groups \(both dynamic and static\) is supported. |

## Related articles

- [Choose the right targeting method in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/choose-targeting-method)
- [Monitor device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile) for guidance on monitoring your policies, and the devices running your policies. See [monitor device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile) for guidance on monitoring your policies, and the devices running your policies.
