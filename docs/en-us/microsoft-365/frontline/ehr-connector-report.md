<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-connector-report?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-06-26 -->

# Microsoft Teams EHR connector Virtual Appointments report

The Microsoft Teams Electronic Health Record \(EHR\) connector Virtual Appointments report in the Microsoft Teams admin center gives you a quick and easy way to view Teams EHR-integrated virtual appointments usage in your organization.

To view the report, you must be a Teams Administrator, Global Reader, Reports Reader, or Global Administrator.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use a less-privileged role.

## View the report

There are two ways to access and view the report in the Teams admin center.

- Through the [EHR connector Virtual Appointments card](#the-ehr-connector-virtual-appointments-card) in the dashboard
- Directly by choosing [**EHR connector Virtual Appointments**](#the-teams-ehr-connector-virtual-appointments-report) in **Analytics & reports** > **Usage reports**

### The EHR connector Virtual Appointments card

In the dashboard of the Microsoft Teams admin center, go to the **EHR connector Virtual Appointments** card.

Here, you get an at-a-glance view of Teams EHR-integrated virtual appointment activity by month, including completed appointments, remaining allocation, and whether you exceeded the monthly limit \(depending on the license you have\).

[![Screenshot of the EHR connector usage card in the Teams admin center dashboard.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-report-card.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-report-card.png?view=o365-worldwide#lightbox)

Choose **View details** to view the report. To purchase more licenses, choose **Buy more**.

### The Teams EHR connector Virtual Appointments report

1. In the left navigation of the Teams admin center, go to **Analytics & reports** > **Usage reports**.
2. On the **View reports** tab, choose **EHR connector Virtual Appointments** and a date range. Then, select **Run report**.

   [![Screenshot of the Teams EHR connector Virtual Appointments report in the Teams admin center.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-report.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-report.png?view=o365-worldwide#lightbox)

## Interpret the report

| Callout | Description |
| --- | --- |
| **1** | Each report shows the date for when the report was generated and the date range you chose. |
| **2** | The table gives you detailed information about each appointment that took place during the selected date range. Keep in mind that you won't see entries for appointments in which either a staff member or patient didn't join.<br><br>- **Start time \(UTC\)** is the date and time when both a staff member and participant are in the appointment.<br>- **Duration** is the time difference between the start time and when the last person leaves the appointment.<br>- **Primary** is the name of the meeting organizer.<br>- **Primary's email** is the email address of the meeting organizer.<br>- **Department** is the department information for the appointment. If the information isn't displayed correctly, contact your EHR support team. For integration with Epic, make sure `&departmentId=%PERFDEPID;;; ; ;;NONE;%` is part of the provider integration record.<br>- **Attendants** is the total number of staff members and participants in the appointment.<br>- **Within limit** indicates whether the appointment is within the allocation limit.<br>- **Appointment ID** \(coming soon\) is the appointment identifier from the EHR system. For Epic-integrated appointments, the identifier refers to the appointment CSN number. |
| **3** | You can export the report to a CSV file for offline analysis. Select **Export to Excel** to download the report. |
| **4** | Select **Filter** to filter the report details view. |
| **5** | Select **Full screen** to view the report in full screen mode. |
| **6** | Select **Edit columns** to add or remove columns in the table |

Note

For more analytics on Teams EHR-integrated virtual appointments, see [Virtual Appointments usage report](https://learn.microsoft.com/en-us/microsoft-365/frontline/virtual-appointments-usage-report?view=o365-worldwide). With the Virtual Appointments usage report, you can view key metrics such as total appointments, lobby wait time, appointment duration, and no shows. Use this information to gain insight into usage trends to help you optimize Virtual Appointments to deliver better business outcomes.

## Related articles

- [Virtual Appointments with Teams - Integration into Oracle Health EHR](https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-admin-oracle-health?view=o365-worldwide)
- [Virtual Appointments with Teams - Integration into Epic EHR](https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-admin-epic?view=o365-worldwide)
