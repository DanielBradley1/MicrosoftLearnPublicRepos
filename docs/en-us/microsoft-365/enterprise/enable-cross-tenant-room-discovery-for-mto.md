<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/enable-cross-tenant-room-discovery-for-mto?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Enable room discovery capability with newly supported attributes \(Private Preview\)

Microsoft 365 admins can enable cross-tenant room discovery in a Multi-Tenant Organization \(MTO\). Once configured, users can search for meeting rooms across different tenants in Global Address List \(GAL\) within the same MTO, and ensure the rooms are visible and correctly identified across tenants.

Important

Enable room discovery capability with newly supported attributes is currently available in preview. Features and availability may change before general availability \(GA\).

Note

This Private Preview is primarily focused on the GAL-based cross-tenant room discovery experience. It allows shared meeting rooms to be correctly represented as room resources and discovered when users browse and book rooms from the Global Address List \(GAL\) across tenants within an MTO.

## Prerequisites

Before you begin, ensure the following prerequisites:

- You're a Global Administrator in the tenant.
- Cross-tenant sync is already set up between source and target tenants.

## Step 1: Synchronize Meeting Rooms as B2B Collaboration Users from MTO Admin Portal.

Follow [this guidance](https://learn.microsoft.com/en-us/microsoft-365/enterprise/sync-users-multi-tenant-orgs) to synchronize room objects from MTO admin portal.

## Step 2: Update CTS Sync Job Schema for Room Attributes

To enable cross-tenant room discovery in a Multi-Tenant Organization \(MTO\), the following Exchange recipient attributes must be synchronized from the source tenant to the target tenant:

- MSExchRecipientDisplayType
- MSExchRecipientTypeDetails

These attributes allow the target tenant to correctly recognize synchronized objects as meeting rooms, rather than standard user mailboxes.

Follow [this guidance](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-multitenant-org-settings) to update CTS sync job schema for room attributes.

## Step 3: Execute Dual-Write for Existing Meeting Rooms

For meeting room mailboxes created **before 05/01/2026**, the following attributes aren't present in Microsoft Entra ID within the source tenant:

- MSExchRecipientDisplayType
- MSExchRecipientTypeDetails

Without these attributes, synced objects will still appear as users instead of rooms after being synchronized to the target tenant.

Executing a dual-write forces Exchange Online to reprocess the room mailbox and ensure these attributes are written and synchronized to the target tenant.

**Steps:**

1. Prepare PowerShell Environment. Install Exchange Online PowerShell Module. If it isn't already installed, run:

   ```powershell
   Install-Module -Name ExchangeOnlineManagement
   ```

2. Connect and authenticate, run:

   ```powershell
   Connect-ExchangeOnline 
   ```

3. Prepare the room mailbox list

   Identify the room mailboxes that are already shared—or planned to be shared — with the target tenant. Example scenario:

   - Source tenant: Contoso
   - Target tenant: Fabrikam
   - Room mailboxes: meetingroom1@contoso.com; meetingroom2@contoso.com


   You may also retrieve all existing room mailboxes using:


   ```powershell
   Get-Mailbox -RecipientTypeDetails RoomMailbox
   ```

4. Force Dual-Write using [Set-Mailbox](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-mailbox) by admin of source tenant for each room mailbox. For example:

   ```powershell
   Set-Mailbox meetingroom1@contoso.com -Type Room
   ```

5. To perform bulk Dual-Write execution \(Recommended for large scale\)

   1. Prepare a CSV file. Ensure that the column name used in the CSV file matches the value referenced in the PowerShell command. For example: rooms.csv
      | Mailbox |
      | --- |
      | meetingroom1@contoso.com |
      | meetingroom2@contoso.com |
   2. Use PowerShell to import the CSV and apply changes: You can use the following command to read the CSV file and apply the changes to each mailbox specified:

      ```powershell
      Import-CSV "C:\path\to\your\file.csv" | ForEach-Object {Set-Mailbox -Identity $_.Mailbox -Type Room}
      ```

6. Verify the result. CTS synchronization job runs about every 40 minutes automatically.
7. After updating the CTS sync job schema, and executing Dual-Write for the source tenant room mailboxes, previously shared room mailboxes should appear in the target tenant GAL with:

   1. Correct meeting room icon
   2. Correct resource mailbox classification \(Room\)

## More Action Required: Rooms Already Shared to Target Tenant Before May 1, 2026

If any room mailboxes were already shared to Fabrikam \(the target tenant\) before May 1, 2026, the corresponding B2B member accounts were already provisioned in Fabrikam before the room-type attributes \(MSExchRecipientDisplayType and MSExchRecipientTypeDetails\) were available in the cross-tenant synchronization \(CTS\) schema, as a result, the existing provisioned B2B accounts don't receive the necessary attribute updates through the provisioning pipeline and therefore cannot be correctly recognized or updated as room resources.

To remediate, the Fabrikam administrator must permanently delete \(hard delete\) the affected B2B member accounts, and the Contoso \(source tenant\) administrator must then reprovision these accounts via Provision on demand or Restart provisioning \(full sync\) from the corresponding cross-tenant synchronization configuration. This process recreates the B2B members in Fabrikam with the correct room-type attributes. Steps to Remediate:

### Part A - Performed by the Fabrikam \(target tenant\) administrator: Hard delete the affected B2B accounts

Choose the option that best matches your scenario:

Option 1: Manual procedure via the Microsoft Entra admin center \(recommended for a few rooms\)

1. Sign in to the Microsoft Entra admin center \(entra.microsoft.com\) as a Global Administrator in the Fabrikam tenant.
2. Navigate to Users > All users, then locate the B2B accounts that correspond to the affected room mailboxes. These accounts appear as external Member users sourced from Contoso.
3. Select each affected B2B account and choose Delete. This performs a soft delete; the object is moved to the recycle bin and remains recoverable for 30 days.
4. In the left navigation, select Deleted users.
5. Select the soft-deleted shadow accounts and choose Delete permanently to hard delete the objects from the Fabrikam tenant.

Option 2: Bulk procedure via Microsoft Graph PowerShell \(recommended for a large number of rooms\)

**Steps**:

1. Prepare a list of the B2B accounts to delete from Fabrikam. Save the list as a CSV file \(for example, rooms.csv\) with a single column named Mailbox. Example: rooms.csv
   | Mailbox |
   | --- |
   | meetingroom1\_contoso.com#EXT#@fabrikam.com |
   | meetingroom2\_contoso.com#EXT#@fabrikam.com |
2. Install the Microsoft Graph PowerShell SDK if it isn't already installed. Run:

   ```powershell
   Install-Module Microsoft.Graph -Scope CurrentUser
   ```

3. Run the following script as a Global Administrator in the Fabrikam tenant:

   ```powershell
   Connect-MgGraph -Scopes "User.ReadWrite.All","User.DeleteRestore.All"
   ```

4. Delete the B2B accounts listed in CSV file.

   ```powershell
   $rooms = Import-Csv "C:\path\to\your\file.csv"
   foreach ($room in $rooms) {
       $upn = $room.Mailbox
       try {
           $shadow = Get-MgUser -UserId $upn -ErrorAction Stop
       }
       catch {
           Write-Warning "Shadow account not found for $upn"
           continue
       }
       Remove-MgUser -UserId $shadow.Id
       Remove-MgDirectoryDeletedItem -DirectoryObjectId $shadow.Id
       Write-Output "Hard deleted: $upn (Id: $($shadow.Id))"
   }
   ```


   Important


   The script performs a permanent \(hard\) deletion of the specified B2B collaboration users. Administrators should carefully verify the CSV file before execution and confirm that every listed object corresponds to an affected room mailbox that requires re-provisioning.

### Part B - Performed by the Contoso \(source tenant\) administrator: Re-provision the affected room mailboxes

Choose the option that best matches your scenario:

Option 1: Manual procedure via the Microsoft Entra admin center \(recommended for a small number of rooms\)

[![Screenshot that shows on demand provision in Entra admin portal.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/enable-cross-tenant-room-discovery-for-mto/image.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/enable-cross-tenant-room-discovery-for-mto/image.png?view=o365-worldwide#lightbox)

1. Sign in to the Microsoft Entra admin center as a Global Administrator in the Contoso tenant.
2. Navigate to Cross-tenant synchronization > Configurations.
3. Select the configuration that corresponds to Fabrikam. The configuration represents the MTO-managed cross-tenant synchronization application.
4. Select **Provision on demand** under the application.
5. Search for and select the room mailbox object that needs to be re-synchronized.
6. Choose Provision to immediately sync the selected room mailbox to Fabrikam. Repeat for each affected room mailbox.

Option 2: Restart provisioning via the Microsoft Entra admin center \(recommended for a large number of rooms with a full sync of all in-scope users in the configuration\)

1. Sign in to the Microsoft Entra admin center as a Global Administrator in the Contoso tenant.
2. Navigate to -tenant synchronization > Configurations.
3. Select the configuration that corresponds to Fabrikam - this is the MTO-managed cross-tenant synchronization application.
4. Select Overview under the application.
5. Choose Restart provisioning. This operation starts a full sync. The sync reprocesses all in-scope user in the configuration, including the affected room mailboxes. It then recreates the B2B collaboration users in Fabrikam with the correct room-type attributes.

   Note

   Restart provisioning performs a full sync of all in-scope users in the configuration, not only the affected room mailboxes. Choose this option when many rooms are affected and a full reprocessing is acceptable. If you need to target only specific rooms without triggering a full sync, use Option 1 \(Provision on demand\) for a few rooms or Option 2 \(Bulk via Microsoft Graph PowerShell\) for a large number.

## Step 4: Set up Room Booking Response

Inbound connectors are required to enable cross tenant room booking, so rooms can automatically respond to meeting requests from other tenants.

[![Screenshot that shows enable room booking response.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/enable-cross-tenant-room-discovery-for-mto/image1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/enable-cross-tenant-room-discovery-for-mto/image1.png?view=o365-worldwide#lightbox)

1. Go to the MTO admin portal
2. Choose Manage settings \(or open a specific tenant → Configurations\)
3. Select **Edit room booking settings** and select which active tenants in an MTO to enable room response for.

## Step 5: Ensure Free/Busy \(Calendar Sharing\) Is Enabled

For room availability to work correctly, calendar information sharing \(Free/Busy\) must be enabled between the same tenant pairs. If it's already enabled previously, you can skip this step. For more information, see [Manage calendar sharing for tenants in your MTO](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-multitenant-org-settings).

## Summary: End-to-End Admin Flow

1. Update MTO sync job schema to include room attributes.
2. Backfill existing rooms using admin cmdlets.
3. Enable cross-tenant room booking in MTO settings.
4. Enable Free/Busy calendar sharing.
5. Validate room booking and availability.

Once completed, your organization can support cross-tenant room discovery and booking as part of its MTO collaboration strategy.
