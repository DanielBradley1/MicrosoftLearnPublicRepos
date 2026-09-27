<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/manage-surface -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Management functionalities for Surface devices

Microsoft Surface devices offer advanced management functionalities, including the possibility to manage firmware settings and a web portal designed for them.

## Manage device firmware for Surface devices

Surface devices use a Unified Extensible Firmware Interface \(UEFI\) setting that allows you to enable or disable built-in hardware components, protect UEFI settings from being changed, and adjust device boot configuration. With [Device Firmware Configuration Interface profiles built into Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-dfci-settings-windows), Surface UEFI management extends the modern management capabilities to the hardware level. Windows can pass management commands from Intune to UEFI for Windows Autopilot-deployed devices.

DFCI supports zero-touch provisioning, eliminates BIOS passwords, and provides control of security settings for boot options, cameras and microphones, built-in peripherals, and more. For more information, see [Manage DFCI on Surface devices](https://learn.microsoft.com/en-us/surface/surface-manage-dfci-guide) and [Manage DFCI with Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/dfci-management), which includes a list of requirements to use DFCI.

[![Creation of a DFCI profile from Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/manage-surface/dfci-profile.png)](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/manage-surface/dfci-profile.png#lightbox)

## Microsoft Surface Management Portal

Located in the Microsoft Intune admin center, the Microsoft Surface Management Portal enables you to self-serve, manage, and monitor your school's Intune-managed Surface devices at scale. Get insights into device compliance, support activity, warranty coverage, and more.

When Surface devices are enrolled in cloud management and users sign in for the first time, information automatically flows into the Surface Management Portal, giving you a single pane of glass for Surface-specific administration activities.

To access and use the Surface Management Portal:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Partner Portals** > **Surface Management Portal**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/manage-surface/surface-management-portal.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/manage-surface/surface-management-portal.png" alt="Surface Management Portal within Microsoft Intune" data-linktype="relative-path">
   </a>
   </span>

3. See an **Overview** of your Surface devices.

   - Devices that are out of compliance or not registered, have critically low storage, require updates, or are currently inactive, are listed here.

4. To obtain details on each insights category, select **Insights**.

   - This dashboard displays diagnostic information that you can customize and export.

5. To obtain the device's warranty information, select **Insights**.
6. To review a list of support requests and their status, select **Support**.
