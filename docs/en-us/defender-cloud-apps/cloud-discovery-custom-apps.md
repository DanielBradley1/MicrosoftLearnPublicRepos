<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/cloud-discovery-custom-apps -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Add custom apps to cloud discovery

Cloud discovery analyzes your traffic logs against the Defender for Cloud Apps catalog. Over 31,000 cloud apps are in the cloud app catalog. The catalog contains publicly available cloud apps only, for which Defender for Cloud Apps provides visibility and risk information.

To gain visibility into cloud apps that are excluded from the cloud app catalog, Defender for Cloud Apps enables you to discover use of custom cloud apps \(LOB apps\) that were developed or assigned specifically for your organization.

By adding a new custom cloud app, Defender for Cloud Apps can match uploaded firewall and proxy traffic log messages to the app and then provide you with visibility into the use of this app across your organization in the cloud discovery pages, such as how many users use the app, how many unique source IP addresses use it, and how much traffic is transmitted to and from the app.

## Add a new custom cloud app

To add a new custom cloud app, perform the following steps:

1. In the Microsoft Defender Portal, under **Cloud Apps**, select **Cloud Discovery**. You should see the cloud discovery dashboard.

   ![Screenshot of the Cloud Discovery dashboard menu in the Microsoft Defender Portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/cloud-discovery-dashboard-menu.png)

2. In the top right corner, select the **Action** menu and then select **Add new custom app**.

   ![Screenshot of the Action menu with the Add new custom app option selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/add-custom-app-menu.png)

3. Fill in the fields to define the new app record that will be listed in the cloud app catalog and in cloud discovery after it's discovered in your firewall logs.

   ![Screenshot of the Add custom app page showing fields for defining a new custom app record.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/add-custom-app.png)

4. Under **Domains**, fill in the unique domains that are used when accessing the custom app. These domains are used to match traffic log messages to this app. If the data source you're using doesn't have app URL information, make sure you fill in the **IPv4** and **IPv6** address fields.
5. Add the **Hosting platform** and **Azure Subscription ID**. Optionally, specify the app's **Business unit**.
6. Assign a risk **Score** and add **App Notes** to help you track changes for this record.
7. Select **Create**.

After the app is created, the custom app is available for you in the cloud app catalog.

At any time, in the cloud app catalog, you can select the three dots at the end of a custom app's row to edit or delete the custom app.

Warning

Avoid adding custom apps when you are using the **Remove all tags** feature. Using **Remove all tags** also removes the **Custom app** tag from the app.

Note

Custom apps are automatically tagged with the **Custom app** tag after you add them. To view all your custom apps, set the **App tag** filter to *Custom app*.

## Next steps

[User activity policies](https://learn.microsoft.com/en-us/defender-cloud-apps/user-activity-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
