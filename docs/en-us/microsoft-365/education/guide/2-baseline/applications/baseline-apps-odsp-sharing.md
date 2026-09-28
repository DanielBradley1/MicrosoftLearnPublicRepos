<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-sharing -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 2: Share within Microsoft OneDrive and SharePoint

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft OneDrive and SharePoint \(ODSP\) are key components of the education offering for the Microsoft ecosystem. This article describes sharing features in OneDrive and SharePoint and how to manage them in educational environments.

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## External sharing overview

The external sharing features of SharePoint and OneDrive let users in your organization share content with people outside the organization \(such as partners, vendors, clients, or customers\). You can also use external sharing to share between licensed users on multiple Microsoft 365 subscriptions if your organization has more than one subscription. External sharing in SharePoint is part of [secure collaboration with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/solutions/setup-secure-collaboration-with-teams).

Learn more about [external sharing in SharePoint and OneDrive](https://learn.microsoft.com/en-us/sharepoint/external-sharing-overview).

## Manage sharing settings

SharePoint administrators in Microsoft 365 can change their organization-level sharing settings for SharePoint and OneDrive. \(If you want to share a file or folder, read [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) or [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)\)

For end-to-end guidance around how to configure guest sharing in Microsoft 365, see:

- [Set up secure collaboration with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/solutions/setup-secure-collaboration-with-teams)
- [Collaborate with guests on a document](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaborate-on-documents)
- [Collaborate with guests in a site](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaborate-in-site)
- [Collaborate with guests in a team](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaborate-as-team)

To change the sharing settings for a site after you set the organization-level sharing settings, see [Change sharing settings for a site.](https://learn.microsoft.com/en-us/sharepoint/change-external-sharing-site) To learn how to change the external sharing setting for a specific user's OneDrive, see [Change the external sharing setting for a user's OneDrive.](https://learn.microsoft.com/en-us/onedrive/user-external-sharing-settings)

Learn more about [managing sharing settings](https://learn.microsoft.com/en-us/sharepoint/turn-external-sharing-on-or-off).

## Change external sharing for a site

You must be at least a [SharePoint Administrator](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role) in Microsoft 365 to change the sharing settings for a site. Site owners aren't allowed to change these settings.

To learn how to change the external sharing setting for a user's OneDrive, see [Change the external sharing setting for a user's OneDrive.](https://learn.microsoft.com/en-us/sharepoint/user-external-sharing-settings) For info about changing your organization-level settings, see [Manage sharing settings.](https://learn.microsoft.com/en-us/sharepoint/turn-external-sharing-on-or-off) Keep in mind that guest sharing settings for Microsoft 365 Groups and Teams affect connected SharePoint sites.

Learn more about [changing external sharing for a site](https://learn.microsoft.com/en-us/sharepoint/change-external-sharing-site).

## Change external sharing for OneDrive

After you set the organization-wide sharing settings for Microsoft SharePoint and Microsoft OneDrive, you can further restrict the external sharing for a specific OneDrive user.

Learn more about [changing external sharing for OneDrive](https://learn.microsoft.com/en-us/sharepoint/user-external-sharing-settings).

## Sharable links overview

When users share files and folders in Microsoft 365, a shareable link is created which has permissions to the item. There are three primary link types:

1. The **Anyone links** option gives access to the item to anyone who has the link. People using an Anyone link don't have to authenticate, and their access can't be audited.
2. The **People in your organization links** option works for only people inside your Microsoft 365 organization. \(They don't work for guests in the directory, only members\).
3. The **Specific people links** option only works for the people that users specify when they share the item.

Learn more about [shareable links](https://learn.microsoft.com/en-us/sharepoint/shareable-links-anyone-specific-people-organization).

## Change default sharing links

Learn about [changing default sharing links](https://learn.microsoft.com/en-us/sharepoint/change-default-sharing-link).

## External sharing notifications \(OneDrive\)

By default, users receive notifications about file activity in OneDrive and SharePoint. These notifications appear across apps and devices. For example, the service sends notifications through the Firebase Cloud Messaging service to the Office mobile app for Android or the Apple Push Notification service to the Office mobile app for iOS. It also sends notifications to the OneDrive sync app for Windows or Mac. As a global or SharePoint admin in Microsoft 365, you can turn off these notifications for all users for compliance purposes. If you allow these notifications, users can select to turn them off app by app where they don't want them.

Learn more about [external sharing notifications](https://learn.microsoft.com/en-us/sharepoint/turn-on-external-sharing-notifications).

## File Requests

With the [file request feature](https://support.microsoft.com/office/create-a-file-request-f54aa7f8-2589-4421-b351-d415fc3b83af) in OneDrive or SharePoint, you can choose a folder where others can upload files using a link that you send them. People you request files from can only upload files; they can't see the content of the folder, edit, delete, or download files, or even see who else has uploaded files.

Admins can use the SharePoint Online Management Shell to disable or enable the Request files feature on OneDrive or SharePoint sites. If there's no change on sharing capability for all sites, then the file request feature can be enabled.

Learn more about [file requests](https://learn.microsoft.com/en-us/sharepoint/enable-file-requests).

## Plan secure file collaboration

With Microsoft 365 services, you can create a secure and productive file collaboration environment for your users. SharePoint powers much of this, but the capabilities of file collaboration in Microsoft 365 reach beyond the traditional SharePoint site. Teams, OneDrive, and various governance and security options all play a role in creating a rich environment where users can collaborate easily and where your organization's sensitive content remains secure.

Options and decisions that you as an administrator should consider when setting up a collaboration environment include:

- How SharePoint relates to other collaboration services in Microsoft 365, including OneDrive, Microsoft 365 Groups, and Teams.
- How you can create an intuitive and productive collaboration environment for your users.
- How you can protect your organization's data by managing access through permissions, data classifications, governance rules, and monitoring.

This is part of the broader Microsoft 365 collaboration story:

- [Secure collaboration with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/solutions/setup-secure-collaboration-with-teams)
- [Collaboration governance](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaboration-governance-overview)
- [Meetings, webinars, and live events](https://learn.microsoft.com/en-us/microsoftteams/quick-start-meetings-live-events)

Learn more about [planning secure file collaboration](https://learn.microsoft.com/en-us/sharepoint/deploy-file-collaboration).

## Integration with Microsoft B2B

Learn how to enable Microsoft SharePoint and Microsoft OneDrive integration with [Microsoft Entra B2B.](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)

Microsoft Entra B2B provides authentication and management of guests. Authentication happens via one-time passcode when they don't already have a work or school account or a Microsoft account.

Learn more about [integration with Microsoft B2B](https://learn.microsoft.com/en-us/sharepoint/sharepoint-azureb2b-integration).

## Restrict domain sharing

If you want to restrict sharing with other organizations \(either at the organization level or site level\), you can limit sharing by domain.

Learn more about [restricting domain sharing](https://learn.microsoft.com/en-us/sharepoint/restricted-domains-sharing).

## Limit sharing by security group

You can restrict external sharing of SharePoint and OneDrive content so that only users in specific security groups can share externally. The people in these security groups must be allowed to invite guests in the [Microsoft Entra guest invite settings.](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/external-collaboration-settings-configure)

Learn more about [limiting sharing by security group](https://learn.microsoft.com/en-us/sharepoint/manage-security-groups).

## Report on sharing

You can create a CSV file of every unique file, user, permission, and link on a given SharePoint site or OneDrive. This can help you understand how sharing is being used and if any files or folders are being shared with guests. You must be a site admin to run the report. More reporting options are available with [Microsoft Graph Data Connect.](https://learn.microsoft.com/en-us/graph/data-connect-datasets#onedrive-and-sharepoint-online)

Learn more about [reporting on sharing](https://learn.microsoft.com/en-us/sharepoint/sharing-reports).

## Create a B2B extranet

An extranet site in Microsoft SharePoint is a site that you create to let external partners have access to specific content, and to collaborate with them. Extranet sites are a way for partners to securely do business with your organization. The content for your partner is kept in one place and they have only the content and access they need. They don't need to email the documents back and forth or use tools that aren't sanctioned by your IT department.

Learn more about [creating a B2B extranet](https://learn.microsoft.com/en-us/sharepoint/create-b2b-extranet).

Note

For education scenarios:

-

## Next steps

Now that you completed the OneDrive/SharePoint sharing section, you're ready to configure security and access controls in OneDrive/SharePoint.

[Next: Configure security and access controls>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-security-access)
