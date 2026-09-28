<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/initiator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# initiator resource type

Namespace: microsoft.graph

Describes who or what initiated the provisioning event. This object is configured in the **initiatedBy** property of [provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/provisioningobjectsummary?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the person or service that initiated the provisioning event. |
| id | String | Uniquely identifies the person or service that initiated the provisioning event. |
| initiatorType | initiatorType | Type of initiator. The possible values are: `user`, `application`, `system`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String",
  "initiatorType": "String"
}
```
