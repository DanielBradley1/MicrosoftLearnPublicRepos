<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-autopilot -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Windows Autopilot

Windows Autopilot is a cloud-based service designed to simplify all parts of Windows devices lifecycle, from initial deployment through end of life. Windows Autopilot can reduce the overall costs for deploying, managing, and retiring devices.

Traditionally, IT pros spend a significant amount of time building and customizing images to apply to devices. Windows Autopilot introduces a new, simplified approach. Devices don't need to be reimaged, rather they can be deployed with the OEM image, and customized using cloud-based services.

From the user's perspective, it only takes a few simple operations to make their device ready to use. The only interaction required from the end user is to set their language and regional settings, connect to a network, and verify their credentials. Everything beyond that is automated.

## Prerequisites

Before setting up Windows Autopilot, consider these prerequisites:

- **Requirements.** Ensure your school and devices meet the [requirements for Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/requirements).
- **Devices ordered and registered.** Ensure your school IT administrator or Microsoft partner devices from an original equipment manufacturer \(OEM\) and registers them with the Windows Autopilot deployment service. To connect with a partner, you can use the [Microsoft Partner Center](https://partner.microsoft.com/) and work with them to register your devices.
- **Networking requirements.** Ensure students know to connect to the school network during OOBE setup. For more information on managing devices behind firewalls and proxy servers, see [Network endpoints for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints).

Note

Where not explicitly specified, both HTTPS \(443\) and HTTP \(80\) must be accessible. If you are auto-enrolling your devices into Microsoft Intune or deploying Microsoft Office, follow the networking guidelines for [<u>Microsoft Intune</u>](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints) and [<u>Microsoft 365</u>](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

## Register devices to Windows Autopilot

Before deployment, devices must be registered in the Windows Autopilot service. Each device's unique hardware identity \(known as a *hardware hash*\) must be uploaded to the Windows Autopilot service. In this way, the Windows Autopilot service can recognize which tenant devices belong to, and which OOBE experience it should present. There are three main ways to register devices to Windows Autopilot:

- **OEM registration process.** When you purchase devices from an OEM or Reseller, that company can automatically register devices to Windows Autopilot and associate them to your tenant. Before this registration can happen, a *Global Administrator* must grant the OEM/Reseller permissions to register devices. For more information, see [OEM registration](https://learn.microsoft.com/en-us/autopilot/oem-registration)

  Note

  For **Microsoft Surface registration**, collect the details shown in this [<u>documentation table</u>](https://learn.microsoft.com/en-us/surface/surface-autopilot-registration-support) and follow the instruction to submit the request form to Microsoft Support.
- **Cloud Solution Provider \(CSP\) registration process.** As with OEMs, CSP partners must be granted permission to register devices for a school. For more information, see [Partner registration](https://learn.microsoft.com/en-us/autopilot/partner-registration).

  Tip

  Try the [Microsoft Partner Center clickable demo](https://cloudpartners.transform.microsoft.com/resources/autopilot-in-edu-setup-english), which provides detailed steps to establish a partner relationship and register devices.
- **Manual registration.** To manually register a device, you must first capture its hardware hash. Then upload the hardware hash to the Windows Autopilot service using Microsoft Intune. For steps, see [Manually register devices with Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/add-devices).

  Important

  **Windows 11 SE** devices do not support the use of Windows PowerShell or Microsoft Configuration Manager to capture hardware hashes. We recommend working with an OEM, partner, or device reseller to register devices.

## Create groups for Windows Autopilot devices

**Windows Autopilot deployment profiles** determine the Windows Autopilot *deployment mode* and define the out-of-box experience of your devices. A device group is required to assign a Windows Autopilot deployment profile to the devices.

You can create dynamic device groups using Windows Autopilot attributes.

If you didn't already create groups in [Plan grouping](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/grouping-and-targeting) earlier, you can create the groups now.

- [Intune](#tabpanel_1_intune)
- [Intune For Education](#tabpanel_1_intune-for-education)

For more information, see [Create a Windows Autopilot device group using Intune](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot#create-an-autopilot-device-group-using-intune).

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** > **Create group**.
3. Specify a **Group name** and select **Dynamic**.
4. Under **Rules**, select **I want to manage: Devices** and use the clause **Where: Device group tag starts with**, specifying the required tag value
5. Select **Create group**.  ![Intune for Education - creation of a dynamic group for Windows Autopilot devices](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/enroll-autopilot/intune-education-autopilot-group.png)

More advanced dynamic membership rules can be created from Microsoft Intune admin center. For more information, see [Create a Windows Autopilot device group using Intune](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot#create-an-autopilot-device-group-using-intune).

Tip

You can use these dynamic groups not only to assign Windows Autopilot profiles, but also to target applications and settings.

## Create Windows Autopilot deployment profiles

For Windows Autopilot devices to offer a customized OOBE experience, you must create **Windows Autopilot deployment profiles** and assign them to a group containing the devices. A deployment profile is a collection of settings that determine the behavior of the device during OOBE. Among other settings, a deployment profile specifies a **deployment mode**, which can either be:

1. **User-driven:** devices with this profile are associated with the user enrolling the device. User credentials are required to complete the Microsoft Entra join process during OOBE.
2. **Self-deploying:** devices with this profile aren't associated with the user enrolling the device. User credentials aren't required to complete the Microsoft Entra join process. Rather, the device is joined automatically and, for this reason, specific hardware requirements must be met to use this mode.

To create a Windows Autopilot deployment profile:

- [Intune](#tabpanel_2_intune)
- [Intune For Education](#tabpanel_2_intune-for-education)

For more information, see [Windows Autopilot deployment profiles](https://learn.microsoft.com/en-us/autopilot/profiles).

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Groups** > Select a group from the list.
3. Select **Windows device settings**.
4. Expand the **Enrolment** category.
5. From **Configure Autopilot deployment profile for device** select **User-driven**.
6. Ensure that **User account type** is configured as **Standard**.
7. Select **Save**.

While Intune for Education offers simple options for Windows Autopilot configurations, more advanced deployment profiles can be created from Microsoft Intune admin center. For more information, see [Windows Autopilot deployment profiles](https://learn.microsoft.com/en-us/autopilot/profiles).

### Configure an Enrollment Status Page

An Enrollment Status Page \(ESP\) is a greeting page displayed to users while enrolling or signing in for the first time to Windows devices. The ESP displays provisioning progress, showing applications and profiles installation status.

![Windows OOBE - enrollment status page animation.](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/enroll-autopilot/win11-oobe-esp.gif)

Note

Some Windows Autopilot deployment profiles **require** the ESP to be configured.

To deploy the ESP to devices, you need to create an ESP profile in Microsoft Intune.

Tip

While testing the deployment process, you can configure the ESP to:

- Allow the reset of the devices in case the installation fails
- Allow the use of the device if installation error occurs

This enables you to troubleshoot the installation process in case any issues arise and to easily reset the OS. You can turn these settings off once you are done testing.

For more information, see [Set-up the Enrollment Status Page](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot#create-an-autopilot-device-group-using-intune).

Caution

The Enrollment Status Page \(ESP\) is compatible with Windows 11 SE. However, due to the E Mode policy, devices may not complete the enrollment. For more information, see [Enrollment Status Page](https://learn.microsoft.com/en-us/education/windows/tutorial-deploy-apps-winse/considerations#enrollment-status-page).

### Windows Autopilot end-user experience

Once configuration is complete and devices are distributed, students and teachers are able to complete the out-of-box experience with Windows Autopilot. They can set up their devices at home, at school, or wherever there's a reliable Internet connection.

When a Windows device is turned on for the first time, the end-user experience with Windows Autopilot is as follows:

1. Identify the language and region.
2. Select the keyboard layout and decide on the option for a second keyboard layout.
3. Connect to the internet: if connecting through Wi-Fi, the user is prompted to connect to a wireless network. If the device is connected through an ethernet cable, Windows skips this step.
4. Apply updates: the device looks for and apply required updates.
5. Windows detects if the device has a Windows Autopilot profile assigned to it. If so, it proceeds with the customized OOBE experience. If the Windows Autopilot profile specifies a naming convention for the device, the device is renamed, and a reboot occurs.
6. The user authenticates to Microsoft Entra ID, using the school account.
7. The device joins Microsoft Entra ID, enrolls in Intune and all the settings and applications are configured.

Note

Some of these steps may be skipped, depending on the Windows Autopilot profile configuration and if the device is using a wired connection.

![Windows 11 login screen](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/shared/win11-login-screen.png)

---

## Next steps

With the devices joined to Microsoft Entra tenant and managed by Intune, you can use Intune to maintain them and report on their status.

[Next: Manage devices >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/manage-overview)
