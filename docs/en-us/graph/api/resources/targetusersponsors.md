<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetusersponsors?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-05 -->

# targetUserSponsors resource type

Namespace: microsoft.graph

Identifies a relationship to another user in the tenant who can approve. Used in the approval settings of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). This resource is a subtype of [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0), in which the `@odata.type` value `#microsoft.graph.targetUserSponsors` indicates that a requesting user's sponsors are the approvers. When creating an access package assignment policy approval stage with **targetUserSponsors**, also include another approver, such as a single user or group member, in case the requesting user doesn't have sponsors.

Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetUserSponsors",
}
```
