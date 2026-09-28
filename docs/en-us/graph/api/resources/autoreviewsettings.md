<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/autoreviewsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# autoReviewSettings resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

The **autoReviewSettings** resource type is used in the [accessReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsettings?view=graph-rest-beta) resource and specifies the behavior for when an access review completes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notReviewedResult | String | Possible values: `Approve`, `Deny`, or `Recommendation`. If `Recommendation`, then **accessRecommendationsEnabled** in the **accessReviewSettings** resource should also be set to `true`. If you want to have the system provide a decision even if the reviewer does not make a choice, set the **autoReviewEnabled** property in the **accessReviewSettings** resource to `true` and include an **autoReviewSettings** object with the **notReviewedResult** property. Then, when a review completes, based on the **notReviewedResult** property, the decision is recorded as either `Approve` or `Deny`. |

## Relationships

None.

## JSON representation

```json
{
  "notReviewedResult": "string"
}
```
