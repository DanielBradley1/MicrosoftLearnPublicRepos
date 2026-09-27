<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-deploy-application-guard-policy -->
<!-- Sitemap-Last-Modified: 2022-12-05 -->

# Create and deploy Microsoft Defender Application Guard policy

*Applies to: Configuration Manager \(current branch\)*

You can create and deploy [Microsoft Defender Application Guard \(Application Guard\)](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) policies by using the Configuration Manager endpoint protection. These policies help protect your users by opening untrusted web sites in a secure isolated container that isn't accessible by other parts of the operating system.

## Prerequisites

To create and deploy a Microsoft Defender Application Guard policy, you must use Windows 10 1709 or later. The Windows 10 or later devices to which you deploy the policy must be configured with a [network isolation policy](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/configure-md-app-guard#network-isolation-settings). For more information, see the [Microsoft Defender Application Guard overview](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview).

## Create a policy, and to browse the available settings

1. In the Configuration Manager console, choose **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, choose **Overview** > **Endpoint Protection** > **Microsoft Defender Application Guard**.
3. In the **Home** tab, in the **Create** group, click **Create Microsoft Defender Application Guard Policy**.
4. Using the [article](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/configure-md-app-guard) as a reference, you can browse and configure the available settings. Configuration Manager allows you to set certain policy settings:

   - [Application behavior](#bkmk_ABS)
   - [Host interaction settings](#bkmk_HIS)

5. On the **Network Definition** page, specify the corporate identity, and define your corporate network boundary.

   Note

   Windows 10 or later PCs store only one network isolation list on the client. You can create two different kinds of network isolation lists and deploy them to the client:

   - one from Windows Information Protection
   - one from Microsoft Defender Application Guard


   If you deploy both policies, these network isolation lists must match. If you deploy lists that don't match to the same client, the deployment will fail. For more information, see the [Windows Information Protection documentation](https://learn.microsoft.com/en-us/windows/security/information-protection/windows-information-protection/create-wip-policy-using-configmgr).

6. When you're finished, complete the wizard, and deploy the policy to one or more Windows 10 1709 or later devices.

### Application behavior

Configures interactions between host devices and the Application Guard container. Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.

- **Clipboard** - Under settings prior to Configuration Manager 1802

  - Permitted content type

    - Text
    - Images

- **Printing:**

  - Enable printing to XPS
  - Enable printing to PDF
  - Enable printing to local printers
  - Enable printing to network printers

- **Graphics:** \(starting with Configuration Manager version 1802\)

  - Virtual graphics processor access

- **Files:** \(starting with Configuration Manager version 1802\)

  - Save downloaded files to host

- **Policies:** \(starting with Configuration Manager version 2207\)

  - Enable or disable cameras and microphones
  - Certificate matching the thumbprints to the isolated container

### Host interaction settings

Configures application behavior inside the Application Guard session. Before Configuration Manager version 1802, both application behavior and host interaction were under the **Settings** tab.

- **Other:**

  - Retain user-generated browser data
  - Audit security events in the isolated application guard session

To edit Application Guard settings, expand **Endpoint Protection** in the **Assets and Compliance** workspace, then click on the **Microsoft Defender Application Guard** node. Right-click on the policy you want to edit, then select **Properties**.

## Known issues

*Applies to version 2203 or earlier*

Devices running Windows 10, version 2004 will show failures in compliance reporting for Microsoft Defender Application Guard File Trust Criteria. This issue occurs because some subclasses were removed from the WMI class `MDM_WindowsDefenderApplicationGuard_Settings01` in Windows 10, version 2004. All other Microsoft Defender Application Guard settings will still apply, only File Trust Criteria will fail. Currently, there are no workarounds to bypass the error.

*Applies to version 2207 or later*

Enabling the policy doesn't install Microsoft Defender Application Guard feature by default. Deploy a PowerShell script via ConfigMgr to all applicable machines.

Use the following commands to enable feature. Enable-WindowsOptionalFeature -online -FeatureName "Windows-Defender-ApplicationGuard"

## Next steps

For more information about Microsoft Defender Application Guard, see

- [Microsoft Defender Application Guard overview](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview).
- [Microsoft Defender Application Guard FAQ](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard).
