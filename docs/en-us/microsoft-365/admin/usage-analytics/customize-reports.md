<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/customize-reports?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-04 -->

# Customize the reports in Microsoft 365 usage analytics

Microsoft 365 usage analytics provides a dashboard in Power BI that offers insights into how users adopt and use Microsoft 365. The dashboard is just a starting point to interact with the usage data. You can customize the reports for more personalized insights.

You can also use Power BI Desktop to further customize your reports by connecting them to other data sources to gain richer insights about your business.

## Customizing reports in the browser

The following two examples show how to modify an existing visual and how to create a new visual.

### Modify an existing visual

This example shows how to modify the **Activation** tab within the **Activation/Licensing** report.

1. Within the **Activation/Licensing** report, select the **Activation** tab.
2. Enter the edit mode by choosing the **Edit** button on the top through the  ![Screenshot of the more page button in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png?view=o365-worldwide) button.

   ![Screenshot of clicking Edit report on the top right navigation in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png?view=o365-worldwide)
3. On the top right, choose **Duplicate this page**.

   ![Screenshot of choosing Duplicate this page in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png?view=o365-worldwide)
4. In the bottom right, choose any of the bar charts that show the count of users activating based on the OS such as Android, iOS, Mac, and more.
5. In the **Visualizations** area to the right, select the **X** next to **Mac Count** to remove it from the visual.

   ![Screenshot of removing Mac Count from the visual in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png?view=o365-worldwide)

### Create a new visual

The following example shows how to create a new visual to track new Viva Engage users on a monthly basis.

1. Go to the **Product Usage** report by using the left navigation and select the **Viva Engage** tab.
2. Switch to edit mode by choosing  ![Screenshot of the more page button in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png?view=o365-worldwide) and **Edit**.
3. At the bottom of the page, select the  ![Screenshot of the add page button in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png?view=o365-worldwide) to create a new page.
4. In the **Visualizations** area to the right, choose the **Stacked bar chart** \(top row, first from left\).

   ![Screenshot of selecting Bar Chart in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/214c3fed-6eae-43e6-83fb-708a2d74406e.png?view=o365-worldwide)
5. To make the visualization larger, select the bottom right of that visualization and drag to resize it.
6. In the **Fields** area to the right, expand the **Calendar** table.
7. Drag **MonthName** to the fields area, directly below the **Axis** heading in the **Visualizations** area.

   ![Screenshot of dragging Month Name in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/bff99987-8c4b-4618-89fd-47df557b0ed7.png?view=o365-worldwide)
8. In the **Fields** area to the right, expand the **TenantProductUsage** table.
9. Drag **FirstTimeUsers** to the fields area, directly below the **Value** heading.
10. Drag **Product** to the **Filters** area, directly below the **Visual level filters** heading.
11. In the **Filter Type** area that appears, select the **Viva Engage** check box.

    ![Screenshot of selecting Viva Engage checkbox in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/82e99730-0de9-42da-928a-76aab0c3e609.png?view=o365-worldwide)
12. Just below the list of visualizations, choose the **Format** icon  ![Screenshot of the Format icon in Power BI Visualizations.](https://learn.microsoft.com/en-us/microsoft-365/media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png?view=o365-worldwide) .
13. Expand Title and change the **Title Text** value to **First-Time Viva Engage Users by Month**.
14. Change the **Text Size** value to **12**.
15. Change the title of the new page by editing the name of the page on bottom right.
16. Save the report by selecting **Reading View** on top and then **Save**.

## Customizing the reports in Power BI Desktop

For most customers, modifying the reports and chart visuals in Power BI web is sufficient. However, some customers might need to join this data with other data sources to gain richer insights contextual to their own business. In this case, they can customize and build other reports by using Power BI Desktop. You can download [Power BI Desktop](https://go.microsoft.com/fwlink/p/?linkid=849797) for free.

### Use the reporting APIs

You can start by connecting directly to the ODATA reporting APIs from Microsoft 365 that power these reports.

1. Go to **Get data** > **Other** > **ODATA Feed** > **Connect**.
2. In the URL window, enter `https://reports.office.com/pbi/v1.0/<tenantid>`.

   Note

   The reporting APIs are in preview and are subject to change until they go into production.

   ![Screenshot of OData feed URL for Power BI Desktop.](https://learn.microsoft.com/en-us/microsoft-365/media/c0ef967e-a454-4eba-bc8e-61e113170053.png?view=o365-worldwide)
3. When prompted to authenticate, enter your Microsoft 365 \(organization or school\) admin credentials.

   See the [Microsoft 365 Usage Analytics Overview FAQ](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics-faq?view=o365-worldwide) for more information about who is allowed to access the Microsoft 365 Adoption template app reports.
4. Once you authorize the connection, you see the **Navigator** window that shows the available datasets.

   Select all and choose **Load**.

   This action downloads the data into your Power BI Desktop. Save this file and then you can start creating the reports you need.

   ![Screenshot of ODATA values available in the reporting API in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png?view=o365-worldwide)

### Use the Microsoft 365 usage analytics template

You can also use the Power BI template file that corresponds to the Microsoft 365 usage analytics reports as a starting point to connect to the data. The advantage of using the pbit file is that it already has the connection string established. You can also take advantage of all the custom measures that are created on top of the data that the base schema returns and build on it further.

You can download the Power BI template file from the [Microsoft Download Center](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). After you download the Power BI template file, follow these steps to get started:

1. Open the pbit file.
2. Enter your tenant ID value in the dialog.

   ![Screenshot of entering your tenant ID to open the pbit file in Power BI.](https://learn.microsoft.com/en-us/microsoft-365/media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png?view=o365-worldwide)
3. Enter your admin credentials to authenticate to Microsoft 365 when prompted.

   Once authorized, the data is refreshed in the Power BI file.

   Data load might take some time. When it's complete, you can save the file as a .pbix file and continue to customize the reports or bring another data source into this report.
4. Follow [Getting started with Power BI](https://learn.microsoft.com/en-us/power-bi/fundamentals/desktop-getting-started) documentation to understand how to build reports, publish them to the Power BI service, and share with your organization. Following this path for customization and sharing might require more Power BI licenses. See Power BI [licensing guidance](https://go.microsoft.com/fwlink/p/?linkid=849803) for details.
