<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-device-options -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Microsoft Entra Connect: Device options

The following documentation provides information about the various device options available in Microsoft Entra Connect. You can use Microsoft Entra Connect to configure the following two operations:

- **Microsoft Entra hybrid join**: If your environment has an on-premises AD footprint and you want the benefits of Microsoft Entra ID, you can implement Microsoft Entra hybrid joined devices. These devices are joined both to your on-premises Active Directory, and your Microsoft Entra ID.
- **Device writeback**: Device writeback is used to enable Conditional Access based on devices to AD FS \(2012 R2 or higher\) protected devices

## Configure device options in Microsoft Entra Connect

1. Run Microsoft Entra Connect. In the **Additional tasks** page, select **Configure device options**. Click **Next**. ![Configure device options](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-device-options/deviceoptions.png)

   The **Overview** page displays the details. ![Overview](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-device-options/deviceoverview.png)

   Note

   The new Configure device options is available only in version 1.1.819.0 and newer.
2. After providing the credentials for Microsoft Entra ID, you can chose the operation to be performed on the Device options page. ![Device operations](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/media/how-to-connect-device-options/deviceoptionsselection.png)

## Next steps

- [Configure Microsoft Entra hybrid join](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan)
- [Configure / Disable device writeback](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-device-writeback)
