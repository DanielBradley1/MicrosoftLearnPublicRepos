<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-settings -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Configure settings and applications for deploying devices with Intune and Intune for Education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-devices.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Before distributing devices to your users, you must ensure that the devices have the required policies, settings, and applications as they get enrolled in Intune.

## Common education device configuration overview

Intune is a powerful tool that can help education organizations manage their devices and data efficiently. However, configuring the right settings can be a time-consuming task, especially for admins new to the platform. To help accelerate the process, we assembled common configurations based on customer engagements into this reference document. These settings can help ensure the security and compliance of your devices and data, while maximizing the user experience for your students and staff. Whether you're setting up a new tenant or need a quick reference guide, this document is a valuable resource for any education organization looking to optimize their use of Intune.

Note

Adding these settings to an existing Intune tenant and assigning them to devices could potentially cause conflicts with your existing Intune policies. For more information, see [Compliance and device configuration policies that conflict.](https://learn.microsoft.com/en-us/mem/intune/configuration/device-profile-troubleshoot#conflicts)

Configurations:

- [Device restrictions](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-device-restrictions)
- [Windows Update](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-windows-update)
- [Microsoft Edge](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-edge)
- [Delivery Optimization](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-delivery-optimization)

Optional configurations:

- [Windows privacy](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-windows-privacy)
- [Start menu customization](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-start-menu)
- [OneDrive Known Folder Move](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/common-config-settings-catalog-onedrive-knownfoldermove)

## Configure policies

With Intune, you can configure settings for devices in the school, to ensure that they comply with specific policies. For example, you might need to secure your devices, ensuring that they're kept up to date, or you might need to configure all the devices with the same look and feel.

Settings can be assigned to groups:

- If you target settings to a group of users, those settings apply, regardless of what managed devices the targeted users sign in to
- If you target settings to a group of devices, those settings apply regardless of who is using the devices

**[Device Settings](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-settings?tabs=intune&pivots=windows#device-settings)** - Configure settings and assign them to devices.

**[Update policies](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-settings?tabs=intune&pivots=windows#update-policies)** - Configure update policies and assign to devices.

**[Security policies](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-settings?tabs=intune&pivots=windows#security-policies)** - Configure security policies and assign them to devices.

## Configure applications

With Intune, school IT administrators have access to diverse applications to help students unlock their learning potential. This section discusses tools and resources for adding apps to Intune.

Applications can be assigned to groups:

- If you target apps to a group of users, the apps will be installed on any managed devices that the users sign into.
- If you target apps to a group of devices, the apps will be installed on those devices and available to any user who signs in.

**To add applications to your inventory**:

- [Add Apps ***Windows***](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-apps?tabs=intune&pivots=windows#add-apps)
- [Add Apps ***iOS***](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-apps?tabs=intune&pivots=ios#add-apps)

**To assign applications to your store**:

- [Assign Apps ***Windows***](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-apps?tabs=intune&pivots=windows#assign-apps)
- [Assign Apps ***iOS***](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/configure-device-apps?tabs=intune&pivots=ios#assign-apps)

## Next steps

Now that you configured your settings, you're ready to deploy and manage devices.

[Next: Deploy and manage devices>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-deploy)
