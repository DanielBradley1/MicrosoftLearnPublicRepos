<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/atp-onboard -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Tenant attach: Onboard Microsoft Configuration Manager clients to Microsoft Defender for Endpoint from the admin center

*Applies to: Configuration Manager \(current branch\)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Intune admin center**. You can deploy Defender for Endpoint onboarding policies to Configuration Manager managed clients. These clients don't require Microsoft Entra ID or MDM enrollment, and the policy is targeted at Configuration Manager collections rather than Microsoft Entra groups.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.

  - Upgrade the target devices to the latest version of the Configuration Manager client.

- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_supportedprofiles)

- [Microsoft Intune and Microsoft Defender for Endpoint integration enabled](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration#connect-defender-for-endpoint-to-intune)
- Client which meets the [minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements#licensing-requirements) and is onboarded.

## Create Defender for Endpoint policies

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** > **Endpoint detection and response** > **Create Policy**.
3. Select the following platform and profile for your policy:

   - Platform: **Windows 10, Windows 11, and Windows Server \(ConfigMgr\)**
   - Profile: **Endpoint detection and response \(ConfigMgr\)**

4. Select **Create**.
5. On the **Basics** page, enter a name and description for the profile, and then choose **Next**.
6. On the **Configuration settings** page, configure the settings you want to manage with this profile. The onboarding package is automatically included and isn't something you can configure.

   When you're done configuring settings, select **Next**.
7. On the **Assignments** page, select the collections that receive this policy. Select collections from Configuration Manager that you synced to Intune admin center and enabled for Defender for Endpoint policy.

   You can choose not to assign collections at this time, and later edit the policy to add an assignment.

   When ready to continue, select **Next**.
8. On the **Review + create** page, when you're done, choose **Create**.

   The new profile is displayed in the list when you select the policy type for the profile you created.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.

## Next steps

- [Create and deploy endpoint security Antivirus policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-antivirus-policy)
- [Create and deploy endpoint security Firewall policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-firewall-policy)
