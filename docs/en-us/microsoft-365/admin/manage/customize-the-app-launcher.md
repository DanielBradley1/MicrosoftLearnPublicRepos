<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/customize-the-app-launcher?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Add custom tiles to the app launcher

You can add your own custom tiles to Apps that point to SharePoint sites, external sites, legacy apps, and more. The custom tile appears under the Apps section in Microsoft 365. Once your users launch the app, the app is added automatically to the list of app launcher apps for access. Adding apps to the app launcher makes it easy to find the relevant sites, apps, and resources to do your job.

Note

Adding apps to the app launcher capability is currently unavailable in the Microsoft Copilot App.

## Add a custom tile for Apps

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **... Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Org Settings**](https://admin.cloud.microsoft/?#/Settings/SecurityPrivacy).
4. In the **Org Settings** page, select the **Organization profile** tab, and then select **Custom tiles for Apps**.
5. In the **Custom tiles for Apps** pane, select **+ Add a custom tile**.
6. In the **Add a custom tile** pane:

   1. Enter a name for the new tile in the **Tile name** field. This name is the name that appears on the My apps page and app launcher.
   2. Enter a URL of the website for the new tile in the **URL of website** field. This URL is the location where you want your users to go when they select the tile on the app launcher. Use HTTPS in the URL.

      Tip

      If you're creating a tile for a SharePoint site, navigate to that site, copy the URL, and paste it here. The URL of your default team site looks like `https://<company_name>.sharepoint.com`.
   3. Enter a URL of the image for the new tile in the **Image URL** field. This image appears on the My apps page and app launcher.

      Tip

      The image should be 60x60 pixels and be available to everyone in your organization without requiring authentication.
   4. Enter a description for the new tile in the **Description** field. The description is displayed when you select the tile on the My apps page and select **App details**.
   5. Select **Save** to finish creating the custom tile.

Your custom tile appears for your users within 24 hours in the app launcher on the **All** tab and in Microsoft 365 Apps.

Note

If you don't see the custom tile created in the previous steps, make sure you have an Exchange Online mailbox assigned to you and that your mailbox has been signed into at least once. These steps are required for custom tiles in Microsoft 365.

## Edit or delete a custom tile

To edit an existing custom tile, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **... Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Org Settings**](https://admin.cloud.microsoft/?#/Settings/SecurityPrivacy).
4. In the **Org Settings** page, select the **Organization profile** tab, and then select **Custom tiles for Apps**.
5. In the **Custom tiles for Apps** pane, find the custom tile you want to edit or delete, select the horizontal ellipsis \(**...**\) next to the custom tile, and then select **Edit custom tile**.
6. In the **Edit custom tile** pane, update the **Tile name**, **URL of website**, **URL of tile image**, or **Description** for the custom tile as needed.
7. Select **Save**.

To delete an existing custom tile, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
2. From the left navigation bar, select **... Show all**, and then select **Settings** to expand it.
3. Under **Settings**, select [**Org Settings**](https://admin.cloud.microsoft/?#/Settings/SecurityPrivacy).
4. In the **Org Settings** page, select the **Organization profile** tab, and then select **Custom tiles for Apps**.
5. In the **Custom tiles for Apps** pane, find the custom tile you want to edit or delete, select the horizontal ellipsis \(**...**\) next to the custom tile, and then select **Delete custom tile**.
6. In the **Delete custom tile?** window, select **Delete**.

## Next steps

To customize the look and feel of Microsoft 365 to match your organization's brand, see [Customize the Microsoft 365 theme](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/customize-your-organization-theme?view=o365-worldwide).

## Related content

- [Pin apps to your users' app launcher](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/pin-apps-to-app-launcher?view=o365-worldwide).
- [Upgrade your Microsoft 365 for business users to the latest version](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/upgrade-users-to-latest-office-client?view=o365-worldwide).
- [Manage add-ins in the admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-addins-in-the-admin-center?view=o365-worldwide).
