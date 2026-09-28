<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-content-center?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Create a content center for document processing models

<sup>**Applies to:** ✓ All custom models \| ✓ All prebuilt models</sup>

To create and manage enterprise models, you first need a content center. The content center is the model creation interface and also contains information about which document libraries published models have been applied to.

You create a default content center during [setup](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/set-up-content-understanding?view=o365-worldwide). But a SharePoint admin can also choose to create additional centers as needed. While a single content center might be fine for environments for which you want a roll-up of all model activity, you might want to have additional centers for multiple departments within your organization, which might have different needs and permission requirements for their models.

![Select a doc library.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/content-center-page.png?view=o365-worldwide)

Additionally, if you want to try document processing models, you can create a content center using the instructions in this article without purchasing licenses. Unlicensed users can create models but can't apply them to a document library.

Note

In a [Microsoft 365 Multi-Geo environment](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo?view=o365-worldwide), if you have a single default content center in your central location, you can only provide a roll-up of model activity from within that location. You currently cannot get a roll-up of model activity across farm-boundaries in Multi-Geo environment.

## Create a content center

A SharePoint admin can create a content center site like they would [create any other SharePoint site](https://learn.microsoft.com/en-us/sharepoint/create-site-collection) through the admin center site provisioning panel.

To create a new content center:

1. On the Microsoft 365 admin center, go to the [**SharePoint admin center** > **Active sites**](https://go.microsoft.com/fwlink/?linkid=2185220).
2. On the **Active sites** page, select **Create**, and then select **Browse more sites**.
3. On the **Choose a template** menu, select **Content center**.
4. For the new site, provide a **Site name**, **Primary administrator**, and a **Language**.
5. Select **Finished**.

After you create a content center site, you'll see it listed on [**Active sites**](https://go.microsoft.com/fwlink/?linkid=2185220) in the SharePoint admin center.

### Give access to additional users

After you create the site, you can give additional users access to the site through the standard [SharePoint site permissions model](https://learn.microsoft.com/en-us/sharepoint/modern-experience-sharing-permissions).

### Roll up of models in the default content center

The first content center created during setup is the *default content center*. If subsequent content centers are created, their models are shown in the default content center view.

![Screenshot of the Model library in the default content center.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/model-library-default-content-center.png?view=o365-worldwide)

The **Models** library in the default content center view groups the created models by content center for a summary view of all models that have been created.

Note

You can't change the designated default content center. It's always the first content center created during setup.
