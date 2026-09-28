<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identityset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# identitySet resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Identity Set

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identity?view=graph-rest-beta) | The Identity of the Application. This property is read-only. |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identity?view=graph-rest-beta) | The Identity of the Device. This property is read-only. |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-identity?view=graph-rest-beta) | The Identity of the User. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.identitySet",
  "application": {
    "@odata.type": "microsoft.graph.identity",
    "id": "String",
    "displayName": "String"
  },
  "device": {
    "@odata.type": "microsoft.graph.identity",
    "id": "String",
    "displayName": "String"
  },
  "user": {
    "@odata.type": "microsoft.graph.identity",
    "id": "String",
    "displayName": "String"
  }
}
```
