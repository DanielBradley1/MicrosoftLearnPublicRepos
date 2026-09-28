<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-managed-identity-regional-move -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Move managed identity for Azure resources across regions

There are situations in which you'd want to move your existing user-assigned managed identities from one region to another. For example, you may need to move a solution that uses user-assigned managed identities to another region. You may also want to move an existing identity to another region as part of disaster recovery planning, and testing.

Moving User-assigned managed identities across Azure regions isn't supported. You can however, recreate a user-assigned managed identity in the target region.

## Prerequisites

- Permissions to list permissions granted to existing user-assigned managed identity.
- Permissions to grant a new user-assigned managed identity the required permissions.
- Permissions to assign a new user-assigned identity to the Azure resources.
- Permissions to edit Group membership, if your user-assigned managed identity is a member of one or more groups.

## Prepare and move

1. Copy user-assigned managed identity assigned permissions. You can list [Azure role assignments](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-list-powershell) but that may not be enough depending on how permissions were granted to the user-assigned managed identity. You should confirm that your solution doesn't depend on permissions granted using a service specific option.
2. Create a [new user-assigned managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-manage-user-assigned-managed-identities?pivots=identity-mi-methods-powershell#create-a-user-assigned-managed-identity-2) at the target region.
3. Grant the managed identity the same permissions as the original identity that it's replacing, including Group membership. You can review [Assign Azure roles to a managed identity](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal-managed-identity), and [Group membership](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups).
4. Specify the new identity in the properties of the resource instance that uses the newly created user assigned managed identity.

## Verify

After reconfiguring your service to use your new managed identities in the target region, you need to confirm that all operations have been restored.

## Clean up

Once that you confirm your service is back online, you can proceed to delete any resources in the source region that you no longer use.

## Next steps

In this tutorial, you took the steps needed to recreate a user-assigned managed identity in a new region.

- [Manage user-assigned managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-manage-user-assigned-managed-identities?pivots=identity-mi-methods-powershell#delete-a-user-assigned-managed-identity-2)
