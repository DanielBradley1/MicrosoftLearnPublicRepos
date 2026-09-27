<!-- Source: https://learn.microsoft.com/en-us/intune/advanced-analytics/device-scopes -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Device scopes

Device scopes use scope tags to filter endpoint analytics reports to a subset of devices, allowing you to see scores, insights, and recommendations for a specific subset of devices.

Device scopes are supported on the following endpoint analytics reports:

- [Startup performance](https://learn.microsoft.com/en-us/intune/endpoint-analytics/startup-performance)
- [Work from anywhere](https://learn.microsoft.com/en-us/intune/endpoint-analytics/work-from-anywhere)
- [Application reliability](https://learn.microsoft.com/en-us/intune/endpoint-analytics/app-reliability)
- [Battery health](https://learn.microsoft.com/en-us/intune/advanced-analytics/battery-health)

## Before you begin

- Confirm that your environment meets all [prerequisites](https://learn.microsoft.com/en-us/intune/advanced-analytics/#prerequisites).

Additional prerequisites for custom device scopes:

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To create custom device scopes, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Read Only Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator)
> - [Intune Role Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#intune-role-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Roles/Read**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)
> 
> Note
> 
> After custom device scopes are created, other users with access to endpoint analytics can use them.  
> Only the user who created the custom device scopes or a Global Administrator can delete the custom device scopes.

## Create and manage custom device scopes

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), open one of the reports within endpoint analytics, for example startup performance. Select **Reports** > **Endpoint analytics** > **Startup performance**.
2. Select **Device scope**.
3. Select **Manage device scopes** to open the flyout where you can create and modify your custom device scopes.

To create custom device scopes:

1. Open the **Manage device scopes**.
2. Select a scope tag from the dropdown and select **Save**.
3. Give the new custom device scope a name and select **OK**.

The new custom device scope appears in your list of saved device scopes. By default, custom devices scopes are in the *Off* state. To activate custom device scopes, toggle the **State** setting to *On*. Data processing starts for the selected device scope.

Note

Once activated, custom device scopes can take up to 24 hours to process. During this period, custom device scopes that are still processing are not usable. Additionally, custom device scopes require 10 devices at minimum to populate supported reports. Otherwise **Insufficient Data** might show when trying to select a custom scope.

To delete custom device scopes:

1. Open the **Manage device scopes** menu.
2. Find the custom device scope you would like to delete and select the menu.
3. Select **Delete**.
4. Select **Yes** to confirm.

Important

If a custom device scope is associated with a Scope tag that gets deleted from your tenant, the custom device scope will no longer function. You see an error message in the **Manage device scopes** menu. Edit the impacted device scope to use a valid Scope tag or delete it to clear the error.

## Use custom device scopes

Custom device scopes can be used in any supported endpoint analytics report. To use a custom device scope:

1. Ensure that the device scope you would like to use is active.
2. Navigate to a supported report in endpoint analytics, such as **Startup performance**.
3. Select **Device scope** menu in the page.
4. From the dropdown menu, select your desired custom device scope.
5. Select **Apply**.

The page is automatically updated to show scores, data, and insights specific to the subset of devices defined by your chosen custom device scope. As you navigate through endpoint analytics, your chosen device scope remains selected on all supported reports and pages.

To return to viewing all devices, navigate to the **Device scope** menu, select **All Devices** from the dropdown menu, and select **Apply**.

## Limitations

- You can save up to 100 custom device scopes, and up to 20 can be active at a time.
- Only one Scope tag can be used to create a custom device scope. To create a custom device scope that includes devices from multiple Scope tags, you must create a new Scope tag and assign it to the full set of devices that you require.
