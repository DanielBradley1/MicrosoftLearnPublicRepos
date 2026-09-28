<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-syntex-model?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-04-23 -->

# Create an enterprise model for document processing

<sup>**Applies to:** ✓ All custom models \| ✓ All prebuilt models</sup>

An enterprise model is created and trained in the [content center](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-content-center?view=o365-worldwide). It can be used across multiple SharePoint sites within your organization, and it can be discovered by others to use. Whether you want to create a custom model or use a prebuilt model, you can do so from any of these places:

- From the **Models** library
- From the [content center](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-content-center?view=o365-worldwide) home page
- From any document library in a site where document processing has been activated

For this article, we start in the **Models** library. For information about the different model types, see [Overview of document processing model types](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/model-types-overview?view=o365-worldwide).

If you want to create a local model, see [Create a model on a local SharePoint site](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-local-model?view=o365-worldwide).

## Create a custom model

1. From the **Models** library, select **Create a model**.

2. On the **Options for model creation** page, select the **Custom models** tab.

   ![Screenshot showing the Custom models section on the Options for model creation page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-custom-model-options.png?view=o365-worldwide)

   Note

   These available model options are configured by your Microsoft 365 admin. All model options might not be available.

3. Select one of the following tabs to continue with the custom model you want to use.

- [Single class model](#tabpanel_1_single-class-model)
- [Freeform extraction model](#tabpanel_1_freeform-extraction-model)
- [Structured extraction model](#tabpanel_1_structured-extraction-model)

Use the **Single class model** to create an [unstructured document processing model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/document-understanding-overview?view=o365-worldwide).

1. Select **Single class model**.
2. On the **Single class model: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.
3. On the right panel of the **Create a model using a single class model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Service agreements*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create a model with the teaching method page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [train the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-classifier?view=o365-worldwide).

Use the **Freeform extraction model** to create a [freeform document processing model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/form-processing-overview?view=o365-worldwide).

1. Select **Freeform extraction model**.
2. On the **Freeform extraction model: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.
3. On the right panel of the **Create a model using the freeform extraction model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Service agreements*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create a model with the Freeform selection method page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [train the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-form-processing-model?view=o365-worldwide).

   Note

   When published, this model type is available for reuse by others who do not own the model. Currently, this model can be edited and shared for editing only by the model owner.

Use the **Structured extraction model** to create a [structured document processing model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/form-processing-overview?view=o365-worldwide).

1. Select **Structured extraction model**.
2. On the **Structured extraction model: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.
3. On the right panel of the **Create a model using the structured extraction model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Service agreements*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create a model with the structured extraction model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [train the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/create-a-form-processing-model?view=o365-worldwide).

   Note

   When published, this model type is available for reuse by others who do not own the model. Currently, this model can be edited and shared for editing only by the model owner.

## Create a prebuilt model

1. From the **Models** library, select **Create a model**.

2. On the **Options for model creation** page, select the **Prebuilt models** tab.

   ![Screenshot showing the Prebuilt models section on the Options for model creation page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/build-a-prebuilt-model-section.png?view=o365-worldwide)

3. Select one of the following tabs to continue with the prebuilt model you want to use.

- [Contract processing](#tabpanel_2_contract-processing)
- [Invoice processing](#tabpanel_2_invoice-processing)
- [Receipt processing](#tabpanel_2_receipt-processing)
- [Sensitive information processing](#tabpanel_2_sensitive-information-processing)
- [Simple document processing](#tabpanel_2_simple-document-processing)

1. Select **Contract processing model**.
2. On the **Contract processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.
3. On the right panel of the **Create a contract processing model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Service agreement*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create a contract processing model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [complete setting up the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-contract?view=o365-worldwide).

1. Select **Invoice processing model**.
2. On the **Invoice processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.
3. On the right panel of the **Create an invoice processing model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Office expenses*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create an invoice processing model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [complete setting up the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-invoice?view=o365-worldwide).

1. Select **Receipt processing model**.
2. On the **Receipt processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.
3. On the right panel of the **Create a receipt processing model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Office expenses*.
   - **Description** - Enter information about how this model will be used.

     ![Screenshot of the right panel of the Create a model to process receipts page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel.png?view=o365-worldwide)

4. Under **Advanced settings**:

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [complete setting up the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-receipt?view=o365-worldwide).

1. Select **Sensitive information processing model**.
2. On the **Sensitive information processing: Details** page, you find information about the model and can see examples of a document library looks with entities detected and entities extracted. If you want to proceed with using the model, select **Next**.

   ![Screenshot of the Sensitive information processing: Details page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-sensitive-info-details.png?view=o365-worldwide)
3. On the **Create a sensitive information processing model** page, enter the following information.

   - **Model name** - Enter the name of the model, for example *Contact numbers*.
   - **Description** - Enter information about how this model will be used.


   ![Screenshot of the right panel of the Create a sensitive information processing model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel-sensitive-info.png?view=o365-worldwide)


   Note


   Unlike other prebuilt models, there isn't an **Advanced settings** section because the options to select a content type or to apply sensitivity or retention labels aren't available for this model. If you need a model where you must specify a content type, you'll need to use a [different model type](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/model-types-overview?view=o365-worldwide). The option to apply security labels will be available in a future release of this model.

4. When you're ready to create the model, select **Create**.
5. You're now ready to [complete setting up the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-sensitive-info?view=o365-worldwide#set-up-a-sensitive-information-model).

1. Select **Simple document processing model**.
2. On the **Simple document processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.
3. On the **Create a simple document processing model** page, on right panel, enter the following information.

   - **Model name** - Enter the name of the model, for example *Service agreement*.
   - **Description** - Enter information about how this model will be used.


   ![Screenshot of the right panel of the Create a simple document processing model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-a-model-panel-simple.png?view=o365-worldwide)

4. If you want to change the content type or add compliance labels, select **Advanced settings**.

   ![Screenshot of the Advanced settings section on the Create a simple document processing model page.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/create-model-advanced-settings.png?view=o365-worldwide)

   - In the **Content type** section, choose whether to create a new content type or to use an existing one.
   - In the **Compliance** section, select the retention label or sensitivity label you want to add. If a label has been already applied to the library where the file is stored, it will be selected.

5. When you're ready to create the model, select **Create**.
6. You're now ready to [complete setting up the model](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/prebuilt-model-simple?view=o365-worldwide#step-2-upload-an-example-file-to-analyze).
