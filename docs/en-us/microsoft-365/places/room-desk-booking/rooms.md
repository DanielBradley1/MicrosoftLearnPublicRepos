<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/rooms -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Rooms

### Overview of Room Booking

Microsoft Places enables **room booking** in Microsoft 365, allowing users to reserve meeting spaces directly from Outlook, Teams, or the Places app. Rooms are represented as resources with their own calendars, which manage availability, scheduling, and conflicts automatically.

**Key concepts:**

1. Rooms are configured within the Places directory and follow a structured hierarchy: **building > floor > \(optional\) section > room**.
2. Each room is a **bookable resource** backed by a mailbox, which acts as the scheduling engine for reservations.
3. Rooms inherit location information from their parent building and floor, rather than maintaining independent location data.
4. Rooms can include metadata such as:

- Capacity
- Devices \(audio, video, display\)
- Accessibility \(for example, wheelchair access\)
- Custom tags to describe room features

**How users book rooms**

Users can book rooms as part of their normal workflow:

1. Add a room while scheduling a meeting in Outlook or Teams.
2. View availability and conflict status automatically.
3. Select rooms based on capacity, location, and available features.
4. Update or remove rooms if meeting details change.

Because the room is tied to a resource calendar, bookings are automatically enforced and conflicts are prevented. This can also be adjusted by IT admins.

**Important**

1. Room booking relies on Exchange resource mailboxes for scheduling and availability management.
2. Rooms must be properly configured in the Places hierarchy to appear in Places Finder and booking experiences.
3. Some advanced features \(such as analytics or auto-release\) may require additional configuration or licensing.

**Prerequisites**

Before creating and configuring rooms, ensure the following steps are complete:

1. Configure **buildings and floors** in the Places directory.
2. Assign appropriate admin permissions \(for example, Places Administrator or Exchange Administrator roles\).
3. Ensure Exchange Online is configured to support resource mailboxes.

### Create a room

You can use either PowerShell or Places management portal to configure rooms. The steps below use PowerShell to align with full administrative control.

**Step 0: Identify the target location \(building and floor\)**

Before creating a room, confirm where it will reside in the hierarchy.

Use the Get-PlaceV3 cmdlet to locate the **PlaceId** of the building and floor:

```powershell
Connect-MicrosoftPlaces

$building = Get-PlaceV3 -Type Building | Where-Object DisplayName -eq "NYC Times Square"

$floor = Get-PlaceV3 -AncestorId $building.PlaceId | Where-Object DisplayName -eq "1"
```

The Get-PlaceV3 cmdlet is used to retrieve metadata and identifiers for places in the hierarchy, including buildings, floors, and rooms.

**Step 1: Create or identify the room mailbox**

Rooms require a **resource mailbox**, which is used for scheduling.

1. If a room mailbox already exists, it can be reused.
2. If not, create a new room mailbox using Exchange Online.

Note

Exact mailbox creation steps depend on Exchange configuration.
