<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/user-groups -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Import user groups from connected apps

When you connect apps using API connectors, Microsoft Defender for Cloud Apps enables you to import user groups, for example from Microsoft 365 and Microsoft Entra ID. There are two types of user groups:

- **Automatic groups:** Automatic groups are created by default by Microsoft Defender for Cloud Apps. For example, there's an automatic user group called **External** that combines all users from all apps who are external to your organization and have access to files or were in user activities in your tenant. The following automatic groups exist in Defender for Cloud Apps:

  - External
  - Dropbox administrator
  - Microsoft 365 administrator
  - Google Workspace administrator
  - Box administrator
  - All Salesforce standard and custom profiles, for example, Salesforce System Administrator. See the full list of [Salesforce standard profiles](https://help.salesforce.com/s/articleView?id=sf.standard_profiles.htm).

- **Imported groups:** You can import any group from your connected apps. For example, you can import user groups from Microsoft 365 \(Active Directory\) and other connected apps. These groups enable you to look for threats in your org, not by looking at the whole org or at a specific user, but by looking at a specific group.

  Typical scenarios that use imported user groups include:

  - Investigating which docs the HR people look at.
  - Check if there's something unusual happening in the executive group.
  - Find if someone from the admin group performed an activity outside the US.

## Import a user group from a connected app

1. In the Defender portal, select **Settings > Cloud Apps > System > User groups > + Import user group**.
2. In the **Import user group** pane, select the app from which to import the user group. The apps shown depend on which connectors you've deployed.
3. Select the group you want to import. The list includes the first 50 groups from the existing user groups in the app. If you don't see your group, enter search text in the search field above the list.

   To add a new group to the list, do so in the app itself, and then return to the Microsoft Defender portal to view your new group in the list.
4. \(Optional\) Select to be notified by email when the import process is complete.
5. Select **Import**.

   After the import is complete, select your group from the **User groups** page to view a list of all group members. Select any group member to drill down further for more details, including the apps used and a summary of the account activities. Imported groups can also be selected as filters when investigating in the **Activity log** and when creating policies. Group members are automatically synchronized for imported groups, just as they are for Active Directory Connect.

Note

- The maximum number of imported user groups is 500.
- Only active users will be imported as part of the imported group. Any suspended, deleted, or disabled users will be ignored.
- There may be a short delay until imported user groups are available in filters.
- Only activities performed after importing a user group will be tagged as having been performed by a member of the user group.
- After the initial sync, groups are usually updated every hour. However, due to various factors there could be times where this might take several hours.
- Usernames must contain only standard alphanumeric characters \(a–z, A–Z, 0–9\). Usernames with special characters such as ~ or # aren't supported.

For more information on using the User group filters, see [Activities](https://learn.microsoft.com/en-us/defender-cloud-apps/activity-filters).

## Next steps

[Set up cloud discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
