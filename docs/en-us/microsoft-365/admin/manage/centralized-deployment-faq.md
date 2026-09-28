<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/centralized-deployment-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Centralized deployment FAQ

Centralized deployment is a way for a Microsoft 365 admin to deploy Office Add-ins \(Word, Excel, PowerPoint, and Outlook\) to users and groups within an organization, provided the organization meets all requirements for using centralized deployment as outlined in this article. However, note that the [integrated apps portal](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps?view=o365-worldwide) is the recommended and most feature-rich way for most customers to centrally deploy Office add-ins to users and groups within your organization. But add-ins can also be centrally deployed through the **Add-in** page of the Microsoft 365 admin center.

## How do I know if my organization is set up for centralized deployment?

Centralized deployment of add-ins requires that users are using apps in Microsoft 365 for enterprise \(and are signed into Microsoft 365 using their organizational log-in credentials\) and have Exchange Online mailboxes. Your subscription directory must either be in, or federated to, Microsoft Entra ID.

Centralized deployment is only supported for online mailboxes. It doesn't support deployment to on-premises Exchange mailboxes.

You can use the [Centralized Deployment Compatibility Checker](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#centralized-deployment-compatibility-checker) to determine if your subscription is eligible.

## How do you target add-in user assignments with centralized deployment?

Centralized deployment supports assignments to individual users, groups, and everyone in the tenant. Centralized deployment can be used for users in top-level groups \(groups without parent groups\), but not for users in nested groups \(groups that have parent groups\). Centralized deployment also supports most Microsoft Entra groups, including Microsoft 365 Groups, distribution lists, dynamic groups, and security groups.

It's better to use groups assignments instead of individual user assignment for easier management.

For more details, see [User and Group assignments](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#user-and-group-assignments).

## How long does it take for add-ins to show up for all users?

It can take up to 24 hours for a new add-in deployment to show up for all users. It can take up to 72 hours for add-in updates, changes from turn on or turn off to reflect for users.

## How long does it take for add-ins to get removed for all users?

It can take up to 24 hours for add-in removal to reflect for all users.

## As an administrator, how do I manage the user access to add-ins for my organization?

For easy deployment of add-ins to users, groups, or to your entire organization, we recommend administrators use centralized deployment whenever deployment through the integrated apps portal is not suitable.

For more information about managing user access, see:

- [Manage add-in downloads by turning on/off Microsoft Marketplace across all apps \(except Outlook\)](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center#manage-add-in-downloads-by-turning-on-off-microsoft-marketplace-across-all-apps-except-outlook)
- [Specify the administrators and users who can install and manage add-ins for Outlook](https://learn.microsoft.com/en-us/Exchange/specify-who-can-install-and-manage-add-ins-2013-help)

## Will centralized deployment provide admins the flexibility to choose the deployment method for Outlook add-ins?

Yes. Centralized deployment provides admins the flexibility to choose one of three deployment methods for Outlook add-ins during add-in deployment:

**Fixed** The add-in will be automatically deployed to the assigned users and they won't be able to remove it from their ribbon.

**Available** Users can install the add-in in Outlook by choosing **Home > Get More add-ins > Admin-managed**.

**Optional** The add-in is deployed automatically to the assigned users, but they can choose to remove it.

Note

Integrated Apps don't have this option available; however, admins can still use the legacy Add-in page to perform this under **Settings** > **Integrated Apps**, and then selecting the **Add-in** link.  [![Screenshot that shows the Adoption Score page in Reports.](https://learn.microsoft.com/en-us/microsoft-365/media/addin-links.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/addin-links.png?view=o365-worldwide#lightbox)

## Can admins update Line-of-Business \(LOB\) add-ins?

Yes. Admins can upload a new manifest file to support metadata changes for admin-deployed LOB add-ins. The add-in updates the next time the Microsoft 365 app starts. The web application can change at any time.

For more information, see [line-of-business add-in](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center?view=o365-worldwide).

## Can admins turn off add-ins?

Yes. Admins can turn on or off the add-ins they deploy for all users from the Microsoft admin center.

For more information, see [Add-in states](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center?view=o365-worldwide#add-in-states-in-the-microsoft-365-admin-center).

## Can admins delete or remove add-ins?

Yes. Admins can delete add-ins they deployed for all users from the Microsoft admin center.

For more information, see [Delete an add-in](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center?view=o365-worldwide#remove-an-add-in-from-the-microsoft-365-admin-center).

## Can admins deploy paid add-ins from Microsoft Marketplace using centralized deployment?

Yes.

## Which admin role do I need to manage add-ins for my organization?

Global Admin is the recommended role with complete access to the add-in management lifecycle. If you're the person who purchased your Microsoft 365 Business subscription, you're the Global admin.

Your subscription comes with a set of admin roles that you can assign to other users in your organization. Each admin role maps to common business functions and gives people in your organization permissions to perform specific tasks in the Microsoft 365 admin center.

For more information, see [Assign admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/assign-admin-roles?view=o365-worldwide).

## How many add-ins can I deploy?

A total of 200 Excel, Outlook, PowerPoint, and Word add-ins can be deployed by admins within their tenant.

## Why do add-in deployment times for Word, Excel, and PowerPoint differ compared to Outlook add-ins?

There are architectural differences between add-in deployments for Word, Excel, and PowerPoint vs Outlook.
