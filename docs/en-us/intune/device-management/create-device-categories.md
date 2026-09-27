<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/create-device-categories -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Categorize devices into groups

Device categories allow you to easily manage and group devices in Microsoft Intune. Create a category, such as *sales* or *accounting*, and Intune will automatically add all devices that fall within that category to the corresponding device group in Intune. To enable categories in your tenant, you must create a category in the Microsoft Intune admin center and set up dynamic Microsoft Entra security groups.

This article describes how to configure and edit device categories.

## Requirements

Device categories are available for these platforms:

- Android
- iOS/iPadOS
- macOS
- Windows

To configure device categories, you must be an [Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

## Before you begin

Decide if it's necessary to show the device category selection prompt to end users when they visit the Company Portal app or website. If you don't want the prompt to be visible, block it in a [customization profile](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-company-portal#device-categories) first, and then create your categories.

If Multi Admin Approval access policies are enabled for device actions, creating new categories, editing existing ones, and deleting device categories might require approval from a second administrator. To learn more, see [Use Access policies to require Multi Admin Approval](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval).

## Step 1: Create device category in Intune

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Manage devices**, and then select **Device categories**.
4. Choose **Create** to add a new category.
5. Enter the name of the new category, such as `HR` and an optional description.
6. Select **Next**.
7. Optionally, assign a scope tag, like `US-NC IT Team` or `JohnGlenn_ITDepartment`, to limit management of the category to specific IT groups. For more information about scope tags, see [Use RBAC and scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).
8. Select **Next**.
9. Select **Create**. The new category is added to your **Device categories** list.

You'll use the device category name when you create Microsoft Entra security groups in the next step.

## Step 2: Create Microsoft Entra security groups

To enable automatic grouping, you must create a dynamic group using attribute-based rules in Microsoft Entra ID. For instructions, see [Using attributes to create advanced rules](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) in the Microsoft Entra documentation. Create an advanced rule for your group using the **deviceCategory** attribute and the category name you created in Step 1 of this article.

For example, to create a rule that automatically groups devices belonging in the HR category, use the following rule syntax: `device.deviceCategory -eq "HR"`

Tip

If you only use device category groups for Intune policy and app targeting, you can use [assignment filters](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview) with the `deviceCategory` property instead of creating dynamic groups. Filters evaluate at check-in without depending on group membership processing. Dynamic groups remain necessary if the category groups are also used for Conditional Access, licensing, or other cross-workload scenarios.

## View categories of all devices

To view the device category assigned to each device, go to **Devices** > **All devices**. The category is listed in the **Device category** column. To add the column to your table, select **Columns**, and then choose **Category** > **Apply**.

When you delete a category, devices assigned to it appear as **Unassigned**.

## Change the category of a device

If you edit a category, be sure to update any Microsoft Entra security groups that reference the category in their rules.

1. Go to **Devices** > **All devices**.
2. Select a device.
3. Select **Properties**.
4. Change the category listed under **Device category**.
5. Select **Save**.

## Best practices

Device categories are supported on devices running Android, iOS/iPadOS, macOS, and Windows. People with Windows devices must use the Company Portal website to select their category. The category prompt appears for all other platforms when the user signs in to the Company Portal app. Regardless of platform, any device user can sign in to portal.manage.microsoft.com at anytime and go to **My devices** to select a category.

If an iOS/iPadOS or Android device is already enrolled before you configure categories, the user will receive a notification about the device the user owns on the Company Portal website. The notification informs them that they need to select a category the next time they're in the Company Portal app.
