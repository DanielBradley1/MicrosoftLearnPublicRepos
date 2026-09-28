<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/translation-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Overview of document translation

Note

Through June 2026, you can try out a [limited amount](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide#included-monthly-capacity) of document translation and other selected content services at no cost if you have [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide) set up. For information and limitations, see [Try out pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide).

Document translation lets you easily create a translated copy of a selected file or a set of files in a SharePoint document library. You can translate a file in one language or up to 10 language at a time, while preserving the original format and structure of the file. Translation is available for all supported languages and dialects.

![Screenshot showing a document library with translated documents.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/translation-sample-library.png?view=o365-worldwide)

This feature lets you translate files of different types either manually or automatically by [creating a rule](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/content-processing-translate?view=o365-worldwide).

You can also use the translation feature for translating video transcripts and closed captioning files. For more information, see [Transcript translations in Stream for SharePoint](https://support.microsoft.com/office/microsoft-syntex-pay-as-you-go-transcript-translations-in-stream-for-sharepoint-2e34ad1b-e213-47ed-a806-5cc0d88751de).

## Requirements and limitations

| Icon | Description |
| --- | --- |
| ![Files symbol.](https://learn.microsoft.com/en-us/office/media/icons/files-blue.png) | **Supported file types**  <br>This service supports the following file types: [see supported document formats](https://learn.microsoft.com/en-us/azure/ai-services/translator/document-translation/overview#batch-supported-document-formats). |
| ![Check mark in a circle symbol.](https://learn.microsoft.com/en-us/office/media/icons/success-blue.png) | **Supported file sizes**  <br>The maximum file size for documents to be translated is limited to 40 MB. |
| ![Conversation symbol.](https://learn.microsoft.com/en-us/office/media/icons/chat-room-conversation-blue.png) | **Supported languages**  <br>This service is available for [all supported languages and dialects](https://learn.microsoft.com/en-us/azure/ai-services/translator/language-support?source=recommendations#translation). |
| ![Security symbol.](https://learn.microsoft.com/en-us/office/media/icons/security-blue.png) | **Manage Lists permission**  <br>To create translated file copies, a user must be a site member and have the Manage Lists permission on the document library. |
| ![Globe symbol.](https://learn.microsoft.com/en-us/office/media/icons/globe-internet.png) | **Multi-Geo environments**  <br>When setting up this service in a [Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo) environment, you can only configure it to use the service in the central location. If you want to use this service in a satellite location, contact Microsoft support. |

## Current release notes

- Encrypted files aren't translated.
- Password-protected files aren't translated.
- Text on images within documents isn't translated.
- Document translation is also [available for files in OneDrive](https://learn.microsoft.com/en-us/sharepoint/onedrive-document-translation).
- On-demand translation on folders will be available in a future release.
- This service is available only for SharePoint sites - including hub sites, sites associated to a hub site, and the primary site of a site collection. Subsites aren't supported.

## Frequently asked questions

#### What are the best practices and limitations for translating documents with various formats and content types?

For answers to frequently asked questions about document translation, see [Document Translation: FAQ](https://learn.microsoft.com/en-us/azure/ai-services/translator/document-translation/faq#document-translation-faq).

#### How does translation count characters and what are the implications for character consumption in various translation methods?

For answers to frequently asked questions about character count, see [How does Translator count characters](https://learn.microsoft.com/en-us/azure/ai-services/translator/translator-faq#how-does-translator-count-characters).

#### How can I provide feedback on a translated document?

Hover over the translated file in the library, select the feedback icon, and follow the prompts. For more information, see [Give feedback on translated documents](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/translation?view=o365-worldwide#give-feedback-on-translated-documents).
