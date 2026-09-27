<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-prepare-win10 -->
<!-- Sitemap-Last-Modified: 2024-12-16 -->

# How to prepare internet-based devices for co-management

This article focuses on the second path to co-management, for new internet-based devices. This scenario is when you have new Windows 10 or later devices that join Microsoft Entra ID and automatically enroll to Intune. You install the Configuration Manager client to reach a co-management state.

## Windows Autopilot

For new Windows devices, use the Windows Autopilot service to configure the out of box experience \(OOBE\). This process includes joining the device to Microsoft Entra ID, enrolling the device in Intune, installing the Configuration Manager client, and configuring co-management.

For more information, see [How to enroll with Windows Autopilot](https://learn.microsoft.com/en-us/intune/configmgr/comanage/autopilot-enrollment).

Note

As we talk with our customers that are using Microsoft Intune to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics. Co-management is a management option, while Microsoft Entra ID is an identity option. For more information, see [Understanding hybrid Microsoft Entra ID and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog post aims to clarify Microsoft Entra hybrid join and co-management, how they work together, but aren't the same thing.

You can't deploy the Configuration Manager client while provisioning a new computer in Windows Autopilot user-driven mode for Microsoft Entra hybrid join. This limitation is due to the identity change of the device during the Microsoft Entra hybrid join process. Deploy the Configuration Manager client after the Windows Autopilot process. For alternative options to install the client, see [Client installation methods in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/client-installation-methods).

### Gather information from Configuration Manager

Use Configuration Manager to collect and report the device information required by Intune. This information includes the device serial number, Windows product identifier, and a hardware identifier. It's used to register the device in Intune to support Windows Autopilot.

1. In the Configuration Manager console, go to the **Monitoring** workspace, expand the **Reporting** node, expand **Reports**, and select the **Hardware - General** node.
2. Run the report, **Windows Autopilot Device Information**, and view the results.
3. In the report viewer, select the **Export** icon, and choose the **CSV \(comma-delimited\)** option.
4. After saving the file, upload the data to Intune.

For more information, see [Manually register devices with Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/add-devices).

### Windows Autopilot for existing devices

*Windows Autopilot for existing devices* allows you to reimage and provision a Windows devices for [Windows Autopilot user-driven mode](https://learn.microsoft.com/en-us/autopilot/user-driven) using a single, native Configuration Manager task sequence.

For more information, see [Windows Autopilot for existing devices](https://learn.microsoft.com/en-us/autopilot/existing-devices).

## Install the Configuration Manager client

You no longer need to create and assign an Intune app to install the Configuration Manager client. The Intune enrollment policy automatically installs the Configuration Manager client as a first-party app. The device gets the client content from the Configuration Manager cloud management gateway \(CMG\), so you don't need to provide and manage the client content in Intune. For more information, see [How to enroll with Windows Autopilot](https://learn.microsoft.com/en-us/intune/configmgr/comanage/autopilot-enrollment).

You do still specify the Configuration Manager client command-line parameters in Intune.

Note

Make sure that the devices trust the CMG server authentication certificate. For more information, see [CMG server authentication certificate](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/server-auth-cert). If a device doesn't trust the CMG server authentication certificate, you'll see a WINHTTP\_CALLBACK\_STATUS\_FLAG\_INVALID\_CA error in the ccmsetup.log on the client.

### Get the command line from Configuration Manager

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Cloud Attach** node.

   Tip

   For version 2103 and earlier, select the **Co-management** node.
2. Select the co-management object, and then choose **Properties** in the ribbon.
3. On the **Enablement** tab, copy the command line. Paste it into Notepad to save for the next process. The command line only shows if you've met all of the prerequisites, such as a cloud management gateway.

The following command line is an example: `CCMSETUPCMD="CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSITECODE=ABC"`

Decide which command-line properties you require for your environment:

- The following command-line properties are required in all scenarios:

  - `CCMHOSTNAME`
  - `SMSSITECODE`

- If devices use Microsoft Entra ID for client authentication and also have a PKI-based client authentication certificate, specify the following properties to use Microsoft Entra ID:

  - `AADCLIENTAPPID`
  - `AADRESOURCEURI`

- If the client roams back to the intranet, use the `SMSMP` property.
- If you use your own PKI certificate, and your CRL isn't published to the internet, use the `/NoCRLCheck` parameter. For more information, see [About client installation properties: /NoCRLCheck](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#nocrlcheck).

  Important

  Microsoft recommends publishing the CRL. For more information, see [Planning for CRLs](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/plan-for-certificates#pki-certificate-revocation).
- To bootstrap a task sequence immediately after client registration, use the `PROVISIONTS` property. For more information, see [About client installation properties: PROVISIONTS](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#provisionts).
- To make sure that internet-based devices get the latest version of the Configuration Manager client, use the `UPGRADETOLATEST` property. For more information, see [About client installation properties: `UPGRADETOLATEST`](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties#upgradetolatest).

The site publishes other Microsoft Entra information to the cloud management gateway \(CMG\). A Microsoft Entra joined client gets this information from the CMG during the ccmsetup process, using the same tenant to which it's joined. This behavior further simplifies enrolling devices to co-management in an environment with more than one Microsoft Entra tenant. The only two required ccmsetup properties are `CCMHOSTNAME` and `SMSSITECODE`.

The following example includes all of these properties:

`CCMSETUPCMD="CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSITECODE=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com PROVISIONTS=PRI20001"`

For more information, see [Client installation properties](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties).

Important

If you customize this command line, make sure it isn't more than 1024 characters long. When the command line length is greater than 1024 characters, the client installation fails.

## Next steps

[How to enroll with Windows Autopilot](https://learn.microsoft.com/en-us/intune/configmgr/comanage/autopilot-enrollment)

[Switch workloads to Intune](https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-switch-workloads)
