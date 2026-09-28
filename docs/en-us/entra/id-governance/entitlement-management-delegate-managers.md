<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# Delegate access governance to access package managers in entitlement management

To delegate the creation and management of access packages in a catalog, you add users to the access package manager role. Access package managers must be familiar with the need for users to request access to resources in a catalog. For example, if a catalog is used for a project, then a project lead might be an access package manager for that catalog. Access package managers can't add resources to a catalog, but they can manage the access packages and policies in a catalog. When delegating to an access package manager, that person can then be responsible for:

- What roles a user has to the resources in a catalog
- Who will need access
- Who needs to approve the access requests
- How long the project lasts

They can create access packages and policies, including policies referencing existing [connected organizations](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-organization). Once their access packages are created, then they can have other users request or be assigned to those access packages.

This video provides an overview of how to delegate access governance from catalog owner to access package manager.

<iframe src="https://learn-video.azurefd.net/vod/player?id=b999927c-7cfd-4029-8b3a-a59efa9f5e8c" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

In addition to the catalog owner and access package manager roles, you can also add users to the catalog reader role, which provides view-only access to the catalog, or to the access package assignment manager role, which enables the users to change assignments but not access packages or policies.

## As a catalog owner, delegate to an access package manager

Follow these steps to assign a user to the access package manager role:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator).

   Tip

   Other least privilege roles that can complete this task include the Catalog owner.
2. Browse to **ID Governance** > **Catalogs**.
3. On the Catalogs page, open the catalog you want to add administrators to.
4. In the left menu, select **Roles and administrators**.

   ![Catalogs roles and administrators](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-shared/catalog-roles-administrators.png)

5. Select **Add access package managers** to select the members for these roles.
6. Select **Select** to add these members.

## Remove an access package manager

Follow these steps to remove a user from the access package manager role:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator).

   Tip

   Other least privilege roles that can complete this task include the Catalog owner.
2. Browse to **ID Governance** > **Catalogs**.
3. On the Catalogs page, open the catalog you want to add administrators to.
4. In the left menu, select **Roles and administrators**.
5. Add a checkmark next to an access package manager you want to remove.
6. Select **Remove**.

## Next steps

- [Create a new access package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-create)
