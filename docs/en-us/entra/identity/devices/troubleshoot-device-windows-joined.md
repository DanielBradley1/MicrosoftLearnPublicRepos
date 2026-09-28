<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/troubleshoot-device-windows-joined -->
<!-- Sitemap-Last-Modified: 2025-07-27 -->

# Troubleshooting Windows devices in Microsoft Entra ID

If you have a Windows 11 or Windows 10 device that isn't working with Microsoft Entra ID correctly, start your troubleshooting here.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Reports Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader).
2. Browse to **Entra ID** > **Devices** > **All devices** > **Diagnose and solve problems**.
3. Select **Troubleshoot** under the **Windows 10+ related issue** troubleshooter.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/devices/media/troubleshoot-device-windows-joined/devices-troubleshoot-windows.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/devices/media/troubleshoot-device-windows-joined/devices-troubleshoot-windows.png" alt="A screenshot showing the Windows troubleshooter located in the diagnose and solve pane." data-linktype="relative-path">
   </a>
   </span>

4. Select **instructions** and follow the steps to download, run, and collect the required logs for the troubleshooter to analyze.
5. Return to the Microsoft Entra admin center when you collect and zip the `authlogs` folder and contents.
6. Select **Browse** and choose the zip file you wish to upload.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/devices/media/troubleshoot-device-windows-joined/devices-troubleshoot-windows-upload.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/devices/media/troubleshoot-device-windows-joined/devices-troubleshoot-windows-upload.png" alt="A screenshot showing how to browse to select the logs gathered in the previous step to allow the troubleshooter to make recommendations." data-linktype="relative-path">
   </a>
   </span>

The troubleshooter will review the contents of the file you uploaded and provide suggested next steps. These next steps might include links to documentation or contacting support for further assistance.

## Next steps

- [Troubleshoot devices by using the dsregcmd command](https://learn.microsoft.com/en-us/entra/identity/devices/troubleshoot-device-dsregcmd)
- [Troubleshoot Microsoft Entra hybrid joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/troubleshoot-hybrid-join-windows-current)
- [Troubleshoot pending device state](https://learn.microsoft.com/en-us/troubleshoot/azure/active-directory/pending-devices)
- [MDM enrollment of Windows 10-based devices](https://learn.microsoft.com/en-us/windows/client-management/mdm-enrollment-of-windows-devices)
- [Troubleshooting Windows device enrollment errors in Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/device-enrollment/troubleshoot-windows-enrollment-errors)
