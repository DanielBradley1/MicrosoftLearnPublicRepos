<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/configure-auto-checkin-desk-peripherals -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Configure automatic check in with desk peripherals

When an admin configures desk peripherals for use in Microsoft Places, users can seamlessly reserve specific desks by connecting their Windows or macOS devices to peripherals on the desk. Configuring peripherals also enables optional automatic update of work location, notifications that desks are occupied, usage reports, and more.

Note

- Peripheral plug-in works with the Teams app for Windows and macOS. Download the latest Teams client from [New Microsoft Teams](https://adoption.microsoft.com/microsoft-teams/).
- Peripheral plug-in is designed to work with all models and manufacturers, but depends on the device having unique properties such as Product ID, Vendor ID, or serial number. Microsoft currently supports monitors and devices with both audio and video capabilities. Support for docking stations and webcams is coming soon.

### Collect and associate peripheral information using PowerShell

To configure desk peripherals, you must first create desk pools or individual desk accounts. See [Configure desk booking](https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/desks) for instructions.

After creating these accounts, wait 24–48 hours for the accounts to appear in the Teams Rooms Pro management portal.

After the desk pools and individual desk accounts are visible in the portal, you must associate peripherals to the desk pool or the individual desk account. To associate peripherals, you must use unique identifying information such as the product ID, vendor ID, and serial number of each peripheral.

Microsoft provides a free PowerShell script to fetch peripheral details and ensure they are mapped to the corresponding desk pool or individual desk accounts in the Teams Rooms Pro management portal.

- Download the script [here](https://www.microsoft.com/download/details.aspx?id=106063).
- For detailed instructions, see [Add peripherals to inventory](https://learn.microsoft.com/en-us/microsoftteams/rooms/get-peripheral-information).

Note

The downloads page might link directly to an older version of the script. Check the **Installation Instructions** section of the downloads page for a link to the latest version.

### Enable automatic update of location for users

See [Enable automatic detection of location](https://learn.microsoft.com/en-us/microsoft-365/places/configure-auto-detect-work-location) for a full description of this feature.

The [User control](https://learn.microsoft.com/en-us/microsoft-365/places/configure-auto-detect-work-location) section explains how users can provide or deny consent for location autodetection.

### Testing peripheral plug-in

After configuring peripherals, you must wait 24–48 hours for the changes to propagate.

To test whether a peripheral has been correctly associated with a desk:

1. Sign in to Teams on a Windows or macOS device.
2. Connect to an associated peripheral.
3. Verify that the desk is available for booking.
4. Confirm that a booking appears in your calendar.
5. Confirm that a notification appears in your activity feed stating:
   > "The \[space or desk\] is reserved and ready for you."

To learn more about the end-user experience, see [First things to know about bookable desks in Microsoft Teams](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-in-microsoft-teams-5d10c217-1205-48a1-a883-ff4533f4ae71?preview=true).

### Review usage reports

Usage reports show how desk pools or individual desks are being used.

To learn how to access and interpret desk usage reports, see the [link](https://learn.microsoft.com/en-us/microsoftteams/rooms/bookable-desks#step-6---review-data-in-usage-reports).

## Related links

- [First things to know about bookable desks in Microsoft Teams](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-5d10c217-1205-48a1-a883-ff4533f4ae71)
- [Setting up Bookable desks in Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/rooms/bookable-desks)
