<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-control -->
<!-- Sitemap-Last-Modified: 2024-11-27 -->

# Microsoft Entra hybrid join targeted deployment

You can validate your [planning and prerequisites](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan) for hybrid Microsoft Entra joining devices using a targeted deployment before enabling it across the entire organization. This article explains how to accomplish a targeted deployment of Microsoft Entra hybrid join.

Caution

Use caution when modifying values in Active Directory. Making changes in an established environment might have unintended consequences.

## Targeted deployment of Microsoft Entra hybrid join on Windows devices

For devices running Windows 10, the minimum supported version is Windows 10 \(version 1607\) to do hybrid join. As a best practice, upgrade to the latest version of Windows 10 or 11.

To do a targeted deployment of Microsoft Entra hybrid join on Windows devices, you need to:

1. [Clear the Service Connection Point \(SCP\) entry from Windows Server Active Directory if it exists](#clear-the-scp-from-ad).
2. [Configure client-side registry setting for SCP on your domain-joined computers using a Group Policy Object \(GPO\)](#configure-client-side-registry-setting-for-scp).
3. If you're using Active Directory Federation Services \(AD FS\), you must also [configure the client-side registry setting for SCP on your AD FS server using a GPO](#configure-ad-fs-settings).
4. You might need to [customize synchronization options](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-post-installation#additional-tasks-available-in-azure-ad-connect) in Microsoft Entra Connect to enable device synchronization.

Tip

The SCP might be configured locally in the registry of the device in certain situations. If the device finds a value in the registry it uses that configuration, otherwise it queries the directory for the SCP and attempts to hybrid join.

### Clear the SCP from Microsoft Windows Server Active Directory

Use the Active Directory Services Interfaces Editor \(ADSI Edit\) to modify the SCP objects in Microsoft Windows Server Active Directory.

1. Launch the **ADSI Edit** desktop application from and administrative workstation or a domain controller as an Enterprise Administrator.
2. Connect to the **Configuration Naming Context** of your domain.
3. Browse to **CN=Configuration,DC=contoso,DC=com** > **CN=Services** > **CN=Device Registration Configuration**.
4. Right-click on the leaf object **CN=62a0ff2e-97b9-4513-943f-0d221bd30080** and select **Properties**.

   1. Select **keywords** from the **Attribute Editor** window and select **Edit**.
   2. Select the values of **azureADId** and **azureADName** \(one at a time\) and select **Remove**.

5. Close **ADSI Edit**.

### Configure client-side registry setting for SCP

Use the following example to create a Group Policy Object \(GPO\) to deploy a registry setting configuring an SCP entry in the registry of your devices.

1. Open a Group Policy Management console and create a new Group Policy Object in your domain.

   1. Provide your newly created GPO a name \(for example, ClientSideSCP\).

2. Edit the GPO and locate the following path: **Computer Configuration** > **Preferences** > **Windows Settings** > **Registry**.
3. Right-click on the Registry and select **New** > **Registry Item**.

   1. On the **General** tab, configure the following.

      1. Action: **Update**.
      2. Hive: **HKEY\_LOCAL\_MACHINE**.
      3. Key Path: **SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\CDJ\\AAD**.
      4. Value name: **TenantId**.
      5. Value type: **REG\_SZ**.
      6. Value data: The globally unique identifier \(GUID\) or **Tenant ID** of your Microsoft Entra tenant, which can be found in **Entra ID** > **Overview** > **Properties** > **Tenant ID**.

   2. Select **OK**.

4. Right-click on the Registry and select **New** > **Registry Item**.

   1. On the **General** tab, configure the following.

      1. Action: **Update**.
      2. Hive: **HKEY\_LOCAL\_MACHINE**.
      3. Key Path: **SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\CDJ\\AAD**.
      4. Value name: **TenantName**.
      5. Value type: **REG\_SZ**.
      6. Value data: Your verified **domain name** if you're using federated environment such as AD FS. Your verified **domain name** or your onmicrosoft.com domain name, for example `contoso.onmicrosoft.com` if you're using managed environment.

   2. Select **OK**.

5. Close the editor for the newly created GPO.
6. Link the newly created GPO to the correct organizational unit \(OU\) containing domain-joined computers that belong to your controlled rollout population.

### Configure AD FS settings

If your Microsoft Entra ID is federated with AD FS, you first need to configure client-side SCP using the instructions mentioned earlier by linking the GPO to your AD FS servers. The SCP object defines the source of authority for device objects. It can be on-premises or Microsoft Entra ID. When client-side SCP is configured for AD FS, the source for device objects is established as Microsoft Entra ID.

Note

If you failed to configure client-side SCP on your AD FS servers, the source for device identities would be considered as on-premises. AD FS will then start deleting device objects from on-premises directory after the stipulated period defined in the AD FS Device Registration's attribute "MaximumInactiveDays". AD FS Device Registration objects can be found using the [Get-AdfsDeviceRegistration cmdlet](https://learn.microsoft.com/en-us/powershell/module/adfs/get-adfsdeviceregistration).

## Why a device might be in a pending state

When you configure a **Microsoft Entra hybrid join** task in the Microsoft Entra Connect Sync for your on-premises devices, the task syncs device objects to Microsoft Entra ID, and temporarily set the registered state of the devices to "pending" before the device completes the device registration. This pending state is because the device must be added to the Microsoft Entra directory before it can be registered. For more information about the device registration process, see [How it works: Device registration](https://learn.microsoft.com/en-us/entra/identity/devices/device-registration-how-it-works#hybrid-azure-ad-joined-in-managed-environments).

## Post validation

After you verify that everything works as expected, you can automatically register the rest of your Windows devices with Microsoft Entra ID. Automate Microsoft Entra hybrid join by [configuring the SCP using Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/devices/how-to-hybrid-join).

## Related content

- [Plan your Microsoft Entra hybrid join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan)
- [Configure Microsoft Entra hybrid join](https://learn.microsoft.com/en-us/entra/identity/devices/how-to-hybrid-join)
- [Configure Microsoft Entra hybrid join manually](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-manual)
