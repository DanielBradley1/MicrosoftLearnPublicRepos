<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/document-understanding-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Overview of unstructured document processing

Note

Through June 2026, you can try out a [limited amount](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide#included-monthly-capacity) of unstructured document processing and other selected content services at no cost if you have [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide) set up. For information and limitations, see [Try out pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide).

Use the unstructured document processing model \([teaching method](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-syntex-model?view=o365-worldwide#create-a-custom-model)\) to automatically classify files and extract information. It works best for unstructured documents, such as letters or contracts.

Note

Microsoft respects the privacy and ownership of data you use to train and process models. None of your organization's data is used or transferred by Microsoft to train AI models, large-language models, or any other models. Your data remains securely within your organization's tenant. For more information, see [Microsoft data protection and privacy](https://www.microsoft.com/en-us/trust-center/privacy).

## Introduction to unstructured models

Unstructured document processing models use artificial intelligence \(AI\) to analyze and extract information from documents. These models rely on identifiable text-based on phrases or patterns-to determine both the document's classification and the data to extract.

Note

For more information about how to use document processing services and scenario examples, see [Drive adoption of document processing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/adoption-getstarted?view=o365-worldwide) and [Scenarios and use cases for document processing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/adoption-scenarios?view=o365-worldwide).

You create and manage unstructured document processing models in a SharePoint content center. When you apply a model to a SharePoint document library, it's associated with a content type that includes columns for storing extracted information. You can create a new content type or use an existing one from the SharePoint content type gallery.

Note

Read-only or sealed content types can't be updated, so they can't be used in a model.

Add [classifiers](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-classifier?view=o365-worldwide) and [extractors](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-an-extractor?view=o365-worldwide) to your unstructured document processing models to do the following actions:

- Classifiers are used to identify and classify documents that are uploaded to the document library. For example, a classifier can be "trained" to identify all *contract renewal* documents that are uploaded to the library. The contract renewal content type is defined by you when you create your classifier.
- Extractors pull information from these documents. For example, for each contract renewal document identified in your document library, columns display that show the *Service Start Date* and *Client* for each document.

Use example files to train and test your classifiers and extractors. These files help the model learn what to look for when identifying and extracting data. For example, train your contract renewal model using real contract renewal documents from your organization. You can also use these files to validate your model's accuracy.

After publishing your model, use the content center to apply it to any SharePoint document library that you have access to.

## Requirements and limitations

For information about requirements to consider when choosing this model, see the [requirements and limitations for unstructured document processing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/requirements-and-limitations?view=o365-worldwide).
