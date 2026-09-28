<!-- Source: https://learn.microsoft.com/en-us/entra/fundamentals/users-restore -->
<!-- Sitemap-Last-Modified: 2026-06-18 -->

# Restore or remove a recently deleted user

## Overview

After you delete a user, the account remains in a suspended state for 30 days. During that 30-day window, the user account can be restored, along with all its properties.

After that 30-day window passes, the permanent deletion process automatically starts and can't be stopped. During this time, the management of soft-deleted users is blocked. This limitation also applies to restoring a soft-deleted user via a match during tenant sync cycle for on-premises hybrid scenarios.

You can view your restorable users, restore a deleted user, or permanently delete a user using the Microsoft Entra admin center.

Important

You can delete users synced from your on-premises environment in Microsoft Entra ID for security purposes. However, Microsoft Entra ID isn't the source of authority for synced users. If the user still exists in your on-premises directory, the sync engine may restore the user during the next synchronization cycle. After a user is permanently deleted, neither you nor Microsoft Support can restore them.

## Prerequisites

You must have at least the following role to restore and permanently delete users.

## View your restorable users

You can see all the users that were deleted less than 30 days ago. These users can be restored.

### To view your restorable users

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**, and then select **Deleted users**.

   If you don't see **Deleted users**, use the Microsoft Entra admin center search box to search for and select **Deleted users**.
3. Review the list of users that are available to restore.

   [![Screenshot of the Users - Deleted users page, with users that can still be restored.](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-view-restorable.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-view-restorable.png#lightbox)

## Restore a recently deleted user

When a user account is deleted from the organization, the account is in a suspended state. All of the account's organization information is preserved. When you restore a user, this organization information is also restored.

Note

Once a user is restored, licenses that were assigned to the user at the time of deletion are also restored even if there are none available. If you're consuming more licenses than you purchased, your organization could be temporarily out of compliance for license usage.

### To restore a user

1. On the **Deleted users** page, search for and select one of the available users. For example, *Mary Parker*.
2. Select **Restore user**.

   [![Screenshot of the Users - Deleted users page, with Restore user option highlighted.](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-restore-user.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-restore-user.png#lightbox)

## Permanently delete a user

You can permanently delete a user from your organization without waiting the 30 days for automatic deletion. A permanently deleted user can't be restored by anyone, including Microsoft customer support.

Note

If you permanently delete a user by mistake, you have to create a new user and manually enter all the previous information. For more information about creating a new user, see [Add or delete users](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users).

### To permanently delete a user

1. On the **Deleted users** page, search for and select one of the available users. For example, *Rae Huff*.
2. Select **Delete permanently**.

   [![Screenshot of the Users - Deleted users page, with Delete user option highlighted.](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-permanent-delete-user.png)](https://learn.microsoft.com/en-us/entra/fundamentals/media/users-restore/users-deleted-users-permanent-delete-user.png#lightbox)

## Related content

- [Add or delete users](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users)
- [Assign roles to users](https://learn.microsoft.com/en-us/entra/fundamentals/how-subscriptions-associated-directory)
- [Add or change profile information](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-user-profile-info)
