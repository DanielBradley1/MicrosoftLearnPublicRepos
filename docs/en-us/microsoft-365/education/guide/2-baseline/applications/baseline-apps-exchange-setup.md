<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-setup -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 2: Set up Microsoft Exchange Online in an education environment

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

This article is relevant to administrators of Exchange Online and describes the setup procedures for educational environments and describes areas of special interest in educational environments.

## Role-based access control

Identify the Exchange Online administrators and assign them to the appropriate built-in roles supporting [role-based access control](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo) \(RBAC\). Microsoft recommends that a delegated administrative model is implemented in education environments; this allows for administration to be defined at the level of district, school, and classroom, for example, if necessary. We also recommend that there be separation between students and faculty / staff / administration. Use the built-in roles and role groups when possible.

1. The **Organization Management role group** provides complete access to entire Exchange Online organization, with just a few exceptions. This is the most powerful role in Exchange Online, so the number of members should be limited. This group is a tenant-wide role group that transcends delegation.
2. At the delegated container level, assign the **Recipient Management role group** to administrators who manage mailboxes. This includes the ability to create and modify recipients.
3. Members of the **Help Desk role group** can reset passwords and manage the configuration for individual recipients. Members can only manage the configuration that the user can manage themselves.

## User mailbox lifecycle

The user mailbox lifecycle consists of the following stages:

1. Mailbox creation: The mailbox creation process occurs automatically when a user is assigned an A1, A3, or A5 license. No manual intervention is required. Ensure the Microsoft Entra ID has a usage location assigned.
2. Email address standards / default format: By default, the email address is derived from the user’s user principal name.
3. Mailbox plans / templates: A mailbox plan is a template that automatically configures mailbox properties. Mailbox plans are optional and should be implemented when default settings need to be changed.
4. Mailbox Management
5. Add / remove addresses
6. Recover deleted messages
7. Retention
8. Mailbox deletion: Mailbox deletion occurs when the user’s sign-in ID is deleted, or when the Exchange Online license is removed. No manual intervention is required. The mailbox can be recovered within 30 days. The mailbox is considered soft-deleted.
9. Soft delete: Soft deleted mailboxes are mailboxes that can be recovered. The soft deleted can be restored \(converted to a shared mailbox\) to another user, for example a supervisor.
10. Hard delete: After 30 days, the mailbox is hard deleted and can't be recovered.
11. Mailbox recovery: If the mailbox was deleted because the user ID was deleted, restoring the user ID restores the mailbox. If the mailbox was deleted because the license was removed, restoring the license automatically brings the mailbox back. The soft deleted mailbox can also be restore to some other user via PowerShell \(new-mailboxrestorerequest\).

## Resource mailboxes

A resource mailbox is a mailbox assigned to a resource as opposed to a user. Resource mailboxes are either room mailboxes, or equipment mailboxes for portable items such as projectors, computers, and other shared devices. Users can reserve these resources.

Room mailboxes should be sorted into lists using Room Lists, grouped by location.

## Distribution groups

The following guidance is for managing distribution groups, also called distribution lists.

1. Separate distribution groups at the district / school / class level.
2. Separate distribution groups for staff / faculty / student.
3. Dynamic distribution groups: Dynamic distribution groups are an effective way to automatically create a distribution lists based on users’ attributes \(for example: school, district, class, student, faculty, and / or administration\). Custom attributes should be populated accordingly to support this model. The logical **AND** operator can be used to filter across multiple attributes. We recommend using dynamic distribution groups since the alternative - manually administering these groups - is impractical at scale.

Distribution groups can be named via a Naming Policy allowing for consistency and easy sorting.

## Next steps

Now that you completed the Exchange Online setup section, you're ready for the Exchange Online privacy/compliance section.

[Next: Exchange Compliance>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-compliance)
