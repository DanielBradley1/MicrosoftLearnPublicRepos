<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/day-to-day-admin/enable-others-as-places-admins -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Enable others as Places administrators

Microsoft Places supports three different administrator roles:

- Places Administrator
- Places Building Administrator
- Places Desk Administrator

The **Places Administrator** role is assigned and managed through Microsoft Entra ID. The **Places Building Administrator** and **Places Desk Administrator** roles are assigned and managed through Exchange Online.

Assign roles based on the scope of responsibility. Some admins may manage the full Places workload, while others may be delegated specific tasks such as managing buildings or desks.

### Role capabilities

| Role | Responsibilities | Where role is assigned | Permissions and capabilities |
| --- | --- | --- | --- |
| **Places Administrator** | Full management of Places onboarding, operations, and analytics | Microsoft 365 admin center or Microsoft Entra PowerShell | - Enable and disable Microsoft Places features<br>- Upload Places directory data in bulk<br>- Configure occupancy sensors<br>- Create, read, update, and delete maps<br>- Create, read, update, and delete buildings, floors, sections, rooms, desk pools \(workspaces\), and desks in the Places directory<br>- Set places as reservable<br>- Manage reservation settings and autorelease policy for rooms and desks<br>- Assign teams to sections, rooms, and desks<br>- Manage desk mode \(Assigned, Reservable, Drop-in, or Unavailable\)<br>- Assign desks to people |
| **Places Building Administrator** | Manage day-to-day aspects of one or more buildings | Exchange PowerShell | - Configure occupancy sensors<br>- Create, read, update, and delete maps<br>- Update or read properties of existing buildings, rooms, or workspaces<br>- Create, read, update, and delete floors, sections, assigned or unavailable desks in the Places directory<br>- Set places as reservable<br>- Manage reservation policy and autorelease policy for rooms and desks<br>- Assign teams to sections, rooms, and desks<br>- Manage desk mode \(Assigned, Reservable, Drop-in, or Unavailable\)<br>- Assign desks to users<br>- Read all directory data |
| **Places Desk Administrator** | Manage desks | Exchange PowerShell | - Manage desk mode \(Assigned, Reservable, Drop-in, or Unavailable\)<br>- Assign desks to users<br>- Read all directory data |

Note

Places Building Administrators and Places Desk Administrators do not have permission to create resource mailboxes or update room and workspace names and capacities.

**Global Administrator** and **Exchange Administrator** are existing roles and can manage all aspects of Places. However, we recommend assigning the least privileged role necessary to improve organizational security. Use the Global Administrator or Exchange Administrator roles only in exceptional cases.

## Assigning roles

### Places Administrator

You can assign the **Places Administrator** role using the Microsoft 365 admin center, the Microsoft Entra admin center, or the Microsoft Graph API.

#### Microsoft 365 admin center

1. Go to **Roles** > **Role assignments**.
2. Under the **Exchange** tab, select **Places Administrator**, then go to the **Assigned** tab.
3. Add users to the role.

#### Microsoft Entra admin center

1. Go to **Roles & admins**, then **Places Administrator**.
2. Add the role to **Eligible assignments** or **Active assignments**.

### Places Building Administrator and Places Desk Administrator

You can assign the **Places Building Administrator** and **Places Desk Administrator** roles using the `New-ManagementRoleAssignment` Exchange Online PowerShell cmdlet:

1. Connect to Exchange Online using an admin account.
2. Run the following cmdlet in PowerShell.

#### PowerShell

```powershell
New-ManagementRoleAssignment -Role "PlacesBuildingManagement" -User <user_id>
```
