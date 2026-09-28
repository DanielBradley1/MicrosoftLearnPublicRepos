<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/howto-delete-agent-identity -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# How to delete and restore agent identity objects

When you delete an agent identity blueprint, Microsoft Entra automatically cleans up all associated child agent identities and agents' user accounts. All deletions are soft deletions — deleted objects move to the recycle bin and can be restored within 30 days.

For a conceptual overview of how cascade cleanup works and quota considerations, see [Agent identity deletion works](https://learn.microsoft.com/en-us/entra/agent-id/concept-agent-identity-deletion).

## Prerequisites

To delete and restore agent identity objects, you need:

- [Agent ID Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#agent-id-administrator) to view and manage agent identity objects.
- [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) to delete the blueprint application and its service principal.
- The `Application.ReadWrite.All` permission for Microsoft Graph API or Microsoft Entra PowerShell operations.
- The `AgentIdentity.ReadWrite.All` permission to permanently delete soft-deleted agent identities.
- Owners of an agent identity blueprint can delete agent identity objects associated with that blueprint without these roles.

## Delete a blueprint

Deleting agent identity objects isn't supported in the Microsoft Entra admin center. Use Microsoft Graph API or Microsoft Entra PowerShell to delete blueprints and agent identities.

You can delete the agent identity blueprint and blueprint principal separately. Deleting the app registration also deletes the principal. Deleting only the principal leaves the app registration in place.

Note

Standard deletion is always soft deletion. Objects are moved to the recycle bin, but not immediately removed. Permanent deletion happens automatically after 30 days, or you can force it using the standard hard-delete process described in [Deleting and recovering applications FAQ](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/delete-recover-faq).

- [Microsoft Graph API](#tabpanel_1_microsoft-graph-api)
- [Microsoft Entra PowerShell](#tabpanel_1_microsoft-entra-powershell)

To delete the blueprint application \(which also deletes the principal\):

```http
DELETE https://graph.microsoft.com/v1.0/applications/{blueprint-app-object-id}
```

To delete only the blueprint principal:

```http
DELETE https://graph.microsoft.com/v1.0/servicePrincipals/{blueprint-principal-object-id}
```

Note

Explicit hard deletion of a blueprint principal \(`permanentDelete`\) is blocked. Use the standard delete endpoint shown above.

To delete the blueprint application \(which also deletes the principal\):

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
Remove-EntraApplication -ObjectId <blueprint-app-object-id>
```

To delete only the blueprint principal:

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
Remove-EntraServicePrincipal -ObjectId <blueprint-principal-object-id>
```

After you delete the blueprint or its principal, Microsoft Entra automatically soft deletes all associated child agent identities and agents' user accounts. For more information on this process, see [Agent identity deletion](https://learn.microsoft.com/en-us/entra/agent-id/concept-agent-identity-deletion).

Important

If you restore the blueprint principal before the cascade cleanup runs, child agent identities aren't affected. After the cleanup runs, each child identity must be restored individually. Restoring the blueprint principal doesn't reverse cascade deletions that already occurred.

## Restore a blueprint principal

You can restore a soft-deleted blueprint principal within 30 days. Restoring agent identity objects isn't supported in the Microsoft Entra admin center. Use Microsoft Graph API or Microsoft Entra PowerShell.

- [Microsoft Graph API](#tabpanel_2_microsoft-graph-api)
- [Microsoft Entra PowerShell](#tabpanel_2_microsoft-entra-powershell)

```http
POST https://graph.microsoft.com/v1.0/directory/deletedItems/{blueprint-principal-object-id}/restore
```

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
Restore-EntraDeletedDirectoryObject -Id <blueprint-principal-object-id>
```

## Restore child agent identities

If the cascade cleanup already ran and child agent identities were soft deleted, restore each one individually.

Note

The Microsoft Graph `/directory/deletedItems` endpoint doesn't support filtering by agent identity type. Query for deleted service principals and filter results on the client side using known object IDs, app IDs, or display names to identify the correct agent identities.

- [Microsoft Graph API](#tabpanel_3_microsoft-graph-api)
- [Microsoft Entra PowerShell](#tabpanel_3_microsoft-entra-powershell)

1. List soft-deleted service principals to find affected agent identities:

   ```http
   GET https://graph.microsoft.com/v1.0/directory/deletedItems/microsoft.graph.servicePrincipal
   ```

2. Filter the results on the client side to identify agent identities linked to your blueprint, then restore each one:

   ```http
   POST https://graph.microsoft.com/v1.0/directory/deletedItems/{agent-identity-object-id}/restore
   ```

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'

# List deleted service principals and identify agent identities
Get-EntraDeletedServicePrincipal

# Restore each agent identity individually
Restore-EntraDeletedDirectoryObject -Id <agent-identity-object-id>
```

## Permanently delete agent identity objects

Soft-deleted objects continue to count toward [directory quota](https://learn.microsoft.com/en-us/entra/identity/users/directory-service-limits-restrictions) until they're permanently deleted. If you're at the 250 agent identity limit for a blueprint using app-only permissions, you might need to force permanent deletion to free up quota immediately rather than waiting for the 30-day retention period to expire. Permanent deletion of an agent identity blueprint principal is blocked. To permanently free quota used by a blueprint principal, wait for the 30-day retention period to expire.

Caution

Permanently deleted objects can't be restored. Only permanently delete objects when you're certain they're no longer needed.

- [Microsoft Graph API](#tabpanel_4_microsoft-graph-api)
- [Microsoft Entra PowerShell](#tabpanel_4_microsoft-entra-powershell)

Permanently delete a soft-deleted agent identity:

```http
DELETE https://graph.microsoft.com/v1.0/directory/deletedItems/{agent-identity-object-id}
```

Permanently delete a soft-deleted blueprint application:

```http
DELETE https://graph.microsoft.com/v1.0/directory/deletedItems/{blueprint-app-object-id}
```

Permanently delete a soft-deleted agent identity:

```powershell
Connect-Entra -Scopes 'AgentIdentity.ReadWrite.All'
Remove-EntraDeletedDirectoryObject -DirectoryObjectId <agent-identity-object-id>
```

Permanently delete a soft-deleted blueprint application:

```powershell
Connect-Entra -Scopes 'Application.ReadWrite.All'
Remove-EntraDeletedDirectoryObject -DirectoryObjectId <blueprint-app-object-id>
```

## Agents' user accounts

Agents' user accounts are paired 1:1 with agent identities. If agents' user accounts aren't automatically cleaned up as part of cascade deletion, delete them manually.

- [Microsoft Graph API](#tabpanel_5_microsoft-graph-api)
- [Microsoft Entra PowerShell](#tabpanel_5_microsoft-entra-powershell)

```http
DELETE https://graph.microsoft.com/v1.0/users/{agent-user-object-id}
```

```powershell
Connect-Entra -Scopes 'User.ReadWrite.All'
Remove-EntraUser -UserId <agent-user-object-id>
```

## Related content

- [Understand agent identity deletion](https://learn.microsoft.com/en-us/entra/agent-id/concept-agent-identity-deletion)
- [Create and delete agent identities](https://learn.microsoft.com/en-us/entra/agent-id/create-delete-agent-identities)
- [Deleting and recovering applications FAQ](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/delete-recover-faq)
