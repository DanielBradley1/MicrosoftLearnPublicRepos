<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-asr-policy -->
<!-- Sitemap-Last-Modified: 2023-12-12 -->

# Tenant attach: Create and deploy Attack surface reduction policies from the admin center

*Applies to: Configuration Manager \(current branch\)*

Create Attack surface reduction policies in the Microsoft Intune admin center and deploy them to Configuration Manager collections.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.

  - Upgrade the target devices to the latest version of the Configuration Manager client.

- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_supportedprofiles)

## Assign Attack surface reduction policy to a collection

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** > **Attack surface reduction** then **Create Policy**.
3. Create a profile with the following settings:

   - **Platform**: Windows 10 and later \(ConfigMgr\)
   - **Profile**: Choose one of the following profiles:

     - Attack Surface Reduction Rules \(ConfigMgr\)
     - Exploit Protection \(ConfigMgr\)
     - Web Protection \(ConfigMgr\)

Note

The Microsoft Edge installer, Attack Surface Reduction rules engine for tenant attach, and [CMPivot](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot) are currently signed with the **Microsoft Code Signing PCA 2011** certificate. If you set PowerShell execution policy to **AllSigned**, then you need to make sure that devices trust this signing certificate. You can export the certificate from a computer where you've installed the Configuration Manager console. View the certificate on `"C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\CMPivot.exe"`, and then export the code signing certificate from the certification path. Then import it to the *machine*'s **Trusted Publishers** store on managed devices. You can use the process in the following blog, but make sure to export the *code signing certificate* from the certification path: [Adding a Certificate to Trusted Publishers using Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/adding-a-certificate-to-trusted-publishers-using-intune/ba-p/1974488)

1. Assign a **Name** and optionally a **Description** on the **Basics** page.
2. On the **Configuration settings** page, configure the settings you want to manage with this profile. When your done configuring settings, select **Next**. For more information about available settings for both profiles, see [Attack surface reduction policy settings for tenant attached devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr).
3. Assign the policy to a Configuration Manager collection on the **Assignments** page.

## Device Status

You can review the status of endpoint security policies for tenant attached devices. The **Device Status** page can be accessed for all endpoint security policy types for tenant-attached clients. To display the **Device Status** page:

1. Select a policy that's targeted to **ConfigMgr** devices to display the **Overview** page for the policy.
2. Select **Device Status** to display a list of devices targeted by the policy.
3. The **Device Name**, **Compliance State**, and **SMS ID** are displayed for each of the devices on the **Device Status** page.

## Next steps

- [Attack surface reduction policy settings for tenant attached devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr).
- [Create and deploy endpoint security Antivirus policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-antivirus-policy)
- [Create and deploy endpoint security Endpoint Detection and Response policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/atp-onboard)
- [Create and deploy endpoint security Firewall policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-firewall-policy)
