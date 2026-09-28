<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-18 -->

# Create, edit, or delete a security group in the Microsoft 365 admin center

On the Microsoft 365 **Active teams and groups** page, you can create groups of user accounts that you can use to assign the same permissions to in SharePoint Online and CRM Online. For example, an administrator can create a security group to grant a certain group of people access to a SharePoint site.

## Before you begin

User management administrators have permissions to create, edit, or delete security groups; for more information about administrator roles, see [Assigning admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/assign-admin-roles?view=o365-worldwide).

There are also [Groups in Exchange Online and SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) that you can use to send email or assign permissions to a group of users, and [Groups in Exchange Online and SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) that grant users rights and access to sites and site collections.

## Manage security groups in the admin center

### Add a security group

1. In the Microsoft 365 admin center, go to **Teams & groups** > [Active teams and groups](https://go.microsoft.com/fwlink/p/?linkid=2052855) page.
2. Go to the **Security groups** page, and select **Add a security group**.
3. On the **Set up the basics** page, add your group name and a description and choose **Next**.
4. On the **Edit settings** page, select whether you want to allow Microsoft Entra roles to be assigned to the group and select **Next**.
5. Review your selections and choose **Create group** and **Close**.

### Add owners or members to a security group

1. Select the security group name on the [Active teams and groups](https://go.microsoft.com/fwlink/p/?linkid=2052855) page.
2. On the **General** tab, select **Add owners** to add group owners.
3. On the **Members** tab, select **View all and manage members** and choose the person from the list or use the **Search** box. Select **Add** and close.

### Remove members from a security group

1. Select the security group name on the [Active teams and groups](https://go.microsoft.com/fwlink/p/?linkid=2052855) page, and on the **Members** tab, select **View all and manage members**.
2. To remove members, select the user, choose the ellipsis and choose **Remove members**.

### Edit a security group

1. Select the security group name on the [Active teams and groups](https://go.microsoft.com/fwlink/p/?linkid=2052855) page, and on the **Members** tab, select **View all and manage members**.
2. Select the group's name and make your changes.

### Delete a security group

1. In the Microsoft 365 admin center, go to **Teams & groups** > [Active teams and groups](https://go.microsoft.com/fwlink/p/?linkid=2052855) page.
2. Select the security group and on the **General** tab, select **Delete group** and then confirm by selecting **Delete group**. Then **Close** once the group is deleted.

## Groups in Exchange Online and SharePoint Online

If you want to create groups of users so you can send email to them all at the same time, you can do that in the Exchange admin center by going to **Admin** > **Exchange** > **Recipients** > [**Groups**](https://go.microsoft.com/fwlink/?linkid=2183233). Next, select **Add a group**. Then, choose the type of group you want to create. For more information, see [Compare types of groups in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/compare-groups).

After you create distribution groups and mail-enabled security groups in the [Exchange admin center](https://go.microsoft.com/fwlink/p/?linkid=2059104), their names and user lists appear on the **Security groups** page. You can delete these groups in both locations, but you can edit them only in the Exchange admin center. Dynamic distribution groups don't show up on the **Security groups** page.

SharePoint groups are created automatically when you make a site collection. The default groups use the default permission levels in SharePoint-sometimes called SharePoint roles-to grant users rights and access. For more information, see [Default SharePoint groups in SharePoint Online](https://learn.microsoft.com/en-us/sharepoint/default-sharepoint-groups).

## Frequently asked questions about groups

### How is a security group different from security groups I create in SharePoint?

Security groups can be used with SharePoint, Exchange, Windows, and more. A security group you create in SharePoint is only recognized by that SharePoint site collection.

### Do I have to use security groups for my organization to be secure?

No. This is just one more way you can manage security for your organization. You can always grant user permissions and access to sites individually. But with security groups, you can easily manage larger groups of users.

### Can I send email to a security group?

Yes. But if you want to use groups for email and collaboration, we recommend that you [create a Microsoft 365 group](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/create-groups?view=o365-worldwide) instead.

## Related content

[Create a group in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/create-groups?view=o365-worldwide) \(article\)  
[Explaining Microsoft 365 Groups to your users](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/explain-groups-knowledge-worker?view=o365-worldwide) \(article\)  
[Manage a group in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/manage-groups?view=o365-worldwide) \(article\)
