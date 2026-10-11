<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyagentidentitysubjectreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyAgentIdentitySubjectReference resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Identifies an agent identity represented in a lifecycle policy report. Returned in the **subject** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-beta). Inherits from [microsoft.graph.identityGovernance.lifecyclePolicySubjectReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreference?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the agent identity. Inherited from [lifecyclePolicySubjectReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreference?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyAgentIdentitySubjectReference",
  "id": "String"
}
```
