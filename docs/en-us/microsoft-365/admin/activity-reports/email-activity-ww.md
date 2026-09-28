<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/email-activity-ww?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-15 -->

# Exchange email activity report

The Exchange email activity report provides a high-level view of email traffic within your organization. Use the Exchange email activity report to understand the trends and per-user level details of the email activity within your organization.

Note

The Exchange email activity report is only available for mailboxes that are associated with users who have licenses.

For general information about usage reports in the Microsoft 365 admin center, and to see a list of all available reports, see [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide).

## View the Exchange email activity report in the Microsoft 365 admin center

For information about the roles needed to view usage reports, see "Before you begin" in [Microsoft 365 admin center usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#before-you-begin)

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the navigation menu, select **Reports**. If you don't see **Reports**, select **Show all**, and then select **Reports**.
3. Select [Usage](https://go.microsoft.com/fwlink/p/?linkid=2074756).
4. On the **Usage** page, under **Reports**, select **Exchange**.
5. On the report page, select the **Email activity** tab.

## Interpret the Exchange email activity report

The report displays trends over the last 7, 30, 90, or 180 days. However, if you select a particular day in the report, the table shows data for up to 28 days from the current date, not the date the report generated. The data in each report usually covers up to the last 24 to 48 hours.

You can view your users' email activity by looking at the **Activity** and **Users** charts.

[![Screenshot of the email activity report.](https://learn.microsoft.com/en-us/microsoft-365/media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png?view=o365-worldwide#lightbox)

The **Activity** chart helps you understand the trend of the amount of email activity going on in your organization. You can see the split of email send, email read, email received, meeting created, or meeting interacted activities. On the **Activity** chart, the Y axis is the count of activity of the type email sent, email received, email read, meeting created, and meeting interacted.

The **User** chart helps you understand the trend of the number of unique users who are generating the email activities. You can look at the trend of users performing email sending, email reading, email receiving, meeting creating, or meeting interacting activities. On the **Users** activity chart, the Y axis is the users performing activity of the type email sent, email received, email read, meeting created, or meeting interacted.

The X axis on both charts is the selected date range for this specific report.

You can filter the series you see on either chart by selecting an item in the legend.

To add or remove columns from the report, select **Choose columns**.

[![Screenshot of the email activity report column options.](https://learn.microsoft.com/en-us/microsoft-365/media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png?view=o365-worldwide#lightbox)

To export the report data into an Excel .csv file, select **Export**. This action exports the usage data of all users and enables you to do simple sorting, filtering, and searching for further analysis.

The following table shows a breakdown of the email activities at the per-user level. This data shows all users that have an Exchange product assigned to them and their email activities.

| Metric | Definition |
| :--- | :--- |
| Username | The email address of the user. |
| Display name | The full name of the user. |
| Deleted | Refers to the user whose current state is deleted, but was active during some part of the reporting period of the report. |
| Deleted date | The date the user was deleted. |
| Last activity date | The last time the user performed a read or send email activity. |
| Send actions | The number of times an email send action was recorded for the user. |
| Receive actions | The number of times an email received action was recorded for the user. |
| Read actions | The number of times an email read action was recorded for the user. |
| Meeting created actions | The number of times a meeting request send action was recorded for the user. |
| Meeting interacted actions | The number of times a meeting request accept, tentative, decline, or cancel action was recorded for the user. |
| Product assigned | The products that are assigned to this user. |

Note

By default, user-specific information like usernames, display names, groups, and sites is hidden in usage reports. To learn how to display this information in usage reports, see [Show user, group, or site details in usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide#show-user-group-or-site-details-in-usage-reports).
