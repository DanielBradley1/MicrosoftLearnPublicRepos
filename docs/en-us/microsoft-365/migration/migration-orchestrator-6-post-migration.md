<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-6-post-migration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Post-migration tasks and cleanup

After the migration completes, you should remove permissions and return the tenants to their original nonmigration state. If you want to migrate again in the future, you need to restore all these permissions and settings. To remove the data and permissions, you need to import the individual modules before deletion.

### Delete batch data

This feature allows you to delete the data associated with a batch from the migration system. It deletes the data within 30 days of the request.

```powershell
Remove-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id> 
```

Only batches in a terminal state can be canceled. Either cancel the batch, or wait for all users to reach a terminal state of Canceled, Failed, or Completed.

Note

Delete batch data is a destructive action and should only be used for after all migrations between the two tenants are complete. This deletion isn't an action to clean up in-progress or discarded migration batches. Deleting batch data affects future migrations the batch would inform. We don't recommend deleting batch data until the entire migration completes. Only use this option when you finish all migrations and want to permanently delete data.

### Delete data and permissions

Identity mapping data is stored until you explicitly delete it.

Use the `Remove-CtimData -SourceTenantGuid <SourceTenantGuid>` cmdlet to remove identity mapping data from the target tenant. Use the `Remove-CtimData -TargetTenantGuid <TargetTenantGuid>` cmdlet to remove identity mapping data from the source tenant.

Post-migration steps for OneDrive are available in [Step 7 of our OneDrive documentation](https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-tenant-onedrive-migration-step7?view=o365-worldwide).

- Use the [Remove-OrganizationRelationship](https://learn.microsoft.com/en-us/exchange/sharing/organization-relationships/remove-an-organization-relationship#use-exchange-online-PowerShell-to-remove-an-organization-relationship) cmdlet to remove existing organization relationships for source or destination servers after the migration is complete.
- Use the [Remove-MigrationEndpoint](https://learn.microsoft.com/en-us/PowerShell/module/exchange/remove-migrationendpoint) cmdlet to remove existing migration endpoints for source or destination servers after the migration is complete.
- Use the `Revoke-CTMSAppPermissions` cmdlet to remove permissions for the CTMS \(Cross-Tenant Migration Service\) application \(only on the target\).

```powershell
# Clean up CTMS Permissions
Connect-MgGraph # Use Target Tenant Admin permissions, verify w/ Get-MgContext
$ctimAppId = '90fb47fc-e46d-4fc5-9833-8517359f2daf' #Identity Mapping 1P app
$permissionId = '42eb8f30-cb38-433e-9651-006680f3b238' # Permission ID for IdentityMapping-Experimental-Internal.Read from 1P portal
$ctmsAppId = '6eda910c-74a9-491b-bda3-88692d503655' # CTMS App Id
$fpAppSp = Get-MgServicePrincipal -Filter "appId eq '${ctimAppId}'"
$ctmsSp = Get-MgServicePrincipal -Filter "appId eq '${ctmsAppId}'"
$ctmsRole = Get-MgServicePrincipalAppRoleAssignedTo -ServicePrincipalId $fpAppSp.Id | Where {$_.PrincipalId -eq $ctmsSp.Id -and $_.AppRoleId -eq $permissionId}
Remove-MgServicePrincipalAppRoleAssignedTo -AppRoleAssignmentId $ctmsRole.Id -ServicePrincipalId $fpAppSp.Id
Remove-MgServicePrincipal -ServicePrincipalId $ctmsSp.Id
```

Check which CTMS app you provisioned. The ctmsAppId is one of:

- '506cf32b-5cbe-4ced-84c6-c7bde303f77c'
- '6eda910c-74a9-491b-bda3-88692d503655'

To remove the service principals and apps for the Teams Meetings app and Mailbox app, go to the Microsoft 365 admin center and remove all permissions.

### User cleanup

Users remain on the source tenant after migration as Mail-Users. Depending on your organization's business needs, you can choose to remove or maintain these users.
