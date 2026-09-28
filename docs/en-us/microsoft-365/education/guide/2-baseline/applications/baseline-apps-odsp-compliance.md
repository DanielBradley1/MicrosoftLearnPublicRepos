<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-compliance -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 4: Compliance in Microsoft OneDrive and SharePoint for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft OneDrive and SharePoint are key components of the education offering for the Microsoft ecosystem. This article provides guidance on compliance in OneDrive and SharePoint for education.

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Block guest access to newly added files

Note

Microsoft Purview Data Loss Prevention requires an A3 or A5 license.

When new files are added to SharePoint or OneDrive in Microsoft 365, it takes a while for [Microsoft Purview Data Loss Prevention \(DLP\) policy](https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-learn-about-dlp) to scan the content and apply rules to help protect sensitive content. If external sharing is turned on, sensitive content could be shared and accessed by guests before the DLP rule finishes processing.

Learn more about how to [block guest access to newly added files](https://learn.microsoft.com/en-us/sharepoint/sensitive-by-default).

## Manage site access based on sensitivity level

Note

This feature requires **[Microsoft Sharepoint Premium - SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management)**.

With [Microsoft Entra authentication context](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#configure-authentication-contexts), you can enforce more stringent access conditions when users access SharePoint sites.

You can use authentication contexts to connect an [Microsoft Entra Conditional Access policy](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) to a SharePoint site. Policies can be applied directly to the site or via a sensitivity label.

This capability can't be applied to the root site in SharePoint \(for example, `https://contoso.sharepoint.com`\)

Learn more about how to [manage site access based on sensitivity level](https://learn.microsoft.com/en-us/sharepoint/authentication-context-example).

## Generate data access governance report

Note

This feature requires **[Microsoft Sharepoint Premium - SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management)** or an A5 license.

As sprawl and oversharing of SharePoint sites increase with exponential data growth, organizations need help with governing their data. Data access governance reports can help you govern access to SharePoint data. The reports let you discover sites that contain potentially overshared or sensitive content. You can use these reports to assess and apply the appropriate security and compliance policies.

Learn more about how to [generate data access governance reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports).

## Generate AI insights

Note

This feature requires **[Microsoft Sharepoint Premium - SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management)**.

The AI insights feature for [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management) uses a language model to identify patterns and potential issues from reporting and receive actionable recommendations to solve issues.

As an IT administrator, you can reduce the manual effort required to review reports during audits, and mitigate content governance issues with the AI insights feature in SharePoint admin center.

Learn more about how to [generate AI insights](https://learn.microsoft.com/en-us/sharepoint/ai-insights).

## Initiate site access reviews for data access governance reports

Note

This feature requires **[Microsoft Sharepoint Premium - SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management)**.

Site access review in the SharePoint admin center lets IT administrators delegate the review process of data access governance reports to the site owners of overshared sites.

Site access review involves site owners in the review process so they can address the concern of overshared sites identified in [data access governance reports.](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports) This feature is crucial because:

- IT administrators can't have access to file-level or item-level details due to compliance reasons.
- Site owners are best positioned to review and address oversharing issues for their own sites.

Learn more about how to [initiate site access reviews for data access governance reports](https://learn.microsoft.com/en-us/sharepoint/site-access-review).

## Privacy, security, and compliance in OneDrive

Microsoft is transparent about the specific policies, operational practices, and technologies that help you ensure the privacy, security, and compliance of your data across Microsoft OneDrive.

- Microsoft respects the privacy and ownership of data you use to train and process models in Microsoft OneDrive.
- None of your organization's data is used or transferred by Microsoft to train AI models, large-language models, or any other models.
- Your data remains securely within your organization’s tenant.

Learn more about [privacy, security, and compliance in OneDrive](https://learn.microsoft.com/en-us/sharepoint/onedrive-privacy-security-overview).

## Manage unlicensed OneDrive accounts

As an IT administrator, you might encounter situations where some of your users have unmanaged and unlicensed OneDrive accounts within your organization. Unlicensed OneDrive accounts can pose security and compliance risks, as well as create confusion and duplication of files.

Learn more about how to [manage unlicensed OneDrive accounts](https://learn.microsoft.com/en-us/sharepoint/unlicensed-onedrive-accounts).

## Default sensitivity labels for a document library

Note

This feature requires a Microsoft 365 A5 license.

When SharePoint is enabled for sensitivity labels, you can configure a default label for document libraries. Then, any new files uploaded to that library, or existing files edited in the library will have that label applied if they don't already have a sensitivity label, or they have a sensitivity label but with lower priority. Learn more about how to [configure default sensitivity labels for a document library](https://learn.microsoft.com/en-us/purview/sensitivity-labels-sharepoint-default-label).

## Use information barriers \(SharePoint\)

[Microsoft Purview Information Barriers](https://learn.microsoft.com/en-us/purview/information-barriers) are policies in Microsoft 365 that a compliance admin can configure to prevent users from communicating and collaborating with each other. This solution is useful if, for example, one division is handling information that shouldn't be shared with specific other divisions, or a division needs to be prevented, or isolated, from collaborating with all users outside of the division. Information barriers are often used in highly regulated industries and those organizations with compliance requirements, such as finance, legal, and government.

For SharePoint, information barriers can determine and prevent the following kinds of unauthorized collaborations:

- Adding a user to a site
- User access to a site or site content
- Sharing a site or site content with other users

Learn more about how to [use information barriers \(SharePoint\)](https://learn.microsoft.com/en-us/purview/information-barriers-sharepoint).

## Use information barriers \(OneDrive\)

Microsoft Purview Information Barriers are policies in Microsoft 365 that a compliance admin can configure to prevent users from communicating and collaborating with each other. This solution is useful if, for example, one division is handling information that shouldn't be shared with specific other divisions, or a division needs to be prevented, or isolated, from collaborating with all users outside of the division. Information barriers are often used in highly regulated industries and those organizations with compliance requirements, such as finance, legal, and government.

For OneDrive, information barriers can determine and prevent the following kinds of unauthorized collaborations:

- User access to OneDrive or stored content
- Sharing OneDrive or stored content with other users

Learn more about how to [use information barriers \(OneDrive\)](https://learn.microsoft.com/en-us/purview/information-barriers-onedrive).

## Configure information barriers compliance assistance

Explanation of how you can enable the information barrier compliance assistant for group-connected SharePoint sites. These sites are sites that don't have an associated team in Microsoft Teams. When the information barrier compliance assistant is enabled, users who don't match the segments specified on this site are automatically removed to ensure group membership honors configured information barrier policies. This configuration may help ensure your organization remains compliant with standards, policies, and compliance regulations.

Learn more about how to [configure information barriers compliance assistance](https://learn.microsoft.com/en-us/purview/information-barriers-sharepoint-assistant).

## Create an information barriers policy report

If a compliance administrator changes an existing information barriers policy, the change might affect the compatibility of segments already associated with a site.

For example, a policy might allow communication and collaboration between the Sales and Research segments. Later, the policy might not allow communication and collaboration between these segments. The segments are incompatible and shouldn't be associated with the same site.

The SharePoint information barriers policy compliance report lets SharePoint Administrators view the list of sites that are noncompliant with existing policies. The report covers these sites:

- Microsoft 365 group-connected team sites that aren't connected to Microsoft Teams
- Communication sites
- Modern team sites that aren't connected to Microsoft 365 groups
- OneDrive

The report displays the list of sites that are noncompliant per the existing policies which were recently updated. For each noncompliant site, it shows compatible segments, incompatible segments, and invalid segments \(those segments that no longer exist\).

If a OneDrive is noncompliant, this report lets you update the OneDrive to be compliant with the latest information barrier policies in your organization.

Learn more about how to [create an information barriers policy report](https://learn.microsoft.com/en-us/purview/information-barriers-sharepoint-report).

## Control notifications

By default, SharePoint mobile app users can receive notifications about site activity. The service sends these notifications through the Firebase Cloud Messaging service for Android or the Apple Push Notification service for iOS. As a SharePoint Administrator and higher in Microsoft 365, you can turn off these notifications for all users for compliance purposes. If you allow these notifications, users can select to turn them off.

Currently, notifications are sent for the following activities:

- SharePoint news published \(users receive these based on relevancy\)
- Page comment \(sent to the page author\)
- Page comment reply \(sent to the page author and the author of the comment that is being replied to\)
- Page comment mention \(sent to person @ mentioned\)
- Page like \(sent to the page author\)

Learn more about how to [control notifications](https://learn.microsoft.com/en-us/SharePoint/notifications).

## Migration guidance for older features - Overview

If you need to retain or delete content in Microsoft 365, we recommend using Microsoft Purview Data Lifecycle Management and Microsoft Purview Records Management features instead of older information management and records management features in SharePoint for Microsoft 365.

We have a long-term deprecation plan for these older features. More information, including dates, is in the deprecation timeline. Feature deprecations are communicated in advance to give customers time to prepare and perform any applicable migration activities.

The following older information management and records management features in SharePoint for Microsoft 365 are under consideration for deprecation:

- Record Center

  - Create a record center site
  - Submit records to the record center \(commonly referred to as "send to" location\)
  - Content Organizer

- Information management policies
- In-place records management, including vault abilities
- Document deletion policies \(deletion only\)
- Policies for site closure and deletion \(deletion only\)

Learn more:

- [Migration guidance for older features - Overview](https://learn.microsoft.com/en-us/sharepoint/use-microsoft-purview-risk-and-compliance-solutions).
- [Migration guidance for older features - Migration strategies \(compliance\)](https://learn.microsoft.com/en-us/sharepoint/migration-strategies)
