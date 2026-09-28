<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/admin-web-app -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Places Administration Web App

The Microsoft Places Management web application enables Places, Building, and Desk Admins to manage the Places directory, including creating and deleting desks and rooms, configuring desk modes and reservation settings, and identifying unassigned desks. However, its capabilities are limited. The web interface is best suited for individual or small-scale updates, whereas PowerShell is recommended for bulk operations, as cmdlets enable more efficient large-scale management compared to manual, form-based actions.

Important

- The Management Web App is not available on mobile platforms such as Microsoft Teams or Outlook on iOS.
- The "EnablePlacesWebApp" setting must be enabled for the tenant in order for the admin users to access the Management Web App.
- The admin account must have an Exchange license assigned and a mailbox enabled to access the Management Web App.

Note

Batch upload and updates are not currently supported in the Management Web App. For large-scale setups, for example, multiple buildings, we recommend that you use PowerShell. Go to [**License Requirements**](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements) and [**Configure buildings and floors**](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/buildings-floors-sections) for more information.

## Create a new place

1. In the Places management web app, select the **Create new** button.
2. In the dropdown that appears, choose: building, floor, section, room, desk, or desk pool.
3. A **Create** panel appears with various blank metadata fields. Fill in metadata fields with information about the new place.
4. Select the **Create** button.

## Configure desk or desk pool mode

Desks and desk pools support four different modes:

- **Reservable** - Can be reserved in advance
- **Drop-in** - Available on a first-come, first-served basis without prior reservation.
- **Assigned** - Assigned to specified users. This is applicable only for individual desks and does not apply to desk pools.
- **Unavailable** - Not reservable, for example, under maintenance.

Note

For **Drop-in** desks, it is recommended to link peripherals, for example, a monitor or docking station, to the desk. When a user connects their laptop to the peripherals, the desk can be automatically reserved for them.

To learn about setting up peripherals for your desk, go to [**Configure autocheckin desk peripherals**](https://learn.microsoft.com/en-us/microsoft-365/places/room-desk-booking/configure-auto-checkin-desk-peripherals)

To change the mode of a desk or desk pool:

1. In the Places management web app, find the desk or desk pool.
2. Select the ellipsis \(...\) next to it, then select **Edit properties**.
3. Choose the desired mode from the **Mode** dropdown.
4. If **Assigned**, specify a user in **Assigned to** field.
5. If **Unavailable**, provide a reason in **Reason** field.
6. Select **Apply**.

## Configure reservation settings

You can customize the reservation settings for **rooms**, **desks**, and **desk pools**. The available options vary depending on the type.

| Reservation setting | Rooms | Reservable desks/desk pools | Drop-in desks/desk pools |
| --- | --- | --- | --- |
| Set how far in advance users can book | ✅ | ✅ | ❌ |
| Restrict reservation to specific users or groups | ✅ | ✅ | ✅ |
| Limit maximum reservation duration | ✅ | ❌ | ❌ |
| Allow/disallow recurring reservations | ✅ | ✅ | ❌ |
| Enable automatic release if no one checks in | ✅ | ✅ | ❌ |

Note

Reservation settings can't be changed if the desk is in **Assigned** or **Unavailable** mode.

To update reservation settings:

1. In the Places management web app, find the place you want to configure.
2. Select the ellipsis \(...\) next to it, then select **Edit reservation settings**.
3. Adjust settings as needed.
4. Select **Apply**.

## Move a space

You can easily move a room, desk, desk pool, section or floor by editing its properties.

1. In the Places management web app, find the space you wish to move.
2. Select the ellipsis \(...\) then select **Edit properties**.
3. Change the building, floor, and section to the desired location.
4. Select **Apply**.

## Delete a place

You can delete a place that has no child entity associated with it, for example, a room, desk, or desk pool, or an empty section, floor, or building. If the place you want to delete contains child entities, you can either delete all child entities first, or move/reparent them to another location using the Edit properties option.

1. In the Places management web app, find the place that you want to delete.
2. Select the ellipsis \(...\) next to it.
3. In the menu, select **Delete**, then select the **Yes, delete** button.
