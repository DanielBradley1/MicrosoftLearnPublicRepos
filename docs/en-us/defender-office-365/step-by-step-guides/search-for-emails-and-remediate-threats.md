<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/search-for-emails-and-remediate-threats -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Steps to use manual email remediation in Threat Explorer

Email remediation is an already existing feature that helps admins act on emails that are threats. Before you use this feature, make sure you meet the required permissions and licensing prerequisites.

## Prerequisites

Before you begin, make sure you have the following prerequisites:

- Microsoft Defender for Office 365 Plan 2 \(Included in E5 plans\)
- Sufficient permissions \(be sure to grant the account [Search and Purge](https://sip.security.microsoft.com/securitypermissions) role\)

## Create and track the remediation

Perform the following steps to create a remediation action and track it in Action Center:

Important

For better performance, remediation should be done in batches of *50,000 or fewer*. Narrow down the search result by using *latest delivery location* and trigger email remediation if the email is in remediable folder like Inbox, Junk, Deleted, for example.

1. **Select a threat to remediate** in [Threat Explorer](https://security.microsoft.com/threatexplorer) and select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-take-actions.png) **Take action**, which offers you options such as *Soft Delete* or *Hard Delete*.
2. The side pane opens and asks for details, like a name for the remediation, severity, and description. Once the information is reviewed, select **Submit**.
3. As soon as the admin approves the remediation action, the admin sees the Approval ID and a link to the [Microsoft Defender XDR Action Center history](https://security.microsoft.com/action-center/history) page. The Action Center History page is where **actions can be tracked**.

   1. **Admin action alert** - A system alert shows up in the alert queue with the name 'Administrative action submitted by an Administrator'. The alert indicates that an admin submitted a remediation action for an entity. It gives details such as the name of the admin who took the action, and the investigation link and time. The alert helps admins track important actions, like remediation, taken on entities.
   2. **Admin action investigation** - Since the analysis on entities was already done by the admin and that analysis led to the remediation action, no more analysis is done by the system. The admin action investigation shows details such as related alert, entity selected for remediation, action taken, remediation status, entity count, and approver of the action. The admin action investigation record allows admins to keep track of the investigation and actions carried out *manually*.

4. **Action logs in unified action center** - History and action logs for email actions like soft delete and move to deleted items folder, are *all available in a centralized view* under the unified **Action Center** > **History tab**.
5. **Filters in unified action center** - There are multiple filters such as remediation name, approval ID, Investigation ID, status, action source, and action type. These filters are useful for finding and tracking email actions in the unified Action Center.

Important

For better performance, remediation should be done in batches of *50,000 or fewer*. Narrow down the search result by using *latest delivery location* and trigger email remediation if the email is in remediable folder like Inbox, Junk, Deleted, for example.

## Scenarios that call for email remediation

Here are scenarios of email remediation:

1. As part of an investigation, a security operations \(SecOps\) team identifies a threat in an end-user's mailbox and wants to clear out the problem emails.
2. When suggested email actions in Automated Investigation and Response \(AIR\) are approved by SecOps, the remediation action triggers automatically for the email or email cluster identified by AIR.

Two manual email remediation scenarios:

1. The main scenario:

   1. Manual actions taken on emails \(for example, using Threat Explorer or Advanced Hunting\) are only visible in the legacy Defender for Office 365 Action Center \(Email and Collaboration > Review > Action Center in Action center - Microsoft 365 security\).

2. Two-step approval scenario:

   1. Manual actions pending approval using the two-step approval process \(1. The email was added to remediation by one analyst, 2. The email was reviewed and approved by another analyst\).

Given the common scenarios, email remediation can be triggered in three different ways.

1. **Query based remediation**: By selecting all the search results with a query \(200,000 emails can be submitted at a maximum\).
2. **Handpicked remediation**: Selecting emails one-by-one by clicking on the check box \(100 emails can be submitted at one time\).
3. **Query based remediation with exclusions**: Selecting all emails, and then manually removing a few messages \(the query can hold a maximum of 1,000 emails and the maximum number of exclusions is 100\).

## Next steps

Use the following steps to review and track remediation status in Action Center:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, select **Action center**.
3. Go to the **History** tab, select any waiting approval list. It opens up a side pane.
4. Track the action status in the unified action center.

## Learn more about manual email remediation

[Learn more about email remediation](https://learn.microsoft.com/en-us/defender-office-365/air-review-approve-pending-completed-actions).
