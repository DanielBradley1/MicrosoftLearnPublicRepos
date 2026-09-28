<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-set-student-age-group -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Step 9: Set student age group

## Overview

To grant students access to Microsoft Copilot Chat in a Microsoft Education tenant, first configure the Tenant ID for the tenant, as detailed in [Step 8](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-identifier). If the organization and Tenant ID are set to the K12 value, you must also set the age group attribute on each student user account before they can access Microsoft Copilot Chat. This document explains how to quickly define the age group attribute at scale.

## How to set student age group

For most organizations, setting the user’s age group attribute is performed in bulk instead of manually setting these values one by one. This section covers a few different methods.

## Set age group in bulk

The fastest way to make Copilot Chat accessible for students is to set the AgeGroup attribute in bulk. In the Microsoft 365 Admin Center, follow these steps:

1. Open the [Microsoft 365 Admin Center](https://admin.cloud.microsoft/).
2. Navigate to **Settings** > **Org Settings** > **Services** tab.

   [![Screenshot showing Microsoft 365 admin center org settings.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-1.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-1.png#lightbox)
3. Select the Microsoft Education service in the list.

   [![Screenshot showing Microsoft 365 admin center Microsoft Education service.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-2.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-2.png#lightbox)
4. Find the section called **Manage student age groups**.

   [![Screenshot showing Microsoft 365 admin center manage student age groups.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-3.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-3.png#lightbox)
5. Select **Download users** to download a CSV file of all users within your tenant.
6. Save the file as `Users.csv` \(you can create your own `Users.csv` if you prefer\).
7. You can delete all columns except for the following columns, maintaining the header row exactly as shown:

   - User principal name
   - AgeGroup

8. The CSV file should look like this:

   [![Screenshot showing CSV file.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-4.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-4.png#lightbox)
9. Fill out the age group values in the **AgeGroup** column as appropriate and save the file. To learn what values are supported, see the section [Values for Age Group attribute](#values-for-the-age-group-attribute).
10. When the CSV is up to date with the right age group and saved, select **Upload users**, and select the CSV file.
11. When prompted to confirm, select **Continue**.

    [![Screenshot showing process user changes.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-5.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-5.png#lightbox)
12. After the bulk update finishes, you can confirm the updates were successful by selecting **Download users** again.
13. You can repeat this process as often as needed to update and maintain your directory and the student’s age group attribute.

## Set age group for individual users

Setting the age group attribute for individual users can be done in a few different ways.

### Microsoft Entra admin center

1. Go to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. Select **Users** and search for the user.
3. Select the **Properties** tab.
4. Find the **Parental Controls** section and select the edit icon.

   [![Screenshot showing parental controls.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-6.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-6.png#lightbox)
5. Adjust the **Age group** value from the dropdown menu, as needed.

   [![Screenshot showing age group value.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-7.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/age/age-7.png#lightbox)

### PowerShell and MS Graph API

Each user in Microsoft 365 has an age group attribute. You can adjust this attribute directly from the [MS Graph API/user endpoint](https://learn.microsoft.com/en-us/graph/api/resources/user) by using a tool like [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) or by using a tool like PowerShell. The exact attribute is called [ageGroup](https://learn.microsoft.com/en-us/graph/api/resources/user#agegroup-values).

With the AgeGroup attribute available on MS Graph, admins can also use the MS Graph PowerShell module to set the age group attribute for one or several users by using the [Update-MgUser](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.users/update-mguser) cmdlet.

## Set age group in School Data Sync

If your organization is running Microsoft School Data Sync \(SDS\), you can also manage students’ age group values in bulk by using the [Manage Data sync pipeline](https://learn.microsoft.com/en-us/schooldatasync/manage-data-microsoft-365).

## Values for the Age Group attribute

There are three primary values for the age group attribute. Currently, Microsoft policy only allows students set to NotAdult and Adult to access Copilot.

- Minor – generally reserved for students under 13, who are classified as a minor. Any student within a K12 tenant who is set to minor doesn't have access to Copilot.
- NotAdult – generally reserved for students who are teens, aged 13 – 17. Students in K12 tenants set to NotAdult are granted Copilot access.
- Adult – generally reserved for students who are adults, aged 18 and over. Students in K12 tenants set to Adult are granted Copilot access.
