<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-domain-join-windows -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configuration Domain Join settings for Microsoft Entra hybrid joined devices in Microsoft Intune

Many environments use on-premises Active Directory \(AD\). When AD domain-joined devices are also joined to Microsoft Entra ID, they're called Microsoft Entra hybrid joined devices. Using Windows Autopilot, you can [enroll Microsoft Entra hybrid joined devices](https://learn.microsoft.com/en-us/autopilot/windows-autopilot-hybrid) in Intune. To enroll, you also need a **Domain Join** configuration profile.

A **Domain Join** configuration profile includes on-premises Active Directory domain information. When devices are provisioning \(and typically offline\), this profile deploys the AD domain details so devices know which on-premises domain to join. If you don't create a domain join profile, these devices might fail to deploy.

This feature applies to:

- Windows
- Microsoft Entra hybrid joined devices
- Hybrid deployment with Windows Autopilot + Intune

This article shows you how to create a domain join profile for a hybrid Windows Autopilot deployment. You can also see the available settings.

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**.
3. Enter the following properties:

   - **Platform**: Select **Windows 10 and later**.
   - **Profile type**: Select **Templates** > **Domain Join**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Windows Autopilot domain join**.
   - **Description**: Enter a description for the policy. This setting is optional, but recommended. For example, enter **Windows: Domain join profile that includes on-premises domain information to enroll hybrid AD joined devices with Windows Autopilot**.

6. Select **Next**.
7. In **Configuration settings**, enter the following properties:

   - **Computer name prefix**: Enter a prefix for the device name. Computer names are 15 characters long. After the prefix, the remaining 15 characters are randomly generated.
   - **Domain name**: Enter the Fully Qualified Domain Name \(FQDN\) the devices are to join. For example, enter `americas.corp.contoso.com`.
   - **Organizational unit** \(optional\): Enter the full path \([distinguished name](https://learn.microsoft.com/en-us/windows/win32/ad/object-names-and-identities#distinguished-name)\) to the organizational unit \(OU\) the computer accounts are to be created. For example, enter `OU=Mine,DC=Contoso,DC=com`. Don't enter quotation marks. To use the well-known computer object container \(CN=Computers, DC=Contoso, DC=Com\), leave this property blank.

     For more information and advice on this setting, go to [Deploy Microsoft Entra hybrid joined devices](https://learn.microsoft.com/en-us/autopilot/windows-autopilot-hybrid).

8. Select **Next**.
9. In **Scope tags** \(optional\), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use role-based access control \(RBAC\) and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

   Select **Next**.
10. In **Assignments**, select the device groups that will receive your profile. For more information about assigning profiles, go to [Assign user and device profiles](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).

    If you need to join devices to different domains or OUs, create different device groups.

    Select **Next**.
11. In **Applicability rules**, use the **Rule**, **Property**, and **Value** options to define how this profile applies within assigned groups. For more information on applicability rules, go to [Applicability rules](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile#applicability-rules).

    Select **Next**.
12. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

It's now ready for you to [deploy Microsoft Entra hybrid joined devices by using Intune and Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/windows-autopilot-hybrid).

## Related articles

- After the profile is [assigned](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile), [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- [Deploy Microsoft Entra hybrid joined devices by using Intune and Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/windows-autopilot-hybrid).
