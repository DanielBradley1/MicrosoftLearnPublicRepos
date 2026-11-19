<!-- Source: https://learn.microsoft.com/en-us/entra/backup/create-review-difference-reports -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Create and review difference reports in Microsoft Entra Backup and Recovery

A difference report compares the current state of your tenant with a selected backup and highlights what changed.

Difference reports show objects that were **created, modified, soft-deleted, or restored** after the selected backup was taken, along with details about:

- Changed attributes: Properties of the object whose values differ between the backup and the current tenant state.
- Changed links: Changes to the object's relationships with other objects, such as group membership.

Key details:

- A difference report ID identifies the comparison job.
- Create multiple difference reports from the same backup, but only one report can run at a time.
- Difference reports are retained for up to seven days after completion.
- Difference reports against Premium backups skip the data loading phase. The first report against an unloaded Standard backup loads the backup data before calculating differences.

Tip

Create a difference report before starting recovery so you can review and understand the changes in your tenant.

## Prerequisites

You need at least the **Microsoft Entra Backup Reader** role to review difference reports. To review and create difference reports, you need the **Microsoft Entra Backup Administrator** role. The **Global Administrator** role also includes these permissions.

The tenant must meet the [Backup and Recovery prerequisites](https://learn.microsoft.com/en-us/entra/backup/overview#prerequisites) for the selected plan.

## Scope a difference report

When you create a difference report, scope it to control which objects are included in the comparison:

- **All supported objects**: Includes all supported object types in the tenant.
- **By object type**: Includes only selected object types, such as Conditional Access policies, service principals, or groups.
- **By object ID**: Includes only specific objects by their object IDs with their object types specified. Specify up to 100 object IDs across supported object types.

You set the scope when you create the report. You can't change it afterward.

## Create a difference report

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a **Microsoft Entra Backup Administrator**.
2. Go to **Backup and recovery** > **Backups**. Select a backup from the list, and then select **Create difference report**.

   ![Screenshot of the Backups page with a backup selected and the Create difference report pane open.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/create-difference-report-backups-page.png#lightbox)

   Backups are created automatically once per day. Only retained backups appear for selection. The report compares the selected backup with the current tenant state.
3. \(Optional\) Apply filters to limit the scope of objects included in the report. Choose one of these options:

   - **Include all objects in their previous state**: Compares all supported objects in the tenant.
   - **Include only certain types of objects**: Limits the report to selected object types, such as Users and Groups.
   - **Include only specific objects by their ID**: Limits the report to specific objects by their object IDs. Enter up to 100 object IDs across different object types.

4. Select **Create difference report** to start the report.

## Cancel a difference report

Cancel a difference report while it's in progress. Canceled reports don't display partial results. Canceling is useful if you started the report by mistake.

1. Go to **Backup and recovery** > **Difference reports**.
2. Select the in-progress report, and then select **Cancel** in the toolbar.

   ![Screenshot of the Difference Reports page showing an in-progress report selected, a completed report, and the Cancel button highlighted in the toolbar.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/cancel-difference-report.png#lightbox)

## Check difference report statuses

Difference reports move through these statuses as they're created and processed:

| Status | Description |
| --- | --- |
| **Loading data** | For a Standard backup, the system loads data from the selected backup for comparison with the current tenant state. If you previously used the backup for a difference report or recovery, the service reuses the loaded data. Difference reports against Premium backups skip this phase. |
| **In progress** | The system calculates differences between the backup and the current tenant state. Duration depends on the number of objects and the scope of the report. |
| **Completed** | The difference report finished processing and is ready for review. |
| **Failed** | The difference report couldn't be generated because of an error. |
| **Canceled** | The difference report was canceled before completion. |

## Review a difference report

A difference report reflects the current tenant state at the time the report was created and doesn't update automatically. If more changes occur before recovery, create a new difference report.

1. Go to **Backup and recovery** > **Difference reports**. The list shows each report's status, backup details \(ID, timestamp, and availability\), and scoping criteria. It also shows creation and completion times, and the number of objects and links in the report.
2. Select a completed difference report to view its details.

   ![Screenshot of the Difference Reports page showing two completed reports with one report ID highlighted.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/difference-reports-completed.png#lightbox)
3. Review the difference report content. The report lists each object that changed, along with the recovery action that applies during recovery.

   ![Screenshot of a difference report detail page showing user objects with recovery actions and changed attributes.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/difference-report-detail-objects.png#lightbox)

   The report includes this information for each object:

   - **Changed attributes**: Select the count in the **Changed Attributes** column to view the attribute differences. The **Report value** column shows the value captured when the difference report was created. The **Backup value** column shows the value as captured in the selected backup.

     ![Screenshot of the View changed attributes panel showing differences between current state and backup values.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/difference-report-changed-attributes.png#lightbox)
   - **Changed links**: Select the count in the **Changed Links** column to view the relationship differences. The **Report state** column shows the relationship as captured when the difference report was created. The **Backup state** column shows the relationship as captured in the selected backup. The **Recovery action** column indicates the action taken to restore the backup state.

     ![Screenshot of the View changed links panel for a group object, showing group membership changes that would be reverted by recovery.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/difference-report-changed-links.png#lightbox)
   - **Recovery action**: The action that applies when the object is recovered. Possible values:

     - **Update**: Revert changed attributes, links, or both on an existing object.
     - **Restore**: Restore a soft-deleted object.
     - **Soft delete**: Soft-delete an object that was created after the backup.


     ![Screenshot of the difference report detail page with the Recovery Action column highlighted, showing Update and Restore actions for each object.](https://learn.microsoft.com/en-us/entra/backup/media/create-review-difference-reports/difference-report-recovery-action.png#lightbox)

Note

Hard-deleted objects and read-only properties don't appear in difference reports. Objects synced from on-premises directories can appear in difference reports but aren't recoverable.

## Related content

- [View available backups](https://learn.microsoft.com/en-us/entra/backup/view-available-backups)
- [Recover objects](https://learn.microsoft.com/en-us/entra/backup/recover-objects)
