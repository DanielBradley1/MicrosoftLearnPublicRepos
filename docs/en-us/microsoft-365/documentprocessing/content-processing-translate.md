<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/content-processing-translate?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Create a rule to automatically translate a file in a document library

You can create a rule to automatically translate a document [when a new file is added](#translate-a-document-when-a-new-file-is-added) or [when data in a column changes](#translate-a-document-when-data-in-a-column-changes) in a SharePoint document library with document processing for Microsoft 365.

Note

To use a rule to translate a document, you must have the [document translation service](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-pay-as-you-go-services?view=o365-worldwide) enabled.

## Translate a document when a new file is added

To create a rule to translate documents automatically when a document is created, follow these steps:

1. From a SharePoint document library, select **Automate** > **Rules** > **Create a rule**.

   ![Screenshot of the document library showing the Automate > Rules > Create a rule option.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/content-processing-create-rule.png?view=o365-worldwide)
2. On the **Create a rule** page, select **A new file is added**.

   ![Screenshot of the Create a rule page showing the A new file is added option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/content-processing-create-a-rule-page.png?view=o365-worldwide)
3. Under **When a new file is added**, complete the rule statement:

   a. Select **Choose action**, and then select **create a translated copy in**.

   ![Screenshot of the rule statement page showing the translation option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-rule-create-copy.png?view=o365-worldwide)

   b. Select **enter a language**, and then enter a language or use the drop-down menu to choose the language or languages into which you want to translate the file.

   ![Screenshot of the rule statement page showing the enter language option.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-rule-enter-language.png?view=o365-worldwide)

   c. If you want to use a [custom glossary file](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/translation-glossary?view=o365-worldwide) for the translation, select **Choose a file or paste a link**, and then select the glossary file or [add a link to the file](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/translation-glossary?view=o365-worldwide#link-to-a-glossary-file). The option to add a glossary is only available when you select one language at a time.

   ![Screenshot of the rule statement page showing the glossary option.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-rule-enter-language-glossary.png?view=o365-worldwide)
4. When your rule statement is complete, select **Create**. You can [see and manage the new rule](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/content-processing-overview?view=o365-worldwide#manage-a-rule) on the **Manage rules** page.

## Translate a document when data in a column changes

To create a rule to translate documents automatically when data in a column changes, follow these steps:

1. From a SharePoint document library, select **Automate** > **Rules** > **Create a rule**.

   ![Screenshot of the document library showing the Automate > Rules > Create a rule option.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/content-processing-create-rule.png?view=o365-worldwide)
2. On the **Create a rule** page, select **Data in a column changes**.

   ![Screenshot of the Create a rule page showing the A new file is added option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/content-processing-create-a-rule-page.png?view=o365-worldwide)
3. Under **When data in a column changes**, complete the rule statement:

   a. Select **Choose a column**, and then select the appropriate column for which to translate the file.

   ![Screenshot of the Create a rule page showing the beginning rule statement.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-beginning-rule.png?view=o365-worldwide)

   b. Select **Choose a condition**, and then select the appropriate condition under which to translate the file.

   c. Select **Choose action**, and then select **create a translated copy in**.

   d. Select **enter a language**, and then select the language into which you want to translate the file.

   ![Screenshot of the Create a rule page showing the enter a language option.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-column-enter-language.png?view=o365-worldwide)
4. When your rule statement is complete, select **Create**. You can [see and manage the new rule](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/content-processing-overview?view=o365-worldwide#manage-a-rule) on the **Manage rules** page.
