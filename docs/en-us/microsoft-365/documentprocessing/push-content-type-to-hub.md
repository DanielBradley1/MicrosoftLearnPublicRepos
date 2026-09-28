<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/push-content-type-to-hub?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-11 -->

# Push content types to a hub

To make important content types more consistently available to SharePoint libraries and lists, you can push them to the hubs that you choose. Pushing the content types automatically adds them to any new lists and libraries created on the sites associated with the hub, and to any new sites added to the hub. This feature requires a [pay-as-you-go license](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-licensing?view=o365-worldwide).

For this feature to work, the content types being pushed must already be published.

To push content types to hubs

1. In the SharePoint admin center, expand **Content services**, and then select [**Content type gallery**](https://go.microsoft.com/fwlink/?linkid=2185074).
2. Select the content type that you want to push to hubs.
3. Select **Edit** in the command bar.
4. Select **Choose hub sites**.
5. Select the hub sites you want and then choose **OK**.
6. Choose **Save**.

When you push a content type to an existing hub and its existing associated sites for the first time, it can take up to an hour, from when the hub or associated sites are visited, for the settings to update in the site. Any new associations to the hub won't require this wait and will have the settings reflected in a few minutes.

After the settings are updated, the content type with these settings will be available in any newly associated site with the hub in a few minutes. The default library view will be changed to one of these automatically created views. If there are multiple content types pushed to the same library, then the latest one \(based on the order of the action of pushing those content types to the hub this library belongs to\) is what will be set as the default view. Then, any new list or library created will have the content type automatically added to it within a few minutes of creation. A pushed content type will be added to a document library only if it derives directly or indirectly from the Document content type, and a content type will be added to a list only if it does not derive from the Document content type directly or indirectly.
