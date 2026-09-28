<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# endUserSettings resource type

Namespace: microsoft.graph

Represents settings that control the end user experience for access package suggestions and resource discovery in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). These settings configure how suggestions are provided to end users and what level of related people insights are shown.

Inherits from [controlConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/endusersettings-get?view=graph-rest-1.0) | [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) | Read the properties and relationships of an **endUserSettings** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/endusersettings-update?view=graph-rest-1.0) | [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) | Update the properties of an **endUserSettings** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| relatedPeopleInsightLevel | accessPackageSuggestionRelatedPeopleInsightLevel | The level of related people insights to show in access package suggestions. The possible values are: `disabled`, `count`, `countAndNames`, `unknownFutureValue`. |
| showApproverDetailsToMembers | Boolean | Indicates whether approver details are shown to end users. When `true`, approver information is visible to members. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.endUserSettings",
  "relatedPeopleInsightLevel": "String",
  "showApproverDetailsToMembers": "Boolean"
}
```
