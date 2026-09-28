<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/user-identities -->
<!-- Sitemap-Last-Modified: 2026-02-10 -->

# Academic year transition - user identities

Management of user provisioning and deprovisioning with adjustments to Microsoft Entra ID and on-premises or third-party identity solutions for the closing and new school year.

[![Picture showing timeline of academic year transition for user identities. Three weeks before end of school, identify which accounts should be removed or blocked and identify actions needed for graduating student accounts. After school year ends, remove/block inactive accounts, remove graduating student accounts or change graduating student to Alumni accounts. After school year ends, reset or change passwords, review group policy, review Conditional Access policy.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/identity-academic-year-transition.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/identity-academic-year-transition.png#lightbox)

## Microsoft Entra cleanup

After the school year has ended, Microsoft recommends cleaning up inactive and graduating accounts in order to prepare for the new school year, keeping in mind your specific user data retention requirements. Performing a [cleanup of inactive accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts) typically involves the following steps:

1. [Decide on detailed information requirements](#deciding-on-detailed-information-requirements)
2. [Identify the accounts to be removed.](#identifying-accounts-to-be-cleaned-up)
3. [Review and manage list of potential accounts.](#reviewing-list-of-collected-accounts)
4. [Remove accounts](#removing-accounts)
5. [Validate](#validate)

For information on data lifecycle management, see [Retention Capabilities](#retention-capabilities).

### Deciding on detailed information requirements

Several decisions need to be made to identify what defines an inactive account and which accounts need to be cleaned up in Microsoft Entra ID. Use guidelines from previous years to base your decisions. For example:

- What defines an inactive account? \(for example, a user hasn't logged in during the past 18 months\)
- How do we handle graduating student accounts?
- What organizational retention guidelines do we need to follow?

#### Graduating student accounts

Graduating students in higher education are eligible for an alumni SKU that allows them to continue to have an Exchange Online Mailbox post graduation. Organizations typically process the accounts in one of two ways:

- [Change the existing user account](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-groups-change-licenses) in Office 365 from the old SKU to the alumni SKU
- Remove or disable the old user account and then create a new user account in a tenant that is designated for alumni users. This method has three main benefits:

  - It logically separates alumni members from the existing school communications.
  - It creates a logical barrier for interactions and visibility of active students.
  - It frees up storage. All the content associated with the accounts from when they were active students can be removed from the tenant. Then, the content no longer counts against the tenant's storage quota. To free up the storage, you can delete and recreate \(or delete\) the OneDrive.

Note

When a user account is moved to the alumni SKU, the associated OneDrive is not cleaned up and continues to count against pooled storage. To learn more, see [Clean up unlicensed OneDrive accounts.](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/pooled-storage-management#clean-up-unlicensed-onedrive-accounts)

### Identifying accounts to be cleaned up

[Inactive accounts](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts) are user accounts that aren't required anymore by members of your organization to gain access to your resources. One key identifier for inactive accounts is that they haven't been used **for a while** to sign-in to your environment. Because inactive accounts are tied to the sign-in activity, you can use the timestamp of the last sign-in that was successful to detect them.

You can detect inactive accounts by evaluating the lastSignInDateTime property that is exposed by the signInActivity resource type of the Microsoft Graph API. Viewing the sign-in activity details through the Graph API requires a Microsoft Entra ID P1 or P2 license. Using this property, you can implement a solution for the following scenarios:

- **Last sign-in date and time for all users:** In this scenario, you need to generate a report of the last sign-in date of all users. You request a list of all users, and the last lastSignInDateTime for each respective user: `https://graph.microsoft.com/v1.0/users?$select=displayName,signInActivity`
- **Users by name:** In this scenario, you search for a specific user by name, which enables you to evaluate the lastSignInDateTime: `https://graph.microsoft.com/beta/users?$filter=startswith(displayName,'markvi')&$select=displayName,signInActivity`
- **Users by date:** In this scenario, you request a list of users with a lastSignInDateTime before a specified date: `https://graph.microsoft.com/beta/users?filter=signInActivity/lastSignInDateTimele2019-06-01T00:00:00Z`

You can view inactive users by accessing the [**Storage usage by inactive users** report](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/pooled-storage-management#view-inactive-users).

For more information, see [How to manage inactive user accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts).

### Reviewing list of collected accounts

Review the list of collected accounts:

- Are all accounts that are listed going to be deleted?
- Do you have on-premises sync to AD via AD Connect?
- Do you have a third-party on-premises connection sync?
- Do you have regulatory or compliance considerations on data in question?
- \(HED\) - Are these accounts considered 'Alumni' accounts?

### Removing accounts

After you have reviewed the list of accounts and are ready to remove them, you have a few options for deleting them:

- [Bulk delete users in the Azure portal](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/users-bulk-delete)
- [Delete a user from your organization from Microsoft 365.](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/delete-a-user)

### Disabling logins or removing other students

Sometimes, instead of deleting accounts, you might need to disable or block access to them. For instance, your organization might have specific policies on retaining historical records or compliance.

When you block access to a Microsoft 365 account, you prevent anyone from using the account to sign in and access the services and data in your Microsoft 365 organization. You can use [PowerShell to block access to individual or multiple user accounts](https://learn.microsoft.com/en-us/microsoft-365/enterprise/block-user-accounts-with-microsoft-365-powershell).

If your users are synchronized with Microsoft Entra ID from a local Active Directory, identify and clean up the users so that they aren't recreated on the next synchronization run from Microsoft Entra Connect. We recommend that you [regularly check for and remove inactive user accounts in Active Directory](https://learn.microsoft.com/en-us/services-hub/unified/health/remediation-steps-ad/regularly-check-for-and-remove-inactive-user-accounts-in-active-directory).

### Validate

After the accounts have been removed, validate the user accounts are removed by checking Microsoft Entra ID, on-premises sync options, and audit reports.

- Validate user accounts are removed
- Confirm on-premises sync options

## Retention Capabilities

Sometimes, you need to retain user data for a specified period, either for archival purposes, or potentially due to organizational or industry regulations. The following documentation contains details on retention within Microsoft 365 using both policies and labels:

- [Get started with data lifecycle management](https://learn.microsoft.com/en-us/microsoft-365/compliance/get-started-with-retention)
- [Learn about retention policies & labels to automatically retain or delete content](https://learn.microsoft.com/en-us/microsoft-365/compliance/retention)
- [Start retention when an event occurs](https://learn.microsoft.com/en-us/microsoft-365/compliance/event-driven-retention)

[Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-overview) provides a cost-effective solution for storing inactive data while ensuring compliance with various regulations. It allows organizations to retain inactive or aging data for long periods, which can be crucial for retrieval later.

### Rollover Review

#### Bulk Password reset or change

As the Microsoft 365 admin, you can let people use the [self-service password reset tool](https://go.microsoft.com/fwlink/p/?LinkId=522677) so you don't have to reset passwords for them. Less work for you!

- [Let users reset their own passwords](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/let-users-reset-passwords)
- [Reset passwords](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/reset-passwords)
- [Force password change for all users in Office 365](https://www.michev.info/Blog/Post/1419/force-password-change-for-all-users-in-office-365)

#### Group expiration policy review

With the increase in usage of Microsoft 365 groups and Microsoft Teams, administrators and users need a way to clean up unused groups and teams. A Microsoft 365 groups expiration policy \(available as a premium feature\) can help remove inactive groups from the system and make things cleaner. An admin can also manually review the activity details from the Microsoft 365 Admin Center Usage Reports to identify sites and mailboxes that haven't been recently active.

When a group expires, the group and its associated services \(the mailbox, Planner, SharePoint site, team, etc.\) are "soft-deleted," which means it can still be recovered for up to 30 days. For more information, see:

- [Overview of Microsoft 365 Groups for administrators](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups)
- [Microsoft 365 group expiration policy](https://learn.microsoft.com/en-us/microsoft-365/solutions/microsoft-365-groups-expiration-policy)

#### Conditional Access Policy Review

If you're planning or performing a new deployment, review the [Conditional Access insights and reporting workbook](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-insights-reporting) to understand the impact of Conditional Access policies in your organization over time.

## For more information

The following resources provide additional information about user accounts:

- [What is identity lifecycle management with Microsoft Entra ID?](https://learn.microsoft.com/en-us/azure/active-directory/governance/what-is-identity-lifecycle-management)
- [How to manage inactive user accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-manage-inactive-user-accounts) \(Cloud only accounts\)
- [Block Microsoft 365 user accounts with PowerShell - Microsoft 365 Enterprise](https://learn.microsoft.com/en-us/microsoft-365/enterprise/block-user-accounts-with-microsoft-365-powershell)
- [Delete Microsoft 365 user accounts with PowerShell - Microsoft 365 Enterprise](https://learn.microsoft.com/en-us/microsoft-365/enterprise/delete-and-restore-user-accounts-with-microsoft-365-powershell)
- [Regularly check for and remove inactive user accounts in Active Directory](https://learn.microsoft.com/en-us/services-hub/unified/health/remediation-steps-ad/regularly-check-for-and-remove-inactive-user-accounts-in-active-directory)
- [Multi-tenant architecture for large institutions - Microsoft 365 Education](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/design-multi-tenant-architecture)
- [Microsoft Entra security defaults \| Microsoft Docs](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

## Next steps

Next, let's look at procures for devices.

[Next: Devices >](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/devices)
