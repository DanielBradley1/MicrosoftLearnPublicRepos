<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# inferenceClassificationOverride resource type

Namespace: microsoft.graph

Represents a user's override for how incoming messages from a specific sender should always be classified as.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Update Override](https://learn.microsoft.com/en-us/graph/api/inferenceclassificationoverride-update?view=graph-rest-1.0) | [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) | Change the **ClassifyAs** field of an override as specified. |
| [Delete Override](https://learn.microsoft.com/en-us/graph/api/inferenceclassificationoverride-delete?view=graph-rest-1.0) | None | Delete an override specified by its ID. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classifyAs | inferenceClassificationType | Specifies how incoming messages from a specific sender should always be classified as. The possible values are: `focused`, `other`. |
| id | string | The unique identifier of the override. Read-only. |
| senderEmailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The email address information of the sender for whom the override is created. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "classifyAs": "string",
  "id": "string (identifier)",
  "senderEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"}
}
```
