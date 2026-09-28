<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryfile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# ediscoveryFile resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Entity that represents ediscovery ReviewSet files.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-list-files?view=graph-rest-beta) | [microsoft.graph.security.ediscoveryFile](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryfile?view=graph-rest-beta) collection | Get a list of the [ediscoveryFile](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryfile?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryfile-get?view=graph-rest-beta) | [microsoft.graph.security.ediscoveryFile](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryfile?view=graph-rest-beta) | Read the properties and relationships of an [ediscoveryFile](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryfile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content stream of the original file. |
| dateTime | DateTimeOffset | The date and time the file was last modified. See dateTime values for more details. |
| extension | String | The file extension of the file such as png, msg, docx etc. |
| extractedTextContent | Stream | The extracted text from the original file. For image based files, this would be the OCR text. |
| id | String | The unique identifier for the file. |
| mediaType | String | mimeType of the file. for example: text/plain, charset=UTF-8, application/vnd.ms-outlook. |
| name | String | The name of the file. Subject of the mail for email. |
| otherProperties | microsoft.graph.security.stringValueDictionary | A list of other properties of the file like titleOfSharepointDocument, emailRecipients. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/compliance/document-metadata-fields-in-advanced-ediscovery). |
| processingStatus | microsoft.graph.security.fileProcessingStatus | The processing status after the item was added to a review set. The possible values are: `success`, `internalError`, `unknownError`, `processingTimeout`, `invalidFileId`, `fileSizeIsZero`, `fileSizeIsTooLarge`, `fileDepthLimitExceeded`, `fileBodyIsTooLong`, `fileTypeIsUnknown`, `fileTypeIsNotSupported`, `malformedFile`, `protectedFile`, `poisonFile`, `noReviewSetSummaryGenerated`, `extractionException`, `ocrProcessingTimeout`, `ocrFileSizeExceedsLimit`. |
| senderAuthor | String collection | The sender of the email or authors of the document. |
| size | Int64 | size of the file. |
| sourceType | microsoft.graph.security.sourceType | The original source of the content. The possible values are: `mailbox`, `site`. |
| subjectTitle | String | The subject of the email or title of the document |

### fileProcessingStatus values

| Member | Description |
| :--- | --- |
| success | File was successfully processed. |
| internalError | Unhandled exception occurred during processing the file. |
| unknownError | status of processing is null or empty. |
| processingTimeout | Timeout occurred during processing. |
| invalidFileId | Failed to create a unique field ID has for the file. |
| fileSizeIsZero | File size is zero or negative. |
| fileSizeIsTooLarge | File size exceeds the limits for processing. |
| fileDepthLimitExceeded | File depth exceeded the processing limit \(30\). |
| fileBodyIsTooLong | The length of texts in the document exceeds the processing limit. |
| fileTypeIsUnknown | MimeType not supported. |
| fileTypeIsNotSupported | File format not supported. |
| malformedFile | File is malformed. |
| protectedFile | An email is rights protected or a document is encrypted. |
| poisonFile | File already processed. |
| noReviewSetSummaryGenerated | Generation of review set summary failed. |
| extractionException | Extraction of embedded documents failed. |
| ocrProcessingTimeout | Timeout while ocrProcessing of the file. |
| ocrFileSizeExceedsLimit | File size exceeds the limits for OCR processing. |

### dateTime values

| File type | Definition |
| :--- | :--- |
| Email | Sent date. |
| Email attachments | Last modified date of the document. If not available, the parent's Sent date. |
| Embedded documents | Last modified date of the document; if not available, the parent's last modified date. |
| SPO documents \(includes modern attachments\) | SharePoint Last modified date; if not available, the documents last modified date. |
| Non-Office 365 documents | Last modified date. |
| Meetings | Meeting start date. |
| VoiceMail | Sent date. |
| IM | Sent date. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| custodian | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-beta) | Custodians associated with the file. |
| tags | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-beta) collection | Tags associated with the file. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryFile",
  "id": "String (identifier)",
  "dateTime": "String (timestamp)",
  "size": "Integer",
  "name": "String",
  "sourceType": "String",
  "senderAuthor": [
    "String"
  ],
  "subjectTitle": "String",
  "extension": "String",
  "mediaType": "String",
  "content": "Stream",
  "extractedTextContent": "Stream",
  "processingStatus": "String",
  "otherProperties": {
    "@odata.type": "microsoft.graph.security.stringValueDictionary"
  }
}
```
