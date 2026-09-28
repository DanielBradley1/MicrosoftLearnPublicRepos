<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Overview of prebuilt document processing

Note

Through June 2026, you can try out a [limited amount](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide#included-monthly-capacity) of prebuilt document processing and other selected content services at no cost if you have [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide) set up. For information and limitations, see [Try out pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide).

In addition to using [custom models](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/model-types-overview?view=o365-worldwide#custom-models), document processing offers prebuilt models that help automate information extraction from documents-no training required. These models are ready to use and designed to recognize common document types and data patterns, so you can get started quickly and scale efficiently.

Note

Microsoft respects the privacy and ownership of data you use to train and process models. None of your organization's data is used or transferred by Microsoft to train AI models, large-language models, or any other models. Your data remains securely within your organization's tenant. For more information, see [Microsoft data protection and privacy](https://www.microsoft.com/en-us/trust-center/privacy).

## Introduction to prebuilt models

Prebuilt document processing uses pretrained models that are already configured to recognize common document types and extract structured information. Instead of building a custom model from scratch, you can start with a prebuilt model and tailor it by adding fields specific to your organization's needs.

These models combine optical character recognition \(OCR\) with deep learning to identify and extract predefined text and data fields. To get started, analyze a sample file using a prebuilt model. Then, select the fields that are relevant to your scenario. If the model doesn't detect the fields you need, try analyzing a different file.

Like other models, prebuilt models are created and managed in the [content center](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-content-center?view=o365-worldwide). When you apply a model to a SharePoint document library, it links to a content type and includes columns to store the extracted information.

After publishing your model, use the content center to apply it to any SharePoint document library you have access to.

## Available prebuilt models

Currently, there are five prebuilt processing models available: [contracts](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-contract?view=o365-worldwide), [invoices](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-invoice?view=o365-worldwide), [receipts](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-receipt?view=o365-worldwide), [sensitive information](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-sensitive-info?view=o365-worldwide), and [simple document](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-simple?view=o365-worldwide).

- **[Contracts](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-contract?view=o365-worldwide).** The prebuilt *contracts processing model* analyzes and extracts key information from contract documents. The API analyzes contracts in various formats and extracts key contract information, such as client name and address, contract duration, and renewal date.
- **[Invoices](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-invoice?view=o365-worldwide).** The *invoices processing model* analyzes and extracts key information from sales invoices. The API analyzes invoices in various formats and [extracts key invoice information](https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) such as customer name, billing address, due date, and amount due.
- **[Receipts](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-receipt?view=o365-worldwide).** The *receipts processing model* analyzes and extracts key information from sales receipts. The API analyzes printed and handwritten receipts and [extracts key receipt information](https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) such as merchant name, merchant phone number, transaction date, tax, and transaction total.
- **[Sensitive information](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-sensitive-info?view=o365-worldwide).** The *sensitive information model* analyzes, detects, and extracts key information from documents. The API analyzes documents in various formats and [detects and extracts key sensitive information](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-sensitive-info-entities?view=o365-worldwide), such as personal and financial identification numbers, physical and email addresses, and phone numbers.
- **[Simple document](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-simple?view=o365-worldwide).** The *simple document processing model* offers a flexible, pretrained solution for extracting key-value pairs, selection marks, and named entities from basic structured documents. This model also supports barcodes and language detection.

Additional prebuilt models will be available in future releases.

## Requirements and limitations

For information about requirements to consider when choosing this model, see the [requirements and limitations for prebuilt document processing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-requirements?view=o365-worldwide).
