<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/use-dynamic-groups -->
<!-- Sitemap-Last-Modified: 2025-06-06 -->

# Create and manage dynamic membership groups for B2B collaboration in Microsoft Entra External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

## What are dynamic membership groups?

A dynamic membership group is a security-based configuration for Microsoft Entra available in the [Microsoft Entra admin center](https://entra.microsoft.com). Administrators can set rules to populate dynamic membership groups that are created in Microsoft Entra ID based on user attributes \(such as [userType](https://learn.microsoft.com/en-us/entra/external-id/user-properties), department, or country/region\). Members can be automatically added to or removed from a security group based on their attributes. These groups can provide access to applications or cloud resources \(SharePoint sites, documents\) and to assign licenses to members. Learn more about [dedicated groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-groups).

## Prerequisites

[Microsoft Entra ID P1 or P2 licensing](https://www.microsoft.com/security/business/identity-access-management/azure-ad-pricing) is required to create and use dynamic membership groups. Learn more in [Create attribute-based rules for dynamic membership groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership).

## Creating an "all users" dynamic group

You can create a group containing all users within a tenant using a membership rule. When users are added or removed from the tenant in the future, the group's membership is adjusted automatically.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Groups** > **All groups**, and then select **New group**.
3. On the **New Group** page, under **Group type**, select **Security**. Enter a **Group name** and **Group description** for the new group.
4. Under **Membership type**, select **Dynamic User**, and then select **Add dynamic query**.
5. Above the **Rule syntax** text box, select **Edit**. On the **Edit rule syntax** page, type the following expression in the text box:

   ```
   user.objectId -ne null
   ```

6. Select **OK**. The rule appears in the Rule syntax box:

   [![Screenshot of rule syntax for all users dynamic group.](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-user-rule-syntax.png)](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-user-rule-syntax.png#lightbox)
7. Select **Save**. The new dynamic group will now include B2B guest users and member users.
8. Select **Create** on the **New group** page to create the group.

## Creating a group of members only

If you want your group to exclude guest users and include only members of your tenant, create a dynamic group as described above, but in the **Rule syntax** box, enter the following expression:

```
(user.objectId -ne null) and (user.userType -eq "Member")
```

The following image shows the rule syntax for a dynamic group modified to include members only and exclude guests.

[![Screenshot of rule syntax where user type equals member.](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-member-user-rule-syntax.png)](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-member-user-rule-syntax.png#lightbox)

## Creating a group of guests only

You might also find it useful to create a new dynamic group that contains only guest users, so that you can apply policies \(such as Microsoft Entra Conditional Access policies\) to them. Create a dynamic group as described above, but in the **Rule syntax** box, enter the following expression:

```
(user.objectId -ne null) and (user.userType -eq "Guest")
```

The following image shows the rule syntax for a dynamic group modified to include guests only and exclude member users.

[![Screenshot of rule syntax where user type equals guest.](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-guest-user-rule-syntax.png)](https://learn.microsoft.com/en-us/entra/external-id/media/use-dynamic-groups/all-guest-user-rule-syntax.png#lightbox)

## Next steps

- [B2B collaboration user properties](https://learn.microsoft.com/en-us/entra/external-id/user-properties)
- [Reset redemptions status](https://learn.microsoft.com/en-us/entra/external-id/reset-redemption-status)
- [Conditional Access for B2B collaboration users](https://learn.microsoft.com/en-us/entra/external-id/authentication-conditional-access)
