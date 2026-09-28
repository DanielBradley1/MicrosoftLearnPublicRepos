<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-resourceaccessevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-25 -->

# resourceAccessEvent resource type

Namespace: microsoft.graph.security

Represents a resource access attempt made by a [user account](https://learn.microsoft.com/en-us/graph/api/resources/security-useraccount?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessDateTime | DateTimeOffset | The time of the access event. |
| accountId | String | The identifier of the user account. |
| ipAddress | String | IP address of the resource. |
| resourceIdentifier | String | The protocol and host name pairs describing the connection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.resourceAccessEvent",
  "accountId": "String",
  "resourceIdentifier": "String",
  "ipAddress": "String",
  "accessDateTime": "String (timestamp)"
}
```
