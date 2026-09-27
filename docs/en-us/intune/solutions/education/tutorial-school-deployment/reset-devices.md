<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/reset-devices -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Reset and wipe devices

## Device reset options

There are different scenarios that require a device to be reset, for example:

- The device isn't responding to commands.
- The device is lost or stolen.
- It's the end of the life of the device.
- It's the end of the school year and you want to prepare the device for a new school year.
- The device has hardware problems and you want to send it to the service center.

![The device lifecycle for Intune-managed devices - retirement](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/reset-devices/retire.png)

Intune provides reset functionalities that enable IT administrators to remotely execute them:

- **Factory reset** \(also known as **wipe**\) is used to wipe all data and settings from the device, returning it to the default factory settings.
- **Autopilot reset** is used to return the device to a fully configured or known IT-approved state.

- **Factory reset** \(also known as **wipe**\) is used to wipe all data and settings from the device, returning it to the default factory settings.

### Factory reset \(wipe\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Return a device to original settings

A factory reset, or a wipe, reverts a device to the original settings when it was purchased. All settings, applications, and data installed on the device after purchase are removed. By default, the device is also removed from Intune management.

Once the wipe is completed, the device is in out-of-box experience.

- [Intune](#tabpanel_1_intune)
- [Intune For Education](#tabpanel_1_intune-for-education)

Here are the steps to perform a factory reset from Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **All devices**.
3. Select the device you want to reset.
4. Select **Wipe** and follow the instructions.
5. Select **Wipe** to confirm the action.

Here are the steps to perform a factory reset from Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Devices**.
3. Select the device you want to reset > **Factory reset**.
4. Select **Factory reset** to confirm the action.

[![Three screenshots showing the device being wiped, ending up in OOBE](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/reset-devices/win11-wipe.png)](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/reset-devices/win11-wipe.png#lightbox)

Consider using factory reset in the following example scenarios:

- The device isn't working properly.
- It's the end of school year and you want to prepare the device for a new school year.
- You need to reassign the device to a different student, and you want to reset the device to its original settings.
- You're returning a device to the service center, and you want to remove all data and settings from the device.

Tip

Consider that once the device is wiped, the new user will go through OOBE. This option may be ideal if the device is also registered in Windows Autopilot to make the OOBE experience seamless, or if you plan to use a provisioning package to re-enroll the device.

### Windows Autopilot Reset

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Return a device to original settings but maintain enrollment

Windows Autopilot Reset is ideal when all data on a device needs to be wiped, but the device remains enrolled in your tenant.

Once the Windows Autopilot reset action is completed, the device asks to chose region and keyboard layout, then it displays the sign-in screen.

- [Intune](#tabpanel_2_intune)
- [Intune For Education](#tabpanel_2_intune-for-education)

Here are the steps to perform a Windows Autopilot reset from Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **All devices**.
3. Select the device you want to reset.
4. Select **Autopilot Reset** and follow the instructions.
5. Select **Yes** to confirm the action.

Here are the steps to perform a Windows Autopilot reset from Intune for Education:

1. Sign in to the [Intune for Education portal](https://intuneeducation.portal.azure.com).
2. Select **Devices**.
3. Select the device you want to reset > **Autopilot reset**.
4. Select **Autopilot reset** to confirm the action.

![Three screenshots showing the device being wiped, ending up in the login screen](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/reset-devices/win11-autopilot-reset.png)

Consider using Windows Autopilot reset in the following example scenarios:

- The device isn't working properly, and you want to reset it without reimaging it.
- It's the end of school year and you want to prepare the device for a new school year.
- You need to reassign the device to a different student, and you want to reset the device to without requiring the student to go through OOBE.

Tip

Consider that the end user will **not** go through OOBE, and the association of the user to the device in Intune doesn't change. For this reason, this option may be ideal for devices that have been enrolled in Intune as *shared devices* \(for example, a device that was enrolled with a provisioning package or using Windows Autopilot self-deploying mode\).

## Wiping and deleting a device

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Wipe and remove a device from management

There are scenarios that require a device to be deleted from your tenant, for example:

- The device is lost or stolen \(for iOS devices, you may consider using [Lost Mode](https://learn.microsoft.com/en-us/intune/device-management/actions/lost-mode) instead\).
- It's the end of the life of the device.
- The device is replaced or has a new hardware components.

Important

The following actions should only be performed for devices that are no longer going to be used in your tenant.

To completely remove a device, you need to perform the following actions:

1. If possible, perform a **factory reset \(wipe\)** of the device. If the device can't be wiped, delete the device from Intune using [these steps](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe).
2. If the device is registered in Windows Autopilot, delete the Windows Autopilot object using [these steps](https://learn.microsoft.com/en-us/intune/device-management/actions/delete).
3. Delete the device from Microsoft Entra ID using [these steps](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices).

1. If possible, perform a **factory reset \(wipe\)** of the device. If the device can't be wiped, delete the device from Intune using [these steps](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe).
2. Delete the device from Microsoft Entra ID using [these steps](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices).

---

[Next: Troubleshoot and get help >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/troubleshoot-overview)
