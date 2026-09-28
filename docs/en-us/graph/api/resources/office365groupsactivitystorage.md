<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/office365groupsactivitystorage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# office365GroupsActivityStorage resource type

Namespace: microsoft.graph

## Properties

| Property | Type | Description |
| :--- | :--- | --- |
| reportRefreshDate | Date | The latest date of the content. |
| mailboxStorageUsedInBytes | Int64 | The storage used in group mailbox. |
| siteStorageUsedInBytes | Int64 | The storage used in SharePoint document library. |
| reportDate | Date | The snapshot date for Exchange and SharePoint used storage. |
| reportPeriod | String | The number of days the report covers. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "reportRefreshDate": "Date", 
  "mailboxStorageUsedInBytes": 1024, 
  "siteStorageUsedInBytes": 1024, 
  "reportDate": "Date", 
  "reportPeriod": "String"
}
```
