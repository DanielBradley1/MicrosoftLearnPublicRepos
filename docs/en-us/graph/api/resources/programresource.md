<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/programresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# programResource resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

The **programResource** object, contained within a [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) object, represents a reference to an object that is the target of the access review.

This type inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | String | Type of the resource, indicating whether it is a group or an app. |

## Relationships

None.

## JSON representation

```json
{
  "type": "string"
}
```
