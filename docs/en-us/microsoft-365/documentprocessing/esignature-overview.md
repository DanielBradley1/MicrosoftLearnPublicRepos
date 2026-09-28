<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Overview of eSignature

Note

Through June 2026, you can try out a [limited amount](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide#included-monthly-capacity) of eSignature by sending up to five requests at no cost if you have [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide) set up. For information and limitations, see [Try out pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/promo-syntex?view=o365-worldwide).

The eSignature service simplifies the process of signing and sharing documents, while providing the security and compliance of Microsoft 365.

With eSignature, you can quickly and securely send documents for signature to people both inside and outside of your organization. You also have a digital audit trail, which can be used to verify the authenticity of documents and transactions.

## Regional availability

The eSignature service is available worldwide \(excluding Indonesia\) via the Microsoft 365 public cloud.

## Before you begin

### Legal considerations

The eSignature service uses simple electronic signatures as defined under applicable law including, but not limited, to the Regulation \(EU\) No 910/2014 \(the eIDAS Regulation\). Determine whether this is appropriate for your needs and then read the [eSignature terms of service](https://learn.microsoft.com/en-us/legal/microsoft-365/esignature-terms-of-service).

### Licensing

Before you can use eSignature, you must first link your Azure subscription to [pay-as-you-go billing](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-azure-billing?view=o365-worldwide). Billing is based on the [type and number of transactions](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/syntex-pay-as-you-go-services?view=o365-worldwide). Before you can enable eSignature, an admin must [set up eSignature](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-setup?view=o365-worldwide) in the Microsoft 365 admin center.

### Sending a request

The eSignature service creates a sharing link in order for signers to access the document. The creator of the request must have edit and sharing permissions in order for the sharing link to be created.

### External sharing

The eSignature service enables binding agreements between parties. External parties are allowed guest access to SharePoint via Microsoft Entra ID in order to electronically sign a document. If you're requesting signatures from external recipients who are not existing guests on your tenant, you need to enable Microsoft Entra B2B integration for SharePoint and OneDrive and guest sharing. For more information, see [Set up eSignature for external recipients](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-setup?view=o365-worldwide#external-recipients). Consider whether this meets your compliance and security requirements when enabling eSignature.

### Purview integration

The eSignature service enables logging of eSignature activities in the Purview Audit log. Activities can be viewed by opening the audit log and searching for eSignature\* in the **Activities - operation names** field. The activities logged are:

- Request was created
- Request was sent
- Request was canceled
- Request was declined
- Request was completed
- Link to the signed document has expired
- Document was viewed by recipient
- Document was signed by the recipient
- Document was downloaded by recipient

## Using other signature providers

The eSignature platform is integrated with electronic signature providers Adobe Acrobat Sign and Docusign eSignature. You can initiate requests using these providers from PDF documents in SharePoint, while ensuring the secure and automatic storage of signed documents in Microsoft 365.

The providers facilitate the signing process and send out all relevant notifications. When signing is complete, a copy of the fully signed document is automatically saved in SharePoint for easy access. For more information, see [how to add signature providers](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-setup?view=o365-worldwide#add-signature-providers) and [how to create a signature request using another provider](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-send-requests?view=o365-worldwide#create-a-signature-request-using-another-provider).

## Current release notes

- Microsoft 365 eSignature now available worldwide for PDFs and Word documents.
- eSignature for Microsoft Word is available worldwide to users on the Microsoft 365 Beta, Current, and Monthly Enterprise Channels.
- Tracking of eSignature requests through the Approvals app in Microsoft Teams is available.
- Integration with Adobe Acrobat Sign and Docusign eSignature is available worldwide for PDFs.

  


[Create a signature request](https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/esignature-send-requests?view=o365-worldwide)
