<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/quickstart-custom-role -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Step 10 - Create and assign a custom RBAC role in Microsoft Intune

This article guides you through creating a custom Intune RBAC role with specific permissions for a security operations department and assigning the role to a group of operators. Custom roles help you implement least privilege access, ensuring admins can only manage the users and devices they're empowered to handle.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

Intune includes several built-in RBAC roles that you can use. Microsoft recommends using the least-privileged role that can complete the task an administrator is expected to manage, which might be a custom role. This approach minimizes security risks and operational errors by avoiding over-privileged accounts for routine work.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Role Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#intune-role-administrator)** Microsoft Intune role

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To complete this step, you must:
> 
> - [Create a user](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group).

To complete this evaluation step, you must have a group with at least one user.

## Create a custom role

When you create a custom role, you can set permissions for a wide range of actions. For the security operations role, enable *Read* permissions for a few categories so that the operator can review a device's configurations and policies.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant administrator** > **Roles**. Select **Create**. From the drop-down box, select **Intune role**. The *Add Custom Role* workflow opens.

   [![Screenshot of Microsoft Intune admin center showing Tenant administration, All roles selected, and Create Intune role menu open.](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/add-custom-role.png)](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/add-custom-role.png#lightbox)
2. On the **Basics** page:

   - For **Name**, enter *Security operations*.
   - For **Description**, enter *This role lets a security operator monitor device configuration and compliance information.* Select **Next** to continue.

3. On the **Permissions** page, expand the *Corporate device identifiers* category and set *Read* to **Yes**:

   [![Screenshot of Intune Add Custom Role, Permissions page with Corporate device identifiers expanded and Read set to Yes.](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/corp-device-id-read.png)](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/corp-device-id-read.png#lightbox)

   After configuring *Read* for Corporate device identifiers, expand the following additional categories, and make the same configuration by setting *Read* to **Yes**.

   - *Device compliance policies*
   - *Device configurations*
   - *Organization*


   After the four categories are configured, select **Next** to continue.

4. On **Scope tags**, select **Next**. You don't need to configure scope tags for this evaluation scenario.
5. On **Review + Create**, select *Create*. Intune creates the custom role, which now appears on the **Intune roles \| All roles** page in the Intune admin center, with a **Type** of *Custom Intune role*.

Tip

For a list of permissions by role, see [Role-based access control \(RBAC\) reference](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles).

## Assign the role to a group

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant administration** > **Roles** > **All roles**.
2. On **Intune roles - All roles**, select the custom **Security operations** role you created. In the role's *Overview*, select **Assignments**, and then select **Assign**.

   [![Screenshot of Microsoft Intune Security operations Assignments page with Assign button highlighted.](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/assignment-workflow.png)](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/media/quickstart-custom-role/assignment-workflow.png#lightbox)
3. On **Basics**, enter *Sec Ops* for the name, and then select **Next**.
4. On **Admin Groups**, select **Add groups** and then choose a group that contains the users you want to assign the role's permissions to. If you created the **Contoso Testers** group in [Step 3](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group) of this evaluation guide, select that group.

   After adding a group, choose **Select**, and then **Next** to continue to the next page of the workflow.
5. On **Scope Groups**, select **Add groups** and then add the same group you added in the previous step. As before, choose **Select**, and then **Next** to continue to the next page of the workflow.
6. On **Scope tags**, select **Next**. You don't need to configure scope tags for this evaluation scenario.
7. On **Review + Create**, select **Create** when you're done.

   The new assignment is displayed in the list of assignments.

Now, everyone in the group is a member of the *Security operations* role and can review the following information about a device: corporate device identifiers, device compliance policies, device configurations, and organization information.

## Clean up resources

If you no longer want to use the custom role, you can delete it. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Tenant administration** > **Roles** > **All roles**. Locate the role, select the ellipses \(...\) to the left of the role description, and then select **Delete**.

## Next steps

In this evaluation step, you created a custom security operations role and assigned it to a group. For more information about roles in Intune, see [Role-based administration control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

To continue evaluating Microsoft Intune, go to the next step:

[Step 11 - Create an email device profile for iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/quickstart-email-profile)
