<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-offboard-devices -->
<!-- Sitemap-Last-Modified: 2026-04-25 -->

# Offboard a device from Microsoft Defender for Business

As you replace or retire devices, or as your business needs change, you can offboard devices from Defender for Business. When you offboard a device, it stops sending data to Defender for Business. Its status changes to `Inactive` within seven days. You don't need to offboard devices that are already listed as `Inactive`.

Data from a device, such as alerts, vulnerabilities, and detected threats, remains visible in the Microsoft Defender portal until the [configured retention period](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) expires, usually 180 days.

Devices that weren't active within the last 30 days don't affect your organization's [exposure score](https://learn.microsoft.com/en-us/defender-business/mdb-view-tvm-dashboard).

Important

The procedures in this article describe how to remove a device from monitoring by Defender for Business. If you're using Microsoft Intune to manage devices, and you prefer to remove the device from Intune, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/devices-wipe).

## What to do

1. Select one of the following tabs:

   - **Windows 10 or 11**
   - **Mac**
   - **Servers**: Windows Server or Linux Server
   - **Mobile**: for iOS/iPadOS or Android devices

2. Follow the guidance on the selected tab.
3. Proceed to your next steps.

- [**Windows 10 or 11**](#tabpanel_1_Windows1011)
- [**Mac**](#tabpanel_1_mac)
- [**Servers**](#tabpanel_1_Servers)
- [**Mobile devices**](#tabpanel_1_mobiles)

## Windows 10 or 11

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Settings**, and then choose **Endpoints**.
3. Under **Device management**, choose **Offboarding**.
4. Select an operating system, such as **Windows 10 and 11**, and then, under **Offboard a device**, in the **Deployment method** section, choose **Local script**.
5. In the confirmation screen, review the information, and then choose **Download** to proceed.
6. Select **Download offboarding package**. We recommend saving the offboarding package to a removable drive.
7. Run the script on each device that you want to offboard.

## Mac

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Settings**, and then choose **Endpoints**.
3. Under **Device management**, choose **Offboarding**.
4. In the **Select operating system to start the offboarding process** list, select **macOS**.
5. In the **Deployment method** section, select either **Local Script** or **Mobile Device Management / Microsoft Intune**, depending on your preferred method.
6. Select **Download package**. We recommend saving the offboarding package to a removable drive.
7. Run the script on each Mac computer that you want to offboard.

## Servers

Choose the operating system for your server:

- [Windows Server](#windows-server)
- [Linux Server](#linux-server)

### Windows Server

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Settings** > **Endpoints**, and then under **Device management**, choose **Offboarding**.
3. Select an operating system, such as **Windows Server 1803, 2019, and 2022**, and then in the **Deployment method** section, choose **Local script**.
4. Select **Download package**. We recommend that you save the offboarding package to a removable drive. The zipped folder is named `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.zip`, where `YYYY-MM-DD` is the expiry date of the package.
5. On your Windows Server device, extract the contents of the zipped folder to a location such as the Desktop folder.
6. Open a Command Prompt window as an administrator.
7. Type the location of the script file. For example, if you copied the file to the Desktop folder, type `%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_2022-11-11.cmd`, where `YYYY-MM-DD` is the expiry date of the package. Then press **Enter** or select **OK**.

### Linux Server

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Settings** > **Endpoints**, and then under **Device management**, choose **Offboarding**.
3. Select **Linux Server** for the operating system, and then in the **Deployment method** section, choose **Local script**.
4. Select **Download package**. We recommend that you save the offboarding package to a removable drive. The zipped folder is named `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.zip`, where `YYYY-MM-DD` is the expiry date of the package.
5. On your Linux Server device, extract the contents of the zipped folder to a location such as the Desktop folder.
6. Open a terminal, and navigate to the directory where the `MicrosoftDefenderATPOffboardingLinuxServer_valid_until_YYYY-MM-DD` file, where `YYYY-MM-DD` is the expiry date of the file, is located.
7. Type `python MicrosoftDefenderATPOffboardingLinuxServer_valid_until_YYYY-MM-DD.py` in the terminal.

Note

This procedure offboards the server, meaning that the server stops sending security data to Defender for Business. It doesn't remove the Defender for Business software from the device. For information about how to completely remove the software from the device, see [Offboard or uninstall Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints).

## Mobile devices

You can use Microsoft Intune to manage mobile devices, such as iOS, iPadOS, and Android devices.

See [Microsoft Intune device management](https://learn.microsoft.com/en-us/intune/intune-service/remote-actions/device-management).

## Related content

- [Use your Microsoft Defender Vulnerability Management dashboard in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-tvm-dashboard)
- [View or edit policies in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies)
- [Manage devices in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-manage-devices)
