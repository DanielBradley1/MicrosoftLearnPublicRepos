<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetagentidentitysponsorsorowners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# targetAgentIdentitySponsorsOrOwners resource type

Namespace: microsoft.graph

Defines the sponsors, or owners, of a specific agent identity.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isBackup | Boolean | Defines whether or not the listed sponsors and owners of the agent identity is not the primary sponsor or owner for an agent identity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetAgentIdentitySponsorsOrOwners",
  "isBackup": "Boolean"
}
```
