<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-urbac -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Manage unified role-based access control in multitenant management

Use the Microsoft Defender multitenant management portal to manage unified role-based access control \(URBAC\) across multiple tenants. You can view permissions and access for all your tenants in one place. You can also manage these permissions from a central location. The following sections explain how to view custom roles, create or edit roles, delete roles, and import roles from tenant workloads.

## View custom roles

In the multitenant portal, navigate to the **Permissions & roles page** by selecting **System > Permissions**.

![Screenshot of main Permissions and roles page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-main.png)

From the **Permissions & roles** page, you can create or edit a custom role. You can also import and delete roles. Use the **Search** function to find a specific role. To narrow results, filter roles by data source, permissions category, assignee type, or tenant name.

## Create or edit a custom role \(Preview\)

You can create a custom role to provide flexibility and control over access to specific data. To create a custom role, follow these steps:

1. Sign in to multitenant management in Microsoft Defender, then navigate to **System > Permissions**.
2. Select **Create custom role**.

   ![Screenshot highlighting the create role option](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-create-role.png)
3. In the dropdown menu, select the tenant for which you want to create a new role. Select **Continue**.

   ![Screenshot of the tenant dropdown menu](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-create-dropdown.png)
4. In the **Basics** page, enter the name and description of the role. Select **Next**.

   ![Screenshot of the Basics page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-create-basics.png)
5. In the **Permissions** page, select the appropriate permissions for the role.
6. A new pane opens based on the permissions you selected. Select the appropriate permissions for the role, then select **Apply**. Here's an example.

   ![Screenshot of assigning permissions pane](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-create-permissions.png)
7. Select **Next** to proceed to the next page.
8. In the **Assignments** page, select **Add assignment** or **Create assignment** to assign users and data sources.
9. In the **Add assignments** pane, enter the assignment name. Add the team members you want to assign. Select the data sources they can access and the identity scopes they need, then select **Add**.

   The following screenshot shows an example of the **Add assignments** pane:

   ![Screenshot of the options in the Add Assignments pane](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-create-assignment.png)
10. Select **Next**. Review the details you provided in the **Review and finish** page. You can edit the custom role’s name and description, permissions, and assignments in this page.
11. Select **Submit** to finish creating the custom role.

To edit an existing role, select the three dots beside the role name in the Permissions and roles list, then select **Edit**.

![Screenshot of the Edit option in the Permissions page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-edit-role.png)

## Delete roles \(Preview\)

Warning

Deleting a role is permanent and removes all access assignments for that role. Review the selected roles carefully before you continue.

To delete roles, select one or more roles from the list. You can choose roles from different tenants, then select **Delete roles**.

![Screenshot highlighting multiple role selection for deletion](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-delete-multiple.png)

To delete a single role, select the three dots next to the role name, then select **Delete**.

![Screenshot of the Delete option in the Permissions page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-delete-option.png)

The **Delete role** option is also available when editing a specific role.

![Screenshot highlighting the Delete option in the Edit role pane](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-delete-edit-pane.png)

## Import roles \(Preview\)

You can import existing roles from a tenant’s workloads to migrate permissions and assignments. Imported roles become available in the Permissions and roles list.

To import roles, follow these steps:

1. Navigate to **System > Permissions**.
2. Select **Import roles**.
3. In the **Import roles** pane, select the tenant from which you want to import roles in the dropdown menu. Select **Continue**.
4. In the **Workloads** page, select the workloads you want to import from. Select **Next**.

   ![Screenshot of the Workloads page in the Import role scenario](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-import-workload.png)
5. In the **Roles** page, select all or some of the roles that you want to import from the Eligible roles list. To review the permissions and assignments for a role, select the role name. The following screenshot shows an example of the role review pane.

   ![Screenshot of the role review pane in the Import role scenario](https://learn.microsoft.com/en-us/defender-xdr/media/mto-urbac/urbac-import-review-role.png)
6. Review the details then select **Submit** to finish importing the roles.

To learn more about unified RBAC, see [Microsoft Defender unified role-based access control](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## Related content

- [Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-overview)
- [Set up Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-requirements)
