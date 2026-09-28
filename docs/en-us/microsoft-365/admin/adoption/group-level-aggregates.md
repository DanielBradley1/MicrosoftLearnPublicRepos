<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/adoption/group-level-aggregates?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Enable Group Level Aggregates in Adoption Score

Group Level Aggregates in Adoption Score help admins and adoption strategists compare how different groups perform in people experiences insights. This article explains how to enable group-level insights and use Microsoft Entra ID data to identify groups that are doing well and groups that need growth in Microsoft 365.

- **Compare** different groups of your organization to understand the overall distribution of adoption scores and insights, groups that are doing well, and groups that need growth.
- **Focus** on a specific group of your organization to understand more about it in isolation.

## How to enable Group Level Aggregates

Group Level Aggregates isn't enabled by default.

Note

Only the Global administrator role can enable Group Level Aggregates.

To enable Group Level Aggregates:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. From the left navigation bar, select **… Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select **Org settings**.
4. In the **Org settings** page, make sure the **Services** tab is selected, and then select **Adoption Score** in the list of services.
5. In the **Adoption Score** pane, make sure the **Insights calculation and display** tab is selected. Under **Group data filtering**, select **Turn on group-level insights**.

Once enabled, all roles on the people experiences pages can access it.

[![Screenshot of turning on group-level insights in Adoption Score.](https://learn.microsoft.com/en-us/microsoft-365/media/enable-group-level-insights-adoption-score.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/enable-group-level-insights-adoption-score.png?view=o365-worldwide#lightbox)

## Data accuracy evaluation

Before you can enable group-level insights, run a data accuracy evaluation to check if group data is accurate. The evaluation helps you make an informed decision about which segments best reflect your organization's composition.

[![Screenshot of a warning to run a data accuracy evaluation before enabling group-level insights.](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-insights-data-accuracy.jpg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-insights-data-accuracy.jpg?view=o365-worldwide#lightbox)

The data accuracy evaluation check is a report that reflects the organization's composition based on key attributes in Microsoft Entra ID.

Currently, Microsoft Entra ID provides capabilities for five attributes:

- Company.
- Department.
- Country.
- State.
- City.

The report displays the number of users included for all the different organizational attributes out of the total number of users in Microsoft Entra ID. This data is included based on an entry in the Entra ID fields for those five selected attributes. You can download the report for these five attributes and check for data accuracy. You only run and approve this report once while setting up Group Level Aggregates.

For example, in the following screenshot, the organization has the **Department** attribute filled for XX out of the total YY users with ZZ unique departments mentioned. You see ZZ unique departments in the Group Level Aggregates filters on people experience insights pages.

[![Screenshot of the group-level data evaluation report.](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-aggregates-data-evaluation.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-aggregates-data-evaluation.png?view=o365-worldwide#lightbox)

To include all users in the group-level insights reporting, make sure the five fields are accurately updated for all users in Microsoft Entra. For subsequent updates to the Microsoft Entra attributes, you don't need to run the evaluation again. The updates are available immediately. For more information about how to update user data in Microsoft Entra, see [Add or update a user's profile information and settings in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## Filter people experiences scores

Group-level insights on people experience insights help filter the overall score and each insight for the selected group. When you apply certain filters, the portal displays an informative message when some insights aren't available.

Note

In some cases, you might not see an entire group in the filters despite all data being accurate in Microsoft Entra ID. This behavior happens when the group has fewer than 10 individuals for that unique group. This behavior protects user privacy so that no insights can be directly correlated to individual users.

[![Screenshot of filters for group-level insights in Adoption Score.](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-aggregates-filters.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/group-level-aggregates-filters.png?view=o365-worldwide#lightbox)
