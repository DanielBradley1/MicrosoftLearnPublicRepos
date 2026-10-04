<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/endpoint-security-policies-configure -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Manage endpoint security policies in Microsoft Defender for Endpoint

Typically, you [create and manage endpoint security policies in the Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies). Intune can apply these policies to enrolled devices. With Defender for Endpoint security settings management, Intune can also apply supported policies to devices that are onboarded to Defender for Endpoint but aren't enrolled in Intune.

After you configure the connection between Intune and Defender for Endpoint and enable security settings management as described in [Manage Defender for Endpoint security settings](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/security-settings-management), you can also create and manage supported endpoint security policies in the Microsoft Defender portal.

Managing endpoint security policies in the Defender portal has the following benefits:

- Work from a single console.
- Apply one policy to both Intune-enrolled devices and devices managed through Defender for Endpoint security settings management.
- Manage security settings using Defender for Endpoint permissions rather than a full Intune administrator role.

Use the procedures in this article to create and manage policies on the **Endpoint security policies** page in the Microsoft Defender portal at [https://security.microsoft.com/policy-inventory](https://security.microsoft.com/policy-inventory).

## Prerequisites

You need the appropriate permissions to complete the procedures in this article.

- Your permissions must apply to all devices. If your role is scoped to specific device groups, you can't open the **Endpoint security policies** page.
- Regardless of which of the following options grants you access, the list of policies shown in the Microsoft Defender portal is scoped by your Intune role-based access control \(RBAC\) assignments.

You have the following options to assign the required permissions:

- [Microsoft Defender Unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac):

  - *Create and manage policies*: **Authorization and settings/Security settings/Core Security settings \(manage\)**
  - *Read-only access to policies*: **Authorization and settings/Security settings/Core Security settings \(read\)**

- [Microsoft Intune role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/role-based-access-control): Microsoft recommends the Intune built-in [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/role-based-access-control#built-in-roles) role to align the level of permissions between Intune and the Microsoft Defender portal.
- [Microsoft Entra permissions](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup>, **Security Administrator**, or **Intune Administrator** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

  Important

  \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Supported endpoint security policies

The following table lists the endpoint security policy types you can manage and the platforms that each type supports:

Note

You can't use endpoint security policy management on devices that are running a sensor delivered by the Microsoft Monitoring Agent \(MMA\). For information about upgrading these devices, see [Use the Defender deployment tool to deploy Defender endpoint security](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel#use-the-defender-deployment-tool-to-deploy-defender-endpoint-security).

Also, only the **Microsoft Defender Antivirus** policy is supported on Windows 7 SP1 and Windows Server 2008 R2 SP1.

| Policy | Windows | macOS | Linux |
| --- | :---: | :---: | :---: |
| [Attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview) | Yes |  |  |
| [Defender update controls](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates) | Yes |  |  |
| [Device control](https://learn.microsoft.com/en-us/defender-endpoint/device-control-overview) | Yes¹ |  |  |
| [Endpoint detection and response \(EDR\)](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response) | Yes | Yes | Yes |
| [Microsoft Defender AI agent runtime protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-ai-agent-runtime-protection) | Yes |  |  |
| Microsoft Defender Antivirus | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac) | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux) |
| Microsoft Defender Antivirus exclusions | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-overview) | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/mac-exclusions) | [Yes](https://learn.microsoft.com/en-us/defender-endpoint/linux-exclusions) |
| [Microsoft Defender Firewall](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/) | Yes |  |  |
| [Microsoft Defender Firewall rules](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/rules) | Yes |  |  |
| [Microsoft Defender global exclusions \(antivirus and EDR\)](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview) |  |  | Yes |
| [Windows Security experience](https://learn.microsoft.com/en-us/windows/security/operating-system-security/system-security/windows-defender-security-center/windows-defender-security-center) | Yes |  |  |

¹ Device control policies are available in the Defender portal, but they apply only to devices enrolled in Microsoft Intune. They don't apply to devices managed only through Defender for Endpoint security settings management.

![Screenshot of the Endpoint security policies page showing operating system tabs and the policy list.](https://learn.microsoft.com/en-us/defender-endpoint/media/endpoint-security-policies.png)

## Create an endpoint security policy

To create an endpoint security policy, follow these steps:

1. On the **Endpoint security policies** page in the Microsoft Defender portal at [https://security.microsoft.com/policy-inventory](https://security.microsoft.com/policy-inventory), select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Create new policy**.

   The tab you start on doesn't matter because you can create a policy for any operating system from any tab. After creation, the policy appears on the tab for its operating system.
2. In the **Create a new policy** flyout that opens, choose from the following options:

   - **Select platform**: Choose one of the following values:

     - **Windows**
     - **macOS**
     - **Linux**

   - After you select the platform, **Select template** appears. For the templates available on each platform, see [Supported endpoint security policies](#supported-endpoint-security-policies).

     After you select a template, select **Create policy**.

3. The new policy wizard opens. On the **Basics** page, configure the following settings:

   - **Name**: Enter a unique, descriptive name for the policy.
   - **Description**: Enter an optional description for the policy.


   When you're finished on the **Basics** page, select **Next**.

4. On the **Configuration settings** page, the available settings depend on the policy platform and template.

   You can use the ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-search.png) **Search** box to find settings.

   When you're finished on the **Configuration settings** page, select **Next**.
5. On the **Assignments** page, use the ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-search.png) **Search** box to find and select a group to assign the policy to. Intune policy assignments use Microsoft Entra security groups. For information about supported group types and membership, see [Use groups to organize users and devices for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-groups).

   Important

   For devices managed through Defender for Endpoint security settings management \(devices onboarded to Defender for Endpoint but not enrolled in Intune\), assignments support device objects only. Assign the policy to Microsoft Entra device groups, not user groups, because user targeting isn't supported for these devices. For Intune-enrolled devices, you can assign the policy to user groups or device groups.

   After you select a group, the following information is shown on the page:

   - **Group**: The group name.
   - **Group members**: The number of affected devices and users.
   - **Target type**: You can select **Include \(default\)** or **Exclude** to include or exclude the members of the group from the policy.


   Repeat this step to assign more groups.


   When you're finished on the **Assignments** page, select **Next**.

6. On the **Review + create** page, review your settings. Use the **Back** button to modify the settings.

   When you're finished on the **Review + create** page, select **Save**.

After the policy creation finishes, you're taken to the detailed settings of the policy as if you selected it on the **Endpoint security policies** page.

Note

The Defender portal policy wizard doesn't support [scope tags](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags) or [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview). To use these features, [create or edit the policy in the Microsoft Intune admin center](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#create-endpoint-security-policies).

## Edit an endpoint security policy

To modify an endpoint security policy, follow these steps:

1. On the **Endpoint security policies** page in the Defender portal, select an available tab:

   - **Windows policies**: [https://security.microsoft.com/policy-inventory](https://security.microsoft.com/policy-inventory) or [https://security.microsoft.com/policy-inventory?osPlatform=Windows](https://security.microsoft.com/policy-inventory?osPlatform=Windows).
   - **macOS policies**: [https://security.microsoft.com/policy-inventory?osPlatform=Mac](https://security.microsoft.com/policy-inventory?osPlatform=Mac).
   - **Linux policies**: [https://security.microsoft.com/policy-inventory?osPlatform=Linux](https://security.microsoft.com/policy-inventory?osPlatform=Linux).

2. On the appropriate tab, select the policy by using any of the following methods:

   - Select the check box next to the policy, and then select the ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-edit.png) **Edit** action that appears.
   - Select the policy name \(link\). On the policy page that opens, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-edit.png) **Edit**.
   - Select anywhere in the row other than the check box or the policy name. In the policy details flyout that opens, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-edit.png) **Edit**.

3. In the policy wizard, review or change the **Basics**, **Configuration settings**, and **Assignments** pages. On the **Review + create** page, review the policy, and then select **Save**.

The policy page opens after the changes are saved.

## Verify endpoint security policies

To confirm that you successfully created a policy, verify the policy is listed on the appropriate tab of the **Endpoint security policies** page in the Defender portal at [https://security.microsoft.com/policy-inventory](https://security.microsoft.com/policy-inventory).

Select the policy name \(link\) to open the policy page. The policy page summarizes the status of the policy. You can view the policy's status, which devices it applies to, and the assigned groups.

Devices managed through Defender for Endpoint security settings management check in with Intune every 90 minutes for policy updates. To request an on-demand policy sync:

1. On the appropriate tab of the **Device inventory** page in the Defender portal at [https://security.microsoft.com/machines](https://security.microsoft.com/machines), select the **Name** value of the device.
2. On the [device entity page](https://learn.microsoft.com/en-us/defender-xdr/entity-page-device) that opens, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-more-actions.png) **More actions**, and then select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-sync.png) **Policy sync**.

The policy should be applied in about 10 minutes.

![Screenshot of the device actions menu showing the Policy sync action.](https://learn.microsoft.com/en-us/defender-endpoint/media/policy-sync.png)

During an investigation, use the **Security policies** tab in the **Configuration management** section of the device entity page to view the policies applied to the device. For more information, see [Investigating devices](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines).

![Screenshot of the Security policies tab showing policies applied to a device.](https://learn.microsoft.com/en-us/defender-endpoint/media/security-policies-list.png)
