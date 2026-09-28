<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessguestsorexternalusers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# conditionalAccessGuestsOrExternalUsers resource type

Namespace: microsoft.graph

Represents internal guests and external users in a policy scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalTenants | [conditionalAccessExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexternaltenants?view=graph-rest-1.0) | The tenant IDs of the selected types of external users. Either all B2B tenant or a collection of tenant IDs. External tenants can be specified only when the property **guestOrExternalUserTypes** isn't `null` or an empty String. |
| guestOrExternalUserTypes | conditionalAccessGuestOrExternalUserTypes | Indicates internal guests or external user types, and is a multi-valued property. The possible values are: `none`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessGuestsOrExternalUsers",
  "externalTenants": {
    "@odata.type": "microsoft.graph.conditionalAccessExternalTenants"
  },
  "guestOrExternalUserTypes": "String"
}
```
