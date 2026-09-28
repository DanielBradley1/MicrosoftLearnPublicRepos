<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionrelatedpeoplebased?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageSuggestionRelatedPeopleBased resource type

Namespace: microsoft.graph

Represents access package suggestions that are based on related people insights in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). This suggestion type includes information about related users who may have access to similar resources, helping to provide contextual suggestions to end users.

Inherits from [accessPackageSuggestionReason](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionreason?view=graph-rest-1.0).

In entitlement management, this subtype is configured in the **reasons** property of [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| relatedPeople | Collection\([identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0)\) | A collection of identities representing people related to the current user who may have access to similar resources. This property is only populated when the tenant's endUserSettings have `relatedPeopleInsightLevel` set to `countAndNames`. This includes both the user ID and display name information. |
| relatedPeopleAssignmentCount | Int32 | The number of related people who have assignments to this access package. This count is always provided regardless of the `relatedPeopleInsightLevel` setting. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageSuggestionRelatedPeopleBased",
  "relatedPeopleAssignmentCount": "Int32",
  "relatedPeople": [
    {
      "@odata.type": "microsoft.graph.identity",
      "id": "String",
      "displayName": "String"
    }
  ]
}
```
