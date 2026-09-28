<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermatchingsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# userMatchingSetting resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the rules for matching a user in a [roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) with a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object from Microsoft Entra ID.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| matchTarget | [microsoft.graph.industryData.userMatchTargetReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermatchtargetreferencevalue?view=graph-rest-beta) | The `RefUserMatchTarget` for matching a user from the source with a Microsoft Entra user object. |
| priorityOrder | Int32 | The priority order to apply when a user has multiple `RefRole` codes assigned. |
| sourceIdentifier | [microsoft.graph.industryData.identifierTypeReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-identifiertypereferencevalue?view=graph-rest-beta) | The `RefIdentifierType` that uniquely identifies a user in the source data. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| roleGroup | [microsoft.graph.industryData.roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) | The **roleGroup** that these settings apply to. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.userMatchingSetting",
  "matchTarget": {
    "@odata.type": "microsoft.graph.industryData.userMatchTargetReferenceValue"
  },
  "priorityOrder": "Int32",
  "sourceIdentifier": {
    "@odata.type": "microsoft.graph.industryData.identifierTypeReferenceValue"
  }
}
```
