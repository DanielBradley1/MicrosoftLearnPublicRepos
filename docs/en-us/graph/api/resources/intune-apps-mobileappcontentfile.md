<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# mobileAppContentFile resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for a single installer file that is associated with a given mobileAppContent version.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppContentFiles](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-list?view=graph-rest-1.0) | [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) collection | List properties and relationships of the [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) objects. |
| [Get mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-get?view=graph-rest-1.0) | [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) | Read properties and relationships of the [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) object. |
| [Create mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-create?view=graph-rest-1.0) | [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) | Create a new [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) object. |
| [Delete mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-delete?view=graph-rest-1.0) | None | Deletes a [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0). |
| [Update mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-update?view=graph-rest-1.0) | [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) | Update the properties of a [mobileAppContentFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfile?view=graph-rest-1.0) object. |
| [commit action](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-commit?view=graph-rest-1.0) | None | Commits a file of a given app. |
| [renewUpload action](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappcontentfile-renewupload?view=graph-rest-1.0) | None | Renews the SAS URI for an application file upload. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureStorageUri | String | Indicates the Azure Storage URI that the file is uploaded to. Created by the service upon receiving a valid mobileAppContentFile. Read-only. This property is read-only. |
| isCommitted | Boolean | A value indicating whether the file is committed. A committed app content file has been fully uploaded and validated by the Intune service. TRUE means that app content file is committed, FALSE means that app content file is not committed. Defaults to FALSE. Read-only. This property is read-only. |
| id | String | The unique identifier for this mobileAppContentFile. This id is assigned during creation of the mobileAppContentFile. Read-only. This property is read-only. |
| createdDateTime | DateTimeOffset | Indicates created date and time associated with app content file, in ISO 8601 format. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Read-only. This property is read-only. |
| name | String | Indicates the name of the file. |
| size | Int64 | Indicates the original size of the file, in bytes. |
| sizeEncrypted | Int64 | Indicates the size of the file after encryption, in bytes. |
| sizeInBytes | Int64 | Indicates the original size of the file, in bytes. To be deprecated in February 2025, please use Size property instead. Valid values 0 to 9.22337203685478E+18 |
| sizeEncryptedInBytes | Int64 | Indicates the size of the file after encryption, in bytes. To be deprecated in February 2025, please use SizeEncrypted property instead. Valid values 0 to 9.22337203685478E+18 |
| azureStorageUriExpirationDateTime | DateTimeOffset | Indicates the date and time when the Azure storage URI expires, in ISO 8601 format. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Read-only. This property is read-only. |
| manifest | Binary | Indicates the manifest information, containing file metadata. |
| uploadState | [mobileAppContentFileUploadState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentfileuploadstate?view=graph-rest-1.0) | Indicates the state of the current upload request. The possible values are: success, transientError, error, unknown, azureStorageUriRequestSuccess, azureStorageUriRequestPending, azureStorageUriRequestFailed, azureStorageUriRequestTimedOut, azureStorageUriRenewalSuccess, azureStorageUriRenewalPending, azureStorageUriRenewalFailed, azureStorageUriRenewalTimedOut, commitFileSuccess, commitFilePending, commitFileFailed, commitFileTimedOut. Default value is success. This property is read-only. The possible values are: `success`, `transientError`, `error`, `unknown`, `azureStorageUriRequestSuccess`, `azureStorageUriRequestPending`, `azureStorageUriRequestFailed`, `azureStorageUriRequestTimedOut`, `azureStorageUriRenewalSuccess`, `azureStorageUriRenewalPending`, `azureStorageUriRenewalFailed`, `azureStorageUriRenewalTimedOut`, `commitFileSuccess`, `commitFilePending`, `commitFileFailed`, `commitFileTimedOut`. |
| isDependency | Boolean | Indicates whether this content file is a dependency for the main content file. TRUE means that the content file is a dependency, FALSE means that the content file is not a dependency and is the main content file. Defaults to FALSE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppContentFile",
  "azureStorageUri": "String",
  "isCommitted": true,
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "name": "String",
  "size": 1024,
  "sizeEncrypted": 1024,
  "sizeInBytes": 1024,
  "sizeEncryptedInBytes": 1024,
  "azureStorageUriExpirationDateTime": "String (timestamp)",
  "manifest": "binary",
  "uploadState": "String",
  "isDependency": true
}
```
