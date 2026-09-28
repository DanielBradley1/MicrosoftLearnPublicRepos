<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatecatalogentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# featureUpdateCatalogEntry resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents metadata for a Windows 10 feature update that you can approve for deployment.

Windows 10 feature updates are released bi-annually and contain new features for Windows 10. Installing these updates increases the Windows 10 build number and typically results in a new servicing lifecycle and end of service date. We recommend organizations regularly deploy new feature updates as part of adopting Windows as a service.

Inherits from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| buildNumber | String | The build number of the feature update. Read-only. |
| deployableUntilDateTime | DateTimeOffset | The date on which the content is no longer available for deployment. Read-only. Inherited from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta). |
| displayName | String | The display name of the content. Read-only. Inherited from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta). |
| id | String | The unique identifier for the catalog entry. Read-only. Inherited from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta). |
| releaseDateTime | DateTimeOffset | The release date for the content. Read-only. Inherited from [softwareUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-softwareupdatecatalogentry?view=graph-rest-beta). |
| version | String | The version of the feature update. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
  "buildNumber": "String",
  "deployableUntilDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "releaseDateTime": "String (timestamp)",
  "version": "String"
}
```
