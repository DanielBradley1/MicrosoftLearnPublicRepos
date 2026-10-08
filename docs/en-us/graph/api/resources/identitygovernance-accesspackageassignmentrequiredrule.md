<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-accesspackageassignmentrequiredrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# accessPackageAssignmentRequiredRule resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a lifecycle policy rule that requires a guest user to have an active access package assignment. Inherits from [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [lifecyclePolicyRule resource](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isEnabled | Boolean | Indicates whether the rule is enabled. Inherited from [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.accessPackageAssignmentRequiredRule",
  "id": "String (identifier)",
  "isEnabled": "Boolean"
}
```
