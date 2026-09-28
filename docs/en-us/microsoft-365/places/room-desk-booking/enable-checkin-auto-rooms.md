<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/enable-checkin-auto-rooms -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Enable check in and autorelease \(Rooms\)

Microsoft Places can help optimize resource utilization by providing an integrated check-in and autorelease experience with Teams devices for your desks and rooms respectively.

The check-in and autorelease features work together to ensure efficient use of shared spaces.

When autorelease is enabled, users who have reserved a room can check in using various methods. If no one checks in within a configurable time window, the space releases automatically and becomes available for others to book.

### Eligibility and limitations for room autorelease

Users with a Teams Premium license acquired before April 1, 2026 can check in and use autorelease with any room.

In addition, any user can check in and use autorelease for rooms configured with a space license, including Microsoft Teams Rooms and Microsoft Teams Shared Space licenses. Go to [Microsoft Places overview](https://learn.microsoft.com/en-us/microsoft-365/places/places-overview) for more details on license requirements.

Note

You can enable autorelease for any room in your organization. However, we recommend restricting this feature to rooms with Teams panels or Microsoft Teams Rooms devices to ensure that all users have a way to check in.

### Room check in and autorelease experience

Meeting attendees have multiple options to check in and prevent the room from being automatically released:

- Check in on a Teams panel.
- Check in on a Microsoft Teams Rooms touchscreen console.
- Check in via Teams chat.

### Check in on a Teams panel

Any meeting participant can [check in through a Teams panel](https://learn.microsoft.com/en-us/microsoftteams/devices/check-in-and-room-release).

To learn more about Teams panels, see [Overview of Microsoft Teams panels](https://learn.microsoft.com/en-us/microsoftteams/devices/overview-teams-panels).

Teams panels must be on application version `1449/1.0.97.2024061108` or later to support check-ins.

### Enabling rooms for autorelease

Autorelease can be enabled in four different ways:

- Exchange PowerShell
- Microsoft Places management portal
- Microsoft Teams admin center
- Microsoft Teams panel device

### Enable autorelease for rooms using Exchange PowerShell

Use the [Set-CalendarProcessing](https://learn.microsoft.com/en-us/powershell/module/exchange/set-calendarprocessing?view=exchange-ps&preserve-view=true) Exchange PowerShell cmdlet to enable or modify autorelease for a room.

For example, here's how to enable autorelease for a conference room named **Conference Room 1132**:

```powershell
Set-CalendarProcessing -Identity "Conference Room 1132" -EnableAutoRelease $true
```

The default policy is 10 minutes. For meeting rooms in low-demand areas, you can specify a more lenient policy, expressed in minutes:

```powershell
Set-CalendarProcessing -Identity "Conference Room 1132" -EnableAutoRelease $true -PostReservationMaxClaimTimeInMinutes 20
```

In this example, the room is automatically released if no usage is detected within 20 minutes of the meeting start time.

### Enable autorelease for rooms using Microsoft Places management portal

You can set up autorelease via Places management portal.

1. Go to the room you want to configure.
2. Select **Reservation Settings**.
3. Update the policy as needed.

### Enable autorelease for rooms using Microsoft Teams admin center

You can configure autorelease via the [Teams admin center](https://admin.teams.microsoft.com/).

Navigate to:

**Teams devices** > **Panels** > **Configuration profiles** > **Add or Edit** > **Meeting settings**

Then:

1. Turn on **Release room if no one checks in**.
2. Set **Release after**.
3. Assign the configuration profile to a Teams panel.

For more information, see [Manage devices in Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/devices/device-management).

### Enable autorelease for rooms using Teams panel device

You can configure autorelease directly on a Teams panel device.

Sign in using your admin credentials and navigate to:

**Settings** > **Device settings** > **Teams Admin Settings** > **Meetings**

Then:

1. Turn on **Release room if no one checks in**.
2. Set **Release after**.

Teams panels must be on application version `1449/1.0.97.2024061108` or later.

For more information, see [Check in and autorelease on Teams panels](https://learn.microsoft.com/en-us/microsoftteams/devices/check-in-and-room-release).

Note

It can take up to 48 hours for changes to autorelease settings to take effect. For this reason, we recommend adjusting autorelease before the weekend or when no meetings are scheduled for the next 48 hours.

![Screenshot that shows an image of a person using a Teams panel device.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/person-using-teams-panel-device.png)

![Screenshot that shows Teams Panels home screen. Information about the current meeting appears on the screen with a check in button.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/qr-code-reserved.png)

### Check in on a Microsoft Teams Rooms device

Joining a meeting via the [Microsoft Teams Rooms](https://learn.microsoft.com/en-us/microsoftteams/rooms/) touchscreen console checks you in.

![Screenshot that shows Microsoft Teams Rooms. Example information about the meeting appears on the screen with a Join button.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/join-meeting-through-teams-rooms.png)

### Check in via Teams chat

Meeting organizer and attendees can check in through the Teams meeting chat.

Note

If the room has a Microsoft Teams Rooms device configured as a feature of the room \(using the `-MTREnabled` metadata in the [Set-PlaceV3 cmdlet](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3)\), the check-in reminder in Teams meeting chat doesn't contain the option to check in. Users are required to check in using the Microsoft Teams Rooms device.

Important

If the Teams resource account associated with this room has been updated and [set as a resource](https://learn.microsoft.com/en-us/microsoftteams/rooms/set-as-resource-account-for-shared-teams-devices) in the Teams Rooms Pro Management, check-in messages will no longer be sent to Teams meeting chat. Instead, the room check-in request will be sent to the meeting organizer by email.

Here's the experience:

![Screenshot that shows check in using Teams Chat.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/picture1.png)

Once someone checks into the room, a confirmation appears in the meeting chat:

![Screenshot that shows a message confirming check in.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/picture2.png)

If no one checks in, meeting participants see a message that the room is released:

![Screenshot that shows a message indicating that the room has been released.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/picture3.png)

### Check in through email

If check-in messages can't be sent through Teams meeting chat \(either because the meeting is not a Teams meeting or because the Teams resource account associated with the room has been updated and [set as a resource](https://learn.microsoft.com/en-us/microsoftteams/rooms/set-as-resource-account-for-shared-teams-devices)\), the organizer will receive an email to check in if they have not checked-in through any of the above methods.

![Screenshot showing a Teams chat check-in reminder.](https://learn.microsoft.com/en-us/microsoft-365/places/media/enable-auto-release/email-check-in.png)

Important

There's a known limitation wherein check-in notifications in the Teams meeting chat appear only after at least one meeting participant opens the chat thread.
