<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# attachment resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata and content for a file attached to a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta).

Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-list-attachments?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) collection | List attachments for a case. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-attachments?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) | Create an attachment for a case. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-update?view=graph-rest-beta) | None | Update an attachment object. |
| [Download content](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-download-content?view=graph-rest-beta) | Stream | Download the attachment content after malware scanning completes. |
| [Upload content](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-upload-content?view=graph-rest-beta) | None | Upload the attachment content in chunks. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The binary content stream for the attachment. Use the [Upload content](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-upload-content?view=graph-rest-beta) and [Download content](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-attachment-download-content?view=graph-rest-beta) methods to access it. |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| description | String | The description of the attachment. |
| displayName | String | The display name of the attachment. |
| fileExtension | String | The file extension of the attachment. The service normalizes the value to include a leading period. |
| fileSize | Int64 | The size of the attachment in bytes. The maximum file size is 100 MB. |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| origin | [microsoft.graph.security.caseManagement.attachmentOrigin](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachmentorigin?view=graph-rest-beta) | The origin reference for the attachment. |
| scanResult | [microsoft.graph.security.caseManagement.attachmentScanResult](#attachmentscanresult-values) | The service-controlled malware scan result for the attachment. Read-only. |

### attachmentScanResult values

| Member | Description |
| :--- | :--- |
| unscanned | The attachment hasn't been scanned. |
| noThreatsFound | No threats were found in the attachment. |
| malicious | The attachment was identified as malicious. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.attachment",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "displayName": "String",
  "description": "String",
  "fileSize": "Integer",
  "fileExtension": "String",
  "scanResult": "String",
  "origin": {"@odata.type": "#microsoft.graph.security.caseManagement.attachmentOrigin"},
  "content": "Stream"
}
```
