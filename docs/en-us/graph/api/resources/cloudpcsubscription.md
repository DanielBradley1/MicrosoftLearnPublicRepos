<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsubscription?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-23 -->

# cloudPcSubscription resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the subscription information that can be used to store a snapshot or snapshots of a Cloud PC for forensic analysis.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| subscriptionId | String | Indicates the ID of the subscription. |
| subscriptionName | String | Indicates the name of the subscription. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcSubscription",
  "subscriptionId": "String",
  "subscriptionName": "String"
}
```
