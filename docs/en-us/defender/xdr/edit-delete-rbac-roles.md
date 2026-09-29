<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/edit-delete-rbac-roles -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Edit, delete, and export roles in Microsoft Defender unified role-based access control \(RBAC\)

This article walks you through how to edit, delete, and export roles in Microsoft Defender unified role-based access control \(RBAC\). These tasks apply to custom roles you created in unified RBAC and roles imported from Defender for Endpoint, Defender for Identity, or Defender for Office 365. Each section lists the required permissions before the steps.

## Edit roles

To edit roles in Microsoft Defender unified RBAC, follow these steps:

Important

You must be a Security Administrator or higher in Microsoft Entra ID. You can also perform this task if you have all Authorization permissions in Microsoft Defender Unified RBAC. For more information, see [Permission prerequisites](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac#permissions-prerequisites).

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) as security administrator or higher.
2. In the navigation pane, select **Permissions**.
3. Select **Roles** under Microsoft Defender XDR to get to the **Permissions and roles** page.
4. Select the role you want to edit. You can only edit one role at a time.
5. Once selected, a flyout pane opens where you can edit the role:

   [![Screenshot of the edit roles flyout page](https://learn.microsoft.com/en-us/defender-xdr/media/edit-delete-rbac-roles/m365-defender-rbac-edit-roles.png)](https://learn.microsoft.com/en-us/defender-xdr/media/edit-delete-rbac-roles/m365-defender-rbac-edit-roles.png#lightbox)

Note

After editing an imported role, the changes made in Microsoft Defender unified RBAC will not be reflected back in the individual product RBAC model.

## Delete roles

To delete roles in Microsoft Defender unified RBAC:

1. Select the role or roles you want to delete.
2. Select **Delete roles**.

Warning

If a Microsoft Defender workload that uses the role is active, deleting the role also removes all assigned user permissions.

Note

When an an imported role is deleted, the role isn't deleted from the individual product RBAC model. If needed, you can reimport it to the Microsoft Defender unified RBAC list of roles.

## Export roles

Important

Starting in 2025, Microsoft Defender unified RBAC is the default model for new Defender for Endpoint and Defender for Identity tenants. These tenants can't export roles from the old model. Tenants that had roles assigned or exported before 2025 keep their old roles setup.

The Export feature lets you export the following role data:

- Role name
- Role description
- Permissions in the role
- Assignment name
- Assigned data sources
- Assigned users or user groups

When a role has multiple assignments, each assignment appears as a separate row in the CSV file.

The CSV also includes the Defender unified RBAC activation status for each workload on the tenant.

To export roles in Microsoft Defender unified RBAC, follow these steps:

Note

To export roles, you must be a Security Administrator or higher in Microsoft Entra ID. Or, you must have the **Authorization \(manage\)** permission for all data sources in Microsoft Defender Unified RBAC and at least one workload activated.

For more information, see [Permission prerequisites](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac#permissions-prerequisites).

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) with the required roles or permissions.
2. In the navigation pane, select **Permissions**.
3. Select **Roles** under Microsoft Defender XDR to get to the Permissions and roles page.
4. Select the **Export** button.

   [![Screenshot of the export roles page](https://learn.microsoft.com/en-us/defender-xdr/media/edit-delete-rbac-roles/m365-defender-rbac-export-roles.png)](https://learn.microsoft.com/en-us/defender-xdr/media/edit-delete-rbac-roles/m365-defender-rbac-export-roles.png#lightbox)

A CSV file containing all the roles data is generated and downloaded to the local computer.

## Related content

- [Learn about RBAC permissions](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details)
- [Map existing RBAC roles to Microsoft Defender unified RBAC roles](https://learn.microsoft.com/en-us/defender-xdr/compare-rbac-roles)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
