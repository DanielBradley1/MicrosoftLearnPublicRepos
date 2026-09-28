<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/enable-checkin-desks -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Enable check in and autorelease \(Desks\)

Microsoft Places can help optimize resource utilization by providing an integrated check-in and autorelease experience with Teams devices for your desks and rooms respectively.

The check-in and autorelease features work together to ensure efficient use of shared spaces.

When autorelease is enabled, users who have reserved a room, desk, or desk pool can check in using various methods. If no one checks in within a configurable time window, the space releases automatically and becomes available for others to book.

### Enabling rooms for autorelease

Autorelease can be enabled in two different ways:

- Exchange PowerShell
- Microsoft Places management portal

### Enabling desks or desk pools for autorelease

Autorelease can be enabled in two different ways:

- Exchange PowerShell
- Places management portal

### Enable autorelease for desks and desk pools using Exchange PowerShell

Use the [Set-CalendarProcessing](https://learn.microsoft.com/en-us/powershell/module/exchange/set-calendarprocessing?view=exchange-ps&preserve-view=true) Exchange PowerShell cmdlet to enable or modify autorelease for a desk or desk pool.

For example, here's how to enable autorelease for a desk named **Desk1234** with an attached mailbox of `desk1234@contoso.com`:

```powershell
Set-CalendarProcessing -Identity "desk1234@contoso.com" -EnableAutoRelease $true
```

The default policy is 10 minutes. For desks in low-demand areas, you can specify a more lenient policy expressed in minutes:

```powershell
Set-CalendarProcessing -Identity "desk1234@contoso.com" -EnableAutoRelease $true -PostReservationMaxClaimTimeInMinutes 60
```

In this example, the desk or desk pool is automatically released if no usage is detected within 60 minutes of the booking start time.

### Enable autorelease for desks and desk pools using Microsoft Places management portal

You can set up autorelease through the Places management portal.

1. Go to the desk or desk pool that you want to configure.
2. Select **Reservation Settings**.
3. Update the autorelease policy as needed.

Note

It can take up to 48 hours for changes to autorelease settings to take effect. For this reason, we recommend adjusting autorelease before the weekend or when no reservations are scheduled for the next 48 hours.

### Eligibility and limitations for desk and desk pool autorelease

Users with a Teams Premium license acquired before April 1, 2026 can check in and use autorelease with any desk.

In addition, any user can check in and use autorelease with desks configured with Microsoft Teams Shared Space licenses. Go to [What is Places?](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements) for more details on license requirements.

### Desk check-in and autorelease experience

Users have multiple options to check in and prevent the desk from being automatically released:

- Check in by plugging their laptop into a desk peripheral.
- Check in to the building where they have a desk reservation.
- Check in through email.

### Check in by plugging their laptop into a desk peripheral

When an admin [links desk peripherals](https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/configure-auto-checkin-desk-peripherals) to the desk or desk pool resource account, users can seamlessly check in to their reservation by plugging into the desk peripheral.

Upon plug-in, the user receives a notification that they are checked in and ready for their reservation.

![Screenshot that shows check in using desk peripheral.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/check-in-with-peripheral-desk.png)

### Check in through email

If the user hasn't checked in through any of the available methods, an email reminder is sent 15 minutes before the desk is automatically released.

The email allows the user to confirm their reservation and prevent autorelease.

![Screenshot that shows check in using email.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/email-check-in.png)

### Coming soon: Check in to a desk when checking in to the building

When a user checks into the building where they have a desk reservation, they will soon also be checked in to their desk reservation automatically.

Until this feature becomes available, users must continue to check in to their desk separately.

## Frequently Asked Questions

For more information, see [Enable check in and autorelease for rooms, desks, and desk pools \(optional\)](https://learn.microsoft.com/en-us/microsoft-365/places/frequently-asked-questions#enable-check-in-and-autorelease-for-rooms-desks-and-desk-pools-optional).
