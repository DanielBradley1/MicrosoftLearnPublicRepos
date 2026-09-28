<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/devices -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Academic year transition - devices

The academic year transition process for devices consists of the following steps:

![Picture showing timeline of academic year transition for devices. Three weeks before end of school, review changes that you may want to make to set up your Windows devices in the new year and consider the key scenarios for devices: users retain their devices over summer break or users turn in devices or devices remain in the facility. Depending on the district strategy for new device rotation, this process usually occurs in two phases: New Device Enrollment and Device Configuration. As school starts, After the devices are set up and ready to go, run a few tests and then distribute them](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/devices-academic-year-transition.png)

## End of Year closeout

For devices and device management, most of the needed processes occur after the end of the school year. Depending on how exams or tests are administered, you may want to review your policies and make some changes to set up your Windows devices accordingly. For example, look for ways to reduce on-premises infrastructure with new features such as [Microsoft Universal Print](https://www.microsoft.com/microsoft-365/windows/universal-print).

### Existing device cleanup

After the school year has concluded, there are often three key scenarios to consider for devices:

- **Users retain their devices** over summer break and keep them with them
- **Users turn in devices** \(for example, graduating students\)
- **Devices remain** in the facility \(for example, device carts, computer labs\)

#### Users Retain their Devices

In this scenario, little extra work is needed for device management and health. There are a few things to keep in mind, however. For example:

- If there are any school district wide policy changes, these policies can usually be administered remotely. However, in some unique cases they may need to be configured physically upon the user's return
- If any new applications need to be updated or installed, these devices can be addressed remotely, given that they have power and network connectivity
- There may be physical repairs that need to be addressed \(for example, keyboard key replacements, battery replacement, etc.\)

#### Users turn in their devices or devices remain on premises

Often, devices are shared or used commonly during the school year.

- Ensure that applications and settings are configured for the upcoming school year
- Use [Intune bulk device actions](https://learn.microsoft.com/en-us/mem/intune/remote-actions/bulk-device-actions) to target labs or carts of devices to invoke a [Windows Autopilot Reset](https://learn.microsoft.com/en-us/mem/autopilot/windows-autopilot-reset)

### New Device Preparation

Depending on the district strategy for new device rotation, the acquisition period can vary. However, the process remains the same when receiving new devices and usually occurs in two phases:

- [Phase 1: New Device Enrollment](#phase-1-new-device-enrollment)
- [Phase 2: Device Configuration](#phase-2-device-configuration)

#### Phase 1: New Device Enrollment

Adding new devices is a natural part of the school year rollover process, there are a few scenarios to consider:

For new PCs or PCs moving to Microsoft Entra ID:

- [Decide which method to use](https://learn.microsoft.com/en-us/intune/intune-service/industry/education/tutorial-school-deployment/plan-enrollment) to join Windows devices to Microsoft Entra ID and getting them enrolled and managed by Intune:

  - Automatic Intune enrollment via Microsoft Entra join
  - Automatic Intune enrollment with provisioning packages
  - Automatic Intune enrollment with Windows Autopilot

- If you're resetting existing PCs, [you have several options](https://support.microsoft.com/help/4026528) to reset Windows, depending on your version.

For existing computers connected to Active Directory or Configuration Manager:

- Get your devices joined in a hybrid Microsoft Entra environment.
- Set up Windows education devices to enroll them, including enrollment in [**Intune using Group Policy**](https://learn.microsoft.com/en-us/intune/intune-service/industry/education/tutorial-school-deployment/plan-grouping)
- For iPadOS devices, [setup device management](https://learn.microsoft.com/en-us/intune-education/setup-ios-device-management) for Apple School Manager devices and [enroll](https://learn.microsoft.com/en-us/intune-education/add-devices-ios-edu) them

For customers with Configuration Manager:

- [Configure co-management](https://learn.microsoft.com/en-us/mem/configmgr/comanage/tutorial-co-manage-clients) so you can use Intune to manage devices while they aren't connected to the school network
- [Configure a cloud management gateway](https://learn.microsoft.com/en-us/mem/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway) so you can continue to approve software updates, deploy software, and retrieve inventory from devices that aren't connected to the school network

#### Phase 2: Device Configuration

After all the devices are cleaned, set up, and connected to Microsoft Entra ID, perform updates such as deploying new applications, Microsoft Office, and Microsoft Edge.

An education specific setting in Intune for Education is the ability [to choose the version of Windows you want to run on devices](https://learn.microsoft.com/en-us/intune-education/whats-new-in-edu). That version will run on devices until you remove or reconfigure this setting.

Depending on your needs, you may choose to target apps to user groups rather than device groups. However, where possible, the app should be targeted to the device so that it's installed and ready to use when they sign in. Consideration should be taken with the size of the app and potential connectivity that the end user may or may not have.

Intune for Education supports deploying and managing these types of apps:

- Microsoft Office and Microsoft Edge desktop apps
- Microsoft Store apps
- Web apps
- Windows desktop apps \(.msi\)
- iOS VPP and Store apps

If you have other app or platform needs, the Microsoft Intune admin center includes [Android store](https://learn.microsoft.com/en-us/mem/intune/apps/store-apps-android) apps, [managed Google Play](https://learn.microsoft.com/en-us/mem/intune/apps/apps-add-android-for-work) apps, [macOS](https://learn.microsoft.com/en-us/mem/intune/apps/lob-apps-macos), Microsoft Edge, [Microsoft Defender for EndPoint on Mac \(macOS\)](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac) and [Win32 apps](https://learn.microsoft.com/en-us/mem/intune/apps/apps-win32-app-management) \(.exe\). If you need to install apps in a certain order, Intune offers the ability to set up app dependencies.

Note

If an app is assigned to a user group, the app won't start the evaluation, download, and installation until after the user logs in.

## New School Year Launch

After the devices are set up and ready to go, run a few tests, and then distribute the devices.

To confirm that all the groups and settings are working correctly, designate a few devices as test devices to verify the changes are working for the designated users and device groups. Both the hardware and software versions in these test devices should be the same as in the deployed devices.

## For more information

The following resources provide additional information about Intune:

- [Intune](https://learn.microsoft.com/en-us/intune-education/what-is-intune-for-education)
- [Tutorial: deploy and manage devices in a school](https://learn.microsoft.com/en-us/intune/intune-service/industry/education/tutorial-school-deployment/introduction)
- [Microsoft Intune for Education Deployment Workshop](https://aka.ms/i4e/workshopvideos) videos
