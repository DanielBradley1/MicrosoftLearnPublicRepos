<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicySubjectReference resource type

Namespace: microsoft.graph.identityGovernance

An abstract type that identifies a subject represented in lifecycle policy reporting. Returned in the **subject** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0).

This abstract type can't be instantiated directly. Its derived types are [lifecyclePolicyUserSubjectReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyusersubjectreference?view=graph-rest-1.0) and [lifecyclePolicyAgentIdentitySubjectReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyagentidentitysubjectreference?view=graph-rest-1.0). Use the `@odata.type` property to distinguish between these concrete types.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the subject. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicySubjectReference",
  "id": "String"
}
```
