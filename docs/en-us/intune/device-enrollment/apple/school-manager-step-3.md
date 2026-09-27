<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-3 -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Sync and distribute school devices

After you assign Microsoft Intune permission to manage your Apple School Manager devices, sync Intune with the Apple service to see your managed devices in the admin center.

## Start a sync

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), return to **Enrollment program tokens**.
2. Select a token in the list.
3. Select **Devices** > **Sync**.

   ![Screenshot of the Enrollment Program Devices node and Sync link.](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/media/setup-automated-ios/image06.png)

To follow Apple's terms for acceptable enrollment program traffic, Intune imposes the following restrictions:

- A full sync can run no more than once every seven days. During a full sync, Intune refreshes every Apple serial number assigned to Intune. If a full sync is attempted within seven days of the previous full sync, Intune only refreshes serial numbers that aren't already listed in Intune.
- Any sync request is given 15 minutes to finish. During this time or until the request succeeds, the **Sync** button is disabled.
- Intune syncs new and removed devices with Apple every 24 hours.

## Assign a policy to devices

Apple School Manager devices managed by Intune must be assigned an enrollment policy before they're enrolled.

1. Return to **Enrollment program tokens**.
2. Select a token in the list.
3. Select **Devices**, and then choose your devices.
4. Select **Assign policy**. Then select a policy for the devices.
5. Select **Assign**.

## Distribute devices to users

You enabled management and syncing between Apple and Intune, and assigned a policy that lets Apple School devices enroll. You can now distribute devices to users. When an Apple School Manager device is turned on, it enrolls in Microsoft Intune. Policies can't be applied to activated devices currently in use until the device is wiped.

## Connect School Data Sync

Microsoft Education is transitioning to a new School Data Sync \(SDS\) experience with enhanced features, starting August 2024 for the Northern Hemisphere and January 2025 for the Southern Hemisphere. The current Apple School Manager support will be retired by December 31, 2024. This new experience offers various enhancements over SDS \(Classic\) including:

- Decoupled data ingestion
- Faster syncs with fewer errors
- Support for larger organizations
- A modern user interface

Please contact Microsoft Education support with questions regarding the transition to the new School Data Sync experience.

## Next steps

This series of articles describes how to set up Microsoft Intune for devices purchased through Apple School Manager.

1. [Prerequisites](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager)
2. [Get an Apple token for school devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-1)
3. [Create an Apple enrollment policy](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-2)
4. 🡺 Sync and distribute devices \(*You are here*\)
