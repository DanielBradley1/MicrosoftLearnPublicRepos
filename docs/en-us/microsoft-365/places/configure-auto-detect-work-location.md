<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/configure-auto-detect-work-location -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Configure workplace check-in

This article explains what work location is, how workplace check-in works, its prerequisites and limitations, and how to configure it for your organization.

### Work Location in Microsoft 365

Work location is an extension of the **online-presence** signal in Microsoft Teams and of the **working hours** control in the Microsoft 365 calendar. By bringing together working hours, work location and online presence, users can more easily find out *where* their coworkers are working from in addition to *whether* they're available to connect.

Two distinct location signals are supported:

- **Planned work location**. User-entered intent. Users can create a recurring work plan in the Outlook or Teams calendar Settings, and one-off plans directly in the calendar grid.
- **Actual work location**. System‑detected or manually set location, based on check‑in.

Users can choose whether to share their work location with coworkers. Work location can only be shared inside users' organization and is not visible to Microsoft.

### Workplace check-in

Workplace check-in is a Teams feature which helps users spend less time manually updating their status and more time enjoying in‑person collaboration. Workplace check-in applies to the *actual work location* signal. Planned location remains unchanged.

At the end of a user’s working hours, their actual location is cleared, and the history of actual location isn't available. Furthermore, if a user connects after their set work hours, their work location won't be updated. Users can go to [Set your work hours and location in Outlook](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6) for more information on setting work hours.

**Workplace check-in is always off by default** and must be explicitly enabled and configured for your organization. You can enable workplace check-in for your entire organization or for select users.

When workplace check-in is enabled, users' work location can be updated via two signals: connection to a wireless network or connection to a desk peripheral, such as a monitor. As an admin, you can choose to set up either one or both of these signals. Setting up both signals improves the accuracy of users' work location.

**What workplace check-in does**

- Leverages organization devices and wireless networks to update user’s work location, at the building level if buildings are [configured](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors) in your organization. Otherwise, workplace check-in can only determine in-office vs. remote.
- Works when the Teams app detects a network change or a device connection
- Replaces the need for manual check‑in, but doesn't remove the option

**What workplace check-in doesn't do**

Workplace check-in is not a tracking tool and can't be used to monitor employee attendance. The feature is designed to facilitate collaboration, not compliance or oversight.

- Workplace check-in doesn't prevent users from manually setting or clearing their work location
- Workplace check-in doesn't provide admins with monitoring or reporting views, nor with historical location data.

#### User control

Workplace check-in requires end-users to consent to the Teams desktop app accessing the operating system's Location API. For more details, go to [Manage location sharing in Microsoft Teams](https://support.microsoft.com/office/manage-location-sharing-in-microsoft-teams-583dd649-87fc-4b23-aed6-f4e2279297f9). Furthermore, users can opt in or opt out of workplace check-in based on wireless networks via Teams settings.

#### Admin configuration options

The same policy controls workplace check-in based on desk peripherals and wireless networks. For desk peripheral updates, the policy supports a simple on and off switch. For wireless updates the policy supports an extra parameter, which determines whether workplace check-in is on or off by default:

- **Inform mode**. Users see an informational banner in Microsoft Teams when workplace check-in becomes active for them. The banner explains that the feature is enabled and provides an option for users to opt out. In this mode, a user’s location will be shared with coworkers unless they opt out.
- **Ask mode**. Users see an informational banner in Microsoft Teams when workplace check-in becomes available to them. The banner explains that the feature is available, and provides an option to opt in. In this mode, a user’s location is not shared with coworkers unless they choose to opt in.
- **Off**. Workplace check-in is turned off, users are not prompted, and the feature is disabled regardless of user action.

In Inform and Ask modes, users can change their mind at any time, and turn workplace check-in on or off in Teams Settings. In Off mode, users can't enable workplace check-in independently.

Tenant admins can configure one policy for their entire tenant, or apply different configurations to specific user groups \(for example, based on geography\).

### Prerequisites

