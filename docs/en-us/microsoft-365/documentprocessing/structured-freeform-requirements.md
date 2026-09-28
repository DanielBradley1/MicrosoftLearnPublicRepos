<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/structured-freeform-requirements?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-12-20 -->

# Requirements and limitations for structured and freeform document processing in SharePoint

The following sections outline key factors to consider when planning to use a structured or freeform document processing model.

This service is available only for SharePoint sites - including hub sites, sites associated to a hub site, and the primary site of a site collection. Subsites aren't supported.

## Structured document processing

| Icon | Description |
| --- | --- |
| ![Files symbol.](https://learn.microsoft.com/en-us/office/media/icons/files-blue.png) | **Supported file types**  <br>This model supports the following file types: see [file type requirements](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#requirements). |
| ![Conversation symbol.](https://learn.microsoft.com/en-us/office/media/icons/chat-room-conversation-blue.png) | **Supported languages**  <br>This model supports the following languages: see [Model for Fixed-template documents](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#model-for-fixed-template-documents). |
| ![Paragraph symbol.](https://learn.microsoft.com/en-us/office/media/icons/paragraph-writing-blue.png) | **OCR considerations**  <br>This model uses optical character recognition \(OCR\) technology to scan .pdf files, image files, and .tiff files. OCR processing works best on documents that meet [these requirements](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#requirements). |
| ![Bandwidth/efficiency symbol.](https://learn.microsoft.com/en-us/office/media/icons/bandwidth-efficiency-blue.png) | **Optimization tips**  <br>If your model isn't performing as you want it to, try [these steps to improve the performance of your model](https://learn.microsoft.com/en-us/ai-builder/improve-form-processing-performance). |
| ![Globe symbol.](https://learn.microsoft.com/en-us/office/media/icons/globe-internet.png) | **Multi-Geo environments**  <br>When setting up the service in a [Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo) environment, you can only configure it to use the model type in the central location. If you want to use this model type in a satellite location, contact Microsoft support. |
| ![Blocks symbol.](https://learn.microsoft.com/en-us/office/media/icons/blocks-blue.png) | **Custom Power Platform environments**  <br>If you use a custom environment \(rather than the default environment\) for Power Platform processing, there are additional setup requirements. For more information, see [Custom Power Platform environments](https://learn.microsoft.com/en-us/microsoft-365/contentunderstanding/set-up-content-understanding#custom-power-platform-environments). |
| ![Objects symbol.](https://learn.microsoft.com/en-us/office/media/icons/objects-blue.png) | **Multi-model libraries**  <br>If two or more trained models are applied to the same library, the file is classified using the model that has the highest average confidence score. The extracted entities are from the applied model only. You can have only one freeform or one structured model per library. |

## Freeform document processing

| Icon | Description |
| --- | --- |
| ![Files symbol.](https://learn.microsoft.com/en-us/office/media/icons/files-blue.png) | **Supported file types**  <br>This model supports the following file types: see [file type requirements](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#requirements). |
| ![Conversation symbol.](https://learn.microsoft.com/en-us/office/media/icons/chat-room-conversation-blue.png) | **Supported languages**  <br>This model supports the following languages: see [Model for General documents](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#model-for-general-documents). |
| ![Paragraph symbol.](https://learn.microsoft.com/en-us/office/media/icons/paragraph-writing-blue.png) | **OCR considerations**  <br>This model uses optical character recognition \(OCR\) technology to scan .pdf files, image files, and .tiff files. OCR processing works best on documents that meet [these requirements](https://learn.microsoft.com/en-us/ai-builder/form-processing-model-requirements#requirements). |
| ![Bandwidth/efficiency symbol.](https://learn.microsoft.com/en-us/office/media/icons/bandwidth-efficiency-blue.png) | **Optimization tips**  <br>If your model isn't performing as you want it to, try [these steps to improve the performance of your model](https://learn.microsoft.com/en-us/ai-builder/improve-form-processing-performance). |
| ![Globe symbol.](https://learn.microsoft.com/en-us/office/media/icons/globe-internet.png) | **Multi-Geo environments**  <br>When setting up the service in a [Microsoft 365 Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo) environment, you can only configure it to use the model type in the central location. If you want to use this model type in a satellite location, contact Microsoft support. |
| ![Blocks symbol.](https://learn.microsoft.com/en-us/office/media/icons/blocks-blue.png) | **Custom Power Platform environments**  <br>If you use a custom environment \(rather than the default environment\) for Power Platform processing, there are additional setup requirements. For more information, see [Custom Power Platform environments](https://learn.microsoft.com/en-us/microsoft-365/contentunderstanding/set-up-content-understanding#custom-power-platform-environments). |
| ![Objects symbol.](https://learn.microsoft.com/en-us/office/media/icons/objects-blue.png) | **Multi-model libraries**  <br>If two or more trained models are applied to the same library, the file is classified using the model that has the highest average confidence score. The extracted entities are from the applied model only. You can have only one freeform or one structured model per library. |
