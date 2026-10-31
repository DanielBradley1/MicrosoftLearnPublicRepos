<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewcatalogscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-27 -->

# accessReviewCatalogScope resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

This is the recommended API for access reviews. The previous version of the [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta&preserve-view=true) is deprecated.

Represents an entitlement management catalog as the resource scope of an [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta). Use this type in the **resourceScopes** collection of a [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-beta) object configured in the **scope** property of an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-beta).

Groups, applications, and custom data provided resources in the catalog are always reviewed. Use the **additionalCatalogResourceTypes** property to review other resource types in the same catalog, in addition to the resource types that are always reviewed.

Inherits from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalCatalogResourceTypes | [accessReviewCatalogResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessreviewcatalogresourcetype-values) | The resource types in the catalog to review, in addition to the resource types that are always reviewed. The possible values are: `none`, `accessPackage`, `unknownFutureValue`.  <br>  <br>The **additionalCatalogResourceTypes** property is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. If you omit this property, only the resource types that are always reviewed are included in the review. |
| displayName | String | The display name of the catalog. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-beta). |
| resourceId | String | The identifier of the catalog. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-beta). |
| scopeType | [accessReviewResourceScopeType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessreviewresourcescopetype-values) | The scope type. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-beta). The value is `catalog`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewCatalogScope",
  "resourceId": "String",
  "scopeType": "String",
  "displayName": "String",
  "additionalCatalogResourceTypes": "String"
}
```
