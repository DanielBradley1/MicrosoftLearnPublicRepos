<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-provisioningobjectworkflowsubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# provisioningObjectWorkflowSubject resource type

Namespace: microsoft.graph.identityGovernance

Represents a provisioning object as a subject for lifecycle workflow activation. Use this type when activating workflows via the [activateAndWait](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activateandwait?view=graph-rest-1.0) action for non-user provisioning subjects.

Inherits from [workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributeSetEntries | [microsoft.graph.identityGovernance.attributeSetEntry](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attributesetentry?view=graph-rest-1.0) collection | The attribute set entries representing the subject's attributes. Each entry is a key-value pair. |
| id | String | The identifier of the provisioning object subject. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.provisioningObjectWorkflowSubject",
  "id": "String",
  "attributeSetEntries": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.attributeSetEntry"
    }
  ]
}
```
