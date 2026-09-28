<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rankedemailaddress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# rankedEmailAddress resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a ranked email address.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | string | The email address. |
| rank | double | The rank of the email address. A rank is used as a sort key, in relation to the other returned results. A higher rank value corresponds to a more relevant result. Relevance is determined by communication, collaboration, and business relationship signals. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": "string",
  "rank": 1024
}
```
