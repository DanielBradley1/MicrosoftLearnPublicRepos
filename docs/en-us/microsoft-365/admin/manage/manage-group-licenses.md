<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-group-licenses?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-18 -->

# Assign or unassign licenses to a group in the Microsoft 365 admin center

If you have security groups, mail enabled groups, or Microsoft 365 groups, you can assign or unassign licenses for those groups on the **Licenses** page in the Microsoft 365 admin center. We refer to this as *group-based licensing*.

Note

Some Microsoft services aren't available in all locations. Before a license can be assigned to a user, the administrator must specify the user's location setting. For group-based licensing, any users without a specific location inherit the location of the tenant. If you have users in multiple locations, we recommend that you always set the user location as part of your user creation flow. For more information, see [Add users and assign licenses in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide).

## Before you begin

- You must be at least a Groups Administrator, License Administrator, or User Administrator to assign licenses.
- In addition to the steps described in this article, you can also use the Microsoft Graph PowerShell SDK to assign or unassign Microsoft 365 licenses to groups. For more information, see [Set-MgGroupLicense](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.groups/set-mggrouplicense).
- Group-based licensing doesn't currently support nested groups \(groups that contain other groups\). If you assign licenses to a nested group, only users in the first-level group are assigned licenses.
- When you assign or modify licenses for a large group, like 100,000 users, it can affect performance. In certain high load situations, it might take a long time to process license changes for groups or membership changes to groups with existing licenses.

## Limitations of group-based licensing in the Microsoft 365 admin center

- You can assign licenses to a maximum of 20 groups at a time.
- When you select **Reprocess** to resolve issues with group license assignment, the feature attempts to reprocess licenses up to a maximum of 20 users at a time.
- The lists of users who were and who weren't successfully assigned licenses are paginated lists that display 999 users at a time. You must scroll to the bottom of the list to load the next set of users.

## Assign licenses to a group

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) as at least a License Administrator.
2. Go to the **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264) page.
3. On the **Licenses** page, select **Assign licenses**.
4. In the side panel, search for the group that you want to assign licenses to, then select the name from the dropdown list.
5. Select the subscription that the assigned licenses should come from.
6. To assign or remove access to specific items, select **Turn apps and services on or off**.
7. When you're finished, select **Assign licenses**.

## Unassign licenses from a group

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264) page.
2. Select the product that you want to unassign licenses for.
3. On the product details page, find the group in the list.
4. Select the three dots \(more actions\) on the group's row, then select **Unassign**.
5. In the confirmation dialog, select **Unassign**.

## Move users between licensed groups

When you move a user from one licensed group to another, the order of operations matters. If you remove a user from a group before they're added to the new one, the user can experience a brief loss of access to licensed services while group-based licensing finishes processing the new assignment. However, this temporary loss of access is preventable. To move a user between licensed groups without service interruption, use the following steps in this order:

1. **Add** the user to the destination group first.
2. **Confirm** the new license has been applied on the user's **Licenses** page.
3. **Remove** the user from the original group.

   Note

   If you remove the user from the source group first, the user is unlicensed until group-based licensing finishes processing the new group's assignment. Processing time varies based on tenant size and current load, so the temporary loss of access can be longer than expected in large tenants or during high-load periods.

## Manage group-based licensing errors

If you receive any errors during license assignment, you can view them on the product details page.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to the **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264) page.
2. Select the product that you want to view licenses for.
3. Select the **Errors & issues** tab to see a list of users who have license assignment problems.
4. Select a user to inspect what type of error they encountered.

For a full description of each error type, including insufficient licenses, conflicting service plans, missing dependencies, proxy address issues, and usage location problems, along with steps for how to resolve them, see [Identify and resolve license assignment problems for a group](https://learn.microsoft.com/en-us/entra/fundamentals/licensing-groups-resolve-problems).

## Related content

[Assign or unassign licenses for users in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide) \(article\)  
[Buy or remove licenses for a Microsoft business subscription](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide) \(article\)  
[Identify and resolve license assignment problems for a group](https://learn.microsoft.com/en-us/entra/fundamentals/licensing-groups-resolve-problems) \(article\)
