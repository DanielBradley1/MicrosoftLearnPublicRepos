<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-groupbasedsubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-20 -->

# groupBasedSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Defines the group that is the scope of a lifecycle workflow [membershipChangeTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-membershipchangetrigger?view=graph-rest-1.0) configuration.

Inherits from [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groups | [microsoft.graph.group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | The specific group a user is interacting with in a [membershipChangeTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-membershipchangetrigger?view=graph-rest-1.0) workflow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.groupBasedSubjectSet"
}
```