- Review [Management prerequisites](https://learn.microsoft.com/en-us/microsoft-365/places/managementoverview) to verify you have the necessary tools installed.
- Configure buildings in Microsoft Places. Go to [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors) for more information.
- Configure desk pools or individual desk accounts. Go to [Configure desk booking](https://learn.microsoft.com/en-us/microsoft-365/places/configure-desk-booking) for more information.
- You must be a Microsoft Teams administrator to enable workplace check-in in Teams.
- You must be a Microsoft Exchange administrator to configure the SSID list and to configure the BSSID list.
- Workplace check-in requires Microsoft Teams desktop app, on either Windows or macOS. Web and mobile versions of Teams are not supported.

### Enable workplace check-in policy

Use Teams PowerShell cmdlets to create a new Teams workplace check-in policy instance, then add users or groups for whom you want to enable workplace check-in to the policy instance.

```powershell
New-CsTeamsWorkLocationDetectionPolicy -Identity wld-enabled -EnableWorkLocationDetection $true
```

```powershell
Grant-CsTeamsWorkLocationDetectionPolicy -PolicyName wld-enabled -Identity testuser@testorg.example.com
```

For more information on how to configure the policy, check out these articles:

- [New-CsTeamsWorkLocationDetectionPolicy](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/new-csteamsworklocationdetectionpolicy)
- [Set-CsTeamsWorkLocationDetectionPolicy](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/set-csteamsworklocationdetectionpolicy)
- [Get-CsTeamsWorkLocationDetectionPolicy](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/get-csteamsworklocationdetectionpolicy)
- [Grant-CsTeamsWorkLocationDetectionPolicy](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/grant-csteamsworklocationdetectionpolicy)

### Enable workplace check-in via peripheral plug-in

Desk peripherals must be associated with desk pools or individual desks for workplace check-in via peripheral plug-in to work. Go to [Configure desk peripherals](https://learn.microsoft.com/en-us/microsoft-365/places/configure-desk-peripherals) for more information. After configuring peripherals, wait 24–48 hours for your changes to propagate before testing.

When a user is signed into Teams on their Windows or macOS device and then plugs into a peripheral that an admin has configured at a desk that's available to book, then their work location automatically updates to **in-office**. If the desk pool or individual desk is parented to a building, the user's work location updates to a specific building.

To learn more about the end-user experience, go to [First things to know about bookable desks in Microsoft Teams](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-in-microsoft-teams-5d10c217-1205-48a1-a883-ff4533f4ae71).

### Enable workplace check-in via connection to a wireless network

To enable workplace check-in via connection to a wireless network, an admin must first [configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors), then configure the SSID list and configure the BSSID list. Once the configuration is complete, Teams can update users' work location to the building associated to the BSSID that the device is connected to.

#### Configure the SSID list

1. Identify the SSIDs of your wireless networks.
2. Configure the SSID list in Places with the following command. You can separate multiple SSIDs with a semicolon \(;\).

   ```powershell
   Set-PlacesSettings -Collection Presence -WorkplaceWifiNetworkSSIDList 'Default:SSID-1;SSID-2'
   ```

If you configure the SSID list but not the BSSID list, users' locations will show as **In the office** when they connect to a wireless network. To enable building-level work location, you must also configure the BSSID list.

#### Configure the BSSID list

To map BSSIDs to buildings in the Places directory:

1. Create a `.csv` file containing all BSSIDs and their corresponding building names. The file must include a header row with the fields `BSSID` and `BuildingName`.
2. Map building names to Places directory buildings.
   | BSSID | BuildingName |
   | :--- | :--- |
   | D0:4D:C6:AA:1B:20 | Dublin 5 |
   | A1:4D:B6:25:1B:40 | Dublin 5 |
   | 15:AD:C6:AF:1B:11 | building 4 |


   ```PowerShell
   Add-WifiDevices -Action MapBuildings -InputFilePath test-file.csv
   ```


   This command compares the building names from your input file with Places directory building names \(case insensitive\). It then generates a `BuildingMapping.csv` file that shows the building names from your input file and their corresponding Places directory building names. Each building name with no matches is shown on its own line.

   | BuildingName | PlacesDirectoryBuildingName |
   | :--- | :--- |
   | Dublin 5 | Dublin 5 |
   | Building 4 | building 4 |
   | bldg3 |  |
   | building 2 |  |


   This command also generates a `PlacesDirectoryBuildings.csv` file. This file lists all available Places directory buildings and is intended to help with manual mapping.

3. Update `BuildingMapping.csv` as necessary so that all building names correspond to valid Places directory building entries.
4. Upload the BSSID list:

   ```PowerShell
   Add-WifiDevices -Action UploadEntries -InputFilePath test-file.csv -BuildingMappingFile mapping-file.csv
   ```

### Manage Places directory entries individually

If you prefer to manage device entries individually, you can use the following cmdlets:

- [New-PlaceDevice](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/new-placedevice)
- [Get-PlaceDevice](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placedevice)
- [Set-PlaceDevice](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placedevice)
- [Remove-PlaceDevice](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/remove-placedevice)

Note

When using these cmdlets, ensure that the BSSID is set to both the DeviceId and MACAddress fields.

## Onboarding checklist

The following checklist helps administrators and users complete the required setup steps and ensure workplace check-in is configured correctly.

#### Check 1. Has the tenant admin enabled workplace check-in?

In Teams, go to **Settings** > **Privacy**, if the user sees “Automatically setting your work location has been turned off by your IT department", it means that tenant admin hasn't enabled this feature for the user.

![Screenshot shows the Teams Settings experience when workplace check-in is turned off.](https://learn.microsoft.com/en-us/microsoft-365/places/media/configure-auto-detect-work-location/workplace-check-in-turned-off.png)

Contact tenant admin if the user wants to enable this feature.

#### Check 2. Has the user granted OS location permissions to Teams?

Workplace check-in requires users to allow the Teams app to access their location through their operating system's location settings.

In Windows, go to **Settings** > **Privacy & security** > **Location**, and verify that location access is enabled for Teams.

![Screenshot shows the Windows Location Settings experience for Teams.](https://learn.microsoft.com/en-us/microsoft-365/places/media/configure-auto-detect-work-location/windows-location-app-settings.png)

In macOS, verify similar settings in the system setting.

#### Check 3. Has the user enabled the manage my work location setting in Teams?

In Teams, go to **Settings** > **Privacy**, and verify that **Manage my work location** is turned on.

![Screenshot shows the Teams Settings experience when Manage my work location is turned on.](https://learn.microsoft.com/en-us/microsoft-365/places/media/configure-auto-detect-work-location/manage-my-work-location.png)

#### Check 4. Is the user connected to an onboarded corporate Wi-Fi network?

To enable workplace check-in via Wi-Fi, users must connect to a corporate Wi‑Fi network whose SSID has been onboarded by the tenant admin. Verify that the device is connected to Wi‑Fi and not to a wired Ethernet network. Workplace check-in via Wi‑Fi is not supported when the device is connected to Ethernet, either directly or through a docking station.

## Frequently Asked Questions

**What is workplace check-in, and what does it do?** This is a Microsoft Teams feature that helps employees keep their work location up to date, so coworkers can coordinate in‑person work. It's not a monitoring or surveillance tool and does not track movement, attendance, or store historical location data.

**Can workplace check-in be used to monitor employees?** No, because users can manually set or clear their work location at any time, whether they're inside or outside their corporate network. For example, they can mark themselves as in-office or even in a specific building while working from home, or mark themselves as remote while working on‑site. This is by design, as workplace check-in is meant to improve in‑person collaboration and coordination rather than monitor employees.

**Is workplace check-in turned on automatically for employees?** No. Workplace check-in is off by default in every tenant and must be enabled and configured by admins. For Wi-Fi based workplace check-in, admins can choose between "Inform mode" \(users can opt-out\) and "Ask mode" \(users can opt in\). In both cases, users are always informed and can opt in or opt out before any location is shared. Furthermore, users must also grant operating‑system‑level location permission to Microsoft Teams for workplace check-in to work.

**Can employees control or override their work location?** Yes. Employees remain in control by design. Users can manually set, override, or clear their work location at any time, whether they're inside or outside corpnet. Manually setting or clearing the work location overrides workplace check-in and prevents further workplace check-ins from being triggered for the remainder of the day.

![Screenshot shows the work location setting experience for Teams.](https://learn.microsoft.com/en-us/microsoft-365/places/media/configure-auto-detect-work-location/teams-set-work-location.png)

**What information is visible to coworkers?** Users choose whether to share their work location with coworkers in the Teams and Outlook Calendar setting. When sharing is enabled, coworkers can see work‑location signal \(in the office, in a specific building, or remote\) whether it was set manually or automatically.

**How does workplace check-in via Wi-Fi work?** Workplace check-in uses network change events, such as connecting to a Wi‑Fi network, switching between Wi‑Fi networks, or waking a device from sleep. Workplace check-in doesn't continuously poll location. If a user switches to Ethernet after connecting to Wi‑Fi, Teams may clear or retain location depending on the scenario. Work location is not automatically updated on desktop computers connected via Ethernet. Users must grant OS‑level location permission to Teams for the workplace check-in feature to function.

**Does the work location signal expire?** Users can manually clear their work location at any time. Users' work location is automatically cleared at the end of their working hours, which can be configured in the Teams and Outlook calendar settings.

**Does workplace check-in work outside of users' working hours?** No. If users connect to a peripheral or wireless network outside of their working hours, their work location won't be automatically updated. At the end of a user’s working hours, their work location is cleared and workplace check-in via Wi-Fi won't be triggered for the remainder of the day.

Users can go to [Set your work hours and location in Outlook](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6) for more information on setting work hours.

**Does workplace check-in work outside corporate networks?** No. Workplace check-in only works when users connect to a peripheral or a wireless network configured in their tenant. Connecting to the networks or peripherals of another organization is ignored \(it won't update users' work location to that organization's buildings\).

**Does workplace check-in support mobile devices?** No. Workplace check-in is currently available only in the Teams desktop app on Windows and macOS.
