<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/logonuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# logonUser resource type

Namespace: microsoft.graph

Contains stateful information about the logged on user on this host

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountDomain | String | Domain of user account used to logon. |
| accountName | String | Account name of user account used to logon. |
| accountType | String | User Account type, per Windows definition. The possible values are: `unknown`, `standard`, `power`, `administrator`. |
| firstSeenDateTime | DateTimeOffset | DateTime at which the earliest logon by this user account occurred \(provider-determined period\). The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| lastSeenDateTime | DateTimeOffset | DateTime at which the latest logon by this user account occurred. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| logonId | String | User logon ID. |
| logonTypes | String collection | Collection of the logon types observed for the logged on user from when first to last seen. The possible values are: `unknown`, `interactive`, `remoteInteractive`, `network`, `batch`, `service`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accountDomain": "String",
  "accountName": "String",
  "accountType": "String",
  "firstSeenDateTime": "String (timestamp)",
  "lastSeenDateTime": "String (timestamp)",
  "logonId": "String",
  "logonTypes": ["String"]
}
```
