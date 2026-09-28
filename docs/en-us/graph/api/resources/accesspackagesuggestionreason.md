<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionreason?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageSuggestionReason resource type

Namespace: microsoft.graph

Base type for **reasons** why an [access package is suggested](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) to an end user in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). This is an abstract type that is inherited by more specific suggestion reason types.

Base type of [accessPackageSuggestionRelatedPeopleBased](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionrelatedpeoplebased?view=graph-rest-1.0) and [accessPackageSuggestionSelfAssignmentHistoryBased](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionselfassignmenthistorybased?view=graph-rest-1.0).

In entitlement management, this object is configured in the **reasons** property of [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.accessPackageSuggestionReason"
}
```
