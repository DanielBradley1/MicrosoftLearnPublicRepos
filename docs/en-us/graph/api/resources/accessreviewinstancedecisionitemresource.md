<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# accessReviewInstanceDecisionItemResource resource type

Namespace: microsoft.graph

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0), the **resource** property identifies the resource associated with the decision item.

An [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0) object is an open type that allows other properties to be passed in and is the base type for the following resources:

- [accessReviewInstanceDecisionItemAccessPackageAssignmentPolicyResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemaccesspackageassignmentpolicyresource?view=graph-rest-1.0)
- [accessReviewInstanceDecisionItemAccessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemaccesspackageresource?view=graph-rest-1.0)
- [accessReviewInstanceDecisionItemAzureRoleResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemazureroleresource?view=graph-rest-1.0)
- [accessReviewInstanceDecisionItemCustomDataProvidedResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemcustomdataprovidedresource?view=graph-rest-1.0)
- [accessReviewInstanceDecisionItemServicePrincipalResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemserviceprincipalresource?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the resource. |
| displayName | String | Display name of the resource |
| id | String | Identifier of the resource |
| type | String | Type of resource. Types include: `Group`, `ServicePrincipal`, `DirectoryRole`, `AzureRole`, `AccessPackage`, `AccessPackageAssignmentPolicy`, and `CustomDataProvidedResource`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemResource",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "type": "String"
}
```
