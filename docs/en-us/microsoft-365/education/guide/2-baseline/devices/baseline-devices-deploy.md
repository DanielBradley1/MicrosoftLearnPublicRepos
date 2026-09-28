<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-deploy -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 4: Deploy and manage devices with Intune and Intune for Education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-devices.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

## Deploy devices

[Enroll your devices into Intune.](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-overview?pivots=windows)

Select one of the following options to learn the next steps about the enrollment method you chose:

- [Automatic Intune enrollment via Microsoft Entra join](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-entra-join)
- [Automatic Intune enrollment with provisioning packages](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-package)
- [Automatic Intune enrollment with Windows Autopilot](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-autopilot)
- [Enroll with Company Portal **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-ios-company-portal)
- [Enroll devices with Automated Device Enrollment **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-ios-ade)
- [Enroll devices with Apple Configurator **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/enroll-ios-apple-configurator)

## Manage devices

Microsoft Intune offers a streamlined remote device management experience throughout the school year. IT administrators can optimize device settings, deploy new applications, updates, ensuring that security and privacy are maintained.

With Intune, there are several ways to manage students' devices. Groups can be created to organize devices and students, to facilitate remote management. You can determine which applications students have access to, and fine tune device settings and restrictions. You can also monitor which devices students sign in to, and troubleshoot devices remotely.

Learn more about [managing devices with Intune](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/manage-overview?tabs=intune).

### Remote actions

Intune allows you to perform actions on devices without having to sign in to the devices. For example, you can send a command to a device to restart or to turn off, or you can locate a device.

Learn more about [remote actions](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/manage-overview?tabs=intune#remote-actions).

### Remote assistance

With devices managed by Intune, you can remotely assist students and teachers that are having issues with their devices.

Learn more about [remote assistance](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/manage-overview?tabs=intune#remote-assistance).

### Device inventory and reporting

With Intune, it's possible view and report on current devices, applications, settings, and overall health. You can also download reports to review or share offline.

Learn more about [device inventory and reporting](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/manage-overview?tabs=intune#device-inventory-and-reporting).

### Device reset options

Intune provides reset functionalities that enable IT administrators to remotely execute them:

- [Factory reset](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/reset-wipe?tabs=intune&pivots=windows#factory-reset-wipe) \(also known as wipe\) is used to wipe all data and settings from the device, returning it to the default factory settings.
- [Autopilot reset](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/reset-wipe?tabs=intune&pivots=windows#autopilot-reset) is used to return the device to a fully configured or known IT-approved state.

Learn more about [device reset options](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/reset-wipe?tabs=intune&pivots=windows#device-reset-options).

### Wiping and deleting a device

To completely remove a device, you need to perform the following actions:

1. If possible, perform a factory reset \(wipe\) of the device. If the device can't be wiped, delete the device from Intune using [these steps.](https://learn.microsoft.com/en-us/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
2. If the device is registered in Autopilot, delete the Autopilot object using [these steps.](https://learn.microsoft.com/en-us/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
3. Delete the device from Microsoft Entra ID using [these steps.](https://learn.microsoft.com/en-us/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-azure-active-directory-portal)

Learn more about [wiping and deleting a device](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/reset-wipe?tabs=intune&pivots=windows#wiping-and-deleting-a-device).

## Next steps

Now that you completed the devices deploy and management, you're ready to review some Microsoft Windows 11 features and tips.

[Next: Microsoft Windows 11 features and tips>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-windows/baseline-reference-windowsfaq)
