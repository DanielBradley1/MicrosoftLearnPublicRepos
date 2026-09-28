<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/decisionitemprincipalresourcemembership?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# decisionItemPrincipalResourceMembership resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

This is the recommended API for access reviews. The previous version of the [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta&preserve-view=true) is deprecated.

In an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-beta), the **principalResourceMembership** property provides details about the type of membership that a principal has to the associated resource. For example, the principal can have direct or indirect access to the resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| membershipType | decisionItemPrincipalResourceMembershipType | Type of membership that the principal has to the resource. Multi-valued. The possible values are: `direct`, `indirect`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.decisionItemPrincipalResourceMembership",
  "membershipType": "String"
}
```
