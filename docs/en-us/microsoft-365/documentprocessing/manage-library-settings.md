<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/manage-library-settings?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# Manage library settings for document processing

<sup>**Applies to:** ✓ All custom models \| ✓ All prebuilt models</sup>

Library settings in a SharePoint document library provide information about the document processing model and allow you to configure specific settings for the library.

To access library settings from a SharePoint document library, select **Settings**  ![Image showing the Settings menu icon.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/settings-icon.png?view=o365-worldwide) > **Library settings**.

![Screenshot of the Settings menu for a SharePoint document library.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/syntex-library-settings.png?view=o365-worldwide)

## Automatic classification and extraction

When you apply a model to a library, the service automatically adds the content type and updates the default view with the labels you extracted showing as columns. Then, every time you add or edit a document in the library, the service processes the document again, classifying the document and extracting text from it.

By default, the service processes a file every time the file is uploaded or edited. If you want to process new files only and not every time a file is modified, you can change the setting.

### To process new files only

Follow these steps if you want the service to process new files only.

1. On the **Library settings** panel, under **Automatic classification and extraction**, select **New files only**.

   ![Screenshot of the Library settings panel with the Automatic classification and extraction option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/automatic-classification-setting.png?view=o365-worldwide)
2. Select **Save**. Now only new files will be processed.

   Even with this setting selected, you can still select updated files and manually process them using the **Classify and extract** option in the document library.
