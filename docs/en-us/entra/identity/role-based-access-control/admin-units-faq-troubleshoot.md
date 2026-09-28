<!-- Source: https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-faq-troubleshoot -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Microsoft Entra administrative units: Troubleshooting and FAQ

For more granular administrative control in Microsoft Entra ID, you can assign users to a Microsoft Entra role with a scope that is limited to one or more administrative units. For sample PowerShell scripts for common tasks, see [Work with administrative units](https://learn.microsoft.com/en-us/powershell/azure/active-directory/working-with-administrative-units).

## General

### Why am I unable to create an administrative unit?

You must be assigned at least the [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) role to create an administrative unit in Microsoft Entra ID. Check to ensure that the user who's trying to create the administrative unit is assigned the *Privileged Role Administrator* role.

### I added a group to an administrative unit. Why are the group members still not showing up there?

When you add a group to an administrative unit, that doesn't result in all the group's members being added to it. Users must be directly assigned to the administrative unit.

### I just added \(or removed\) a member of the administrative unit. Why is the member not showing up \(or still showing up\) on the user interface?

Sometimes, the addition or removal of one or more members of an administrative unit might take a few minutes to be reflected on the **Administrative units** pane. Alternatively, you can go directly to the associated resource's properties and see whether the action has been completed. For more information about members in administrative units, see [List users, groups, or devices in an administrative unit](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-members-list).

### I am a delegated Password Administrator on an administrative unit. Why am I unable to reset a specific user's password?

As an administrator of an administrative unit, you can reset passwords only for users who are assigned to your administrative unit. Make sure that the user whose password reset is failing belongs to the administrative unit to which you've been assigned. If the user belongs to the same administrative unit but you still can't reset the user's password, check the roles that are assigned to the user.

To prevent an elevation of privilege, an administrative unit-scoped administrator can't reset the password of a user who's assigned to a role with an organization-wide scope.

### Why are administrative units necessary? Couldn't we have used security groups as the way to define a scope?

Security groups have an existing purpose and authorization model. A *User Administrator*, for example, can manage membership of all security groups in the Microsoft Entra organization. The role might use groups to manage access to applications such as Salesforce. A *User Administrator* shouldn't be able to manage the delegation model itself, which would be the result if security groups were extended to support "resource grouping" scenarios.

Administrative units, such as organizational units in Windows Server Active Directory, are intended to provide a way to scope administration of a wide range of directory objects. Security groups themselves can be members of resource scopes. Using security groups to define the set of security groups that an administrator can manage could become confusing.

### What does it mean to add a group to an administrative unit?

Adding a group to an administrative unit brings the group itself into the management scope of the administrative unit, but **not** the members of the group. For more information, see [Administrative units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units#groups).

### Can a resource \(user, group, or device\) be a member of more than one administrative unit?

Yes, a resource can be a member of more than one administrative unit. The resource can be managed by all organization-wide and administrative unit-scoped administrators who have permissions over the resource.

### Are administrative units available in B2C organizations?

No, administrative units aren't available for B2C organizations.

### Are nested administrative units supported?

No, nested administrative units aren't supported.

### Are administrative units supported in PowerShell and the Microsoft Graph API?

Yes. You'll find support for administrative units in [PowerShell cmdlet documentation](https://learn.microsoft.com/en-us/powershell/module/azuread/) and [sample scripts](https://learn.microsoft.com/en-us/powershell/azure/active-directory/working-with-administrative-units).

Find support for the [administrativeUnit resource type](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit) in Microsoft Graph.

## Dynamic administrative units

### I just saved a rule for dynamic membership groups for an administrative unit, but I don't see any users populated yet.

The initial update of an administrative unit can take a few minutes depending on your tenant size and the current Microsoft Entra ID load.

### After creating a rule for dynamic membership groups in the Microsoft Entra admin center using the rule builder and attempting to save, I get the error "Failed to update administrative unit properties".

This usually means there's a problem with the supplied property values. Confirm that the property values you have supplied have a proper value type \(Boolean, string, or string collection\). For more information, see the allowed values for each operator for [users](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership#supported-properties) or [devices](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership#rules-for-devices).

This error can also result if a person without a Microsoft Entra ID P1 license attempts to save an update to the administrative unit.

### How can I add a single member to an administrative unit in addition to the current rule for dynamic membership groups?

To add a single user, add an appropriate expression with the `OR` query operator to the rule for dynamic membership groups.

### I am a Privileged Role Administrator, but I can't add or remove members for an administrative unit.

When an administrative unit has been configured for dynamic membership groups, you must edit the rules for dynamic membership groups to change membership.

### How many administrative units with rules for dynamic membership groups can I create in a tenant?

The total number of dynamic membership groups and dynamic administrative units combined cannot exceed 15,000.

### Is there a limit to the number of characters in a rule for dynamic membership groups?

Yes. 3,072 characters.

### Can I create administrative units with rules for dynamic membership groups in the Microsoft 365 admin center?

No.

## Restricted management administrative units

### I am the owner of a group that is a member of a restricted management administrative unit. How are my permissions affected?

As an owner of a protected group, you won't be able to manage it just based on ownership. Managing protected resources currently require a role to be assigned at the restricted management administrative unit scope of the protected resource.

### How are my Microsoft 365 resources affected by using restricted management administrative units?

Currently, securing Microsoft Entra resources in restricted management administrative units is supported. Resources managed outside of Microsoft Entra ID aren't supported.

### I'm unable to modify a member of a restricted management administrative unit.

The user, group, or device is a member of restricted management administrative unit. Management rights are limited to administrators scoped to that administrative unit.

## Next steps

- [Restrict scope for roles by using administrative units](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)
- [Create or delete administrative units](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-manage)
