<!-- Source: https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/delete-recover-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Deletion and recovery of applications FAQ

The following are some frequently asked questions \(FAQs\) on deletion and recovery of applications.

## When I create applications, and get a Directory\_QuotaExceeded error, how can I avoid this problem?

> A nonadmin user can create no more than 250 Microsoft Entra resources that include applications and service principals. Both active resources and deleted resources that are available to restore count toward this quota. Even if you delete more applications that you don't need, they still add count to the quota. To free up the quota, you need to [permanently delete](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application) objects in the deleted items container.
> 
> For more information about the service limits, see [Azure resource management](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits?msclkid=6cb6cc54c68711ec93eb9539fce3cc28#azure-active-directory-limits).

## Where can I find all the deleted applications and service principals?

> Soft-deleted application and service principal objects go into the deleted items container and remain available to restore for up to 30 days. After 30 days, they're permanently deleted, thus freeing up the quota.
> 
> To learn how to view deleted application objects through the Microsoft Entra admin center, see [View restorable applications](https://learn.microsoft.com/en-us/entra/identity-platform/howto-restore-app#view-your-deleted-applications).
> 
> Deleted service principals can't be viewed through the Microsoft Entra admin center. To learn how to view your restorable service principals using PowerShell or Microsoft Graph API, see [View restorable service principals](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application).

## How do I restore deleted applications or service principals?

> To learn how to restore recently deleted application registrations through the Microsoft Entra admin center, see [Restore application registrations](https://learn.microsoft.com/en-us/entra/identity-platform/howto-restore-app). If the application registration and its corresponding service principal got deleted, the service principal is also restored.
> 
> To learn how to restore recently deleted service principals, see [Restore service principals](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application). This method is also applicable for restoring recently deleted application registrations using PowerShell or Microsoft Graph API.

## How do I permanently delete soft deleted applications or service principals?

> To permanently delete application registrations through the Microsoft Entra admin center, see [Permanently delete an application](https://learn.microsoft.com/en-us/entra/identity-platform/howto-restore-app#permanently-delete-an-application).
> 
> To permanently delete a service principal, see [Permanently delete a service principal](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application). This method is also applicable for permanently deleting application registrations using PowerShell or Microsoft Graph API.

## Can I configure the interval in which applications and service principals are permanently deleted by Microsoft Entra ID?

> No. You can't configure the periodicity of hard deletion.

## Are managed identities soft-deleted?

> Yes, Managed identities are soft-deleted. You can view the soft-deleted managed identity service principal from the recycle bin within 30 days after deletion, but you can't restore or permanently delete it. The managed identity service principal is permanently deleted after 30 days. For more information on how to view soft-deleted managed identities service principals, see [View deleted service principals](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application).

## I can't see the provisioning data from a recovered service principal. How can I recover it?

> After recovering a service principal, you may initially see the error in the following screenshot. This issue resolves itself between 40 mins and 1 day. If you'd like the provisioning job to start immediately, you can hit restart to force the provisioning service to run again. Hitting restart triggers an initial cycle that can take time for customers with 100 K+ users or group memberships.
> 
> ![Screenshot of recovering user provisioning data.](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/media/delete-application-portal/recover-user-provisioning.png)

## I recovered my application that was configured for application proxy. I can't see app proxy configurations after the recovery. How can I recover it back?

> App proxy configurations can't be recovered through the portal UI. Use the API to recover app proxy settings. Expect a delay of up to 24 hours as the app proxy data gets synced back.

## I can't see the policies I set on the service principal object after the recovery. How can I recover them?

> Policies can't be recovered currently. When you restore a service principal, you have to configure the policies again.

## Next steps

- [Restore a service principal](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/restore-application)
- [Restore an application registration](https://learn.microsoft.com/en-us/entra/identity-platform/howto-restore-app)
