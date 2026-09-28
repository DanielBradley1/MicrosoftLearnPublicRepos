<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerattribute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# triggerAttribute resource type

Namespace: microsoft.graph.identityGovernance

Defines the trigger attribute, which is changed to activate a workflow using an [attributeChangeTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attributechangetrigger?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the trigger attribute that is changed to trigger an [attributeChangeTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attributechangetrigger?view=graph-rest-1.0) workflow. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.triggerAttribute",
  "name": "String"
}
```
