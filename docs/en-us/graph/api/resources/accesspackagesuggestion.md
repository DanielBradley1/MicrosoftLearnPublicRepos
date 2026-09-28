<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# accessPackageSuggestion resource type

Namespace: microsoft.graph

Represents a suggested access package with associated suggestion reasons in [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). Access packages are suggested to end users based on various criteria such as related people insights and assignment history.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accesspackagesuggestions-filterbycurrentuser?view=graph-rest-1.0) | [accessPackageSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestion?view=graph-rest-1.0) collection | Retrieve suggested access packages for the current end user based on various criteria including related people insights. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the suggested access package. Read-only. |
| reasons | Collection\([accessPackageSuggestionReason](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesuggestionreason?view=graph-rest-1.0)\) | A collection of reasons why this access package is being suggested to the user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [availableAccessPackage](https://learn.microsoft.com/en-us/graph/api/resources/availableaccesspackage?view=graph-rest-1.0) | The access package information for the suggested package. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageSuggestion",
  "id": "String",
  "reasons": [
    {
      "@odata.type": "microsoft.graph.accessPackageSuggestionReason"
    }
  ],
  "accessPackage": {
    "@odata.type": "microsoft.graph.availableAccessPackage"
  }
}
```
