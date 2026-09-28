<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkapplicationidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# teamworkApplicationIdentity resource type

Namespace: microsoft.graph

Represents an **application** in Microsoft Teams. `teamworkApplicationIdentity` is used to represent bots and outgoing webhooks @mentioned in messages.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationIdentityType | teamworkApplicationIdentityType | Type of application that is referenced. The possible values are: `aadApplication`, `bot`, `tenantBot`, `office365Connector`, `outgoingWebhook`, and `unknownFutureValue`. |
| displayName | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Display name of the application. Optional. |
| id | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). ID of the application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkApplicationIdentity",
  "id": "String (identifier)",
  "displayName": "String",
  "applicationIdentityType": "String"
}
```
