<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# inferenceClassification resource type

Namespace: microsoft.graph

Classification of a user's messages to enable focus on those that are more relevant or important to the user.

For more information, see [Manage Focused Inbox](https://learn.microsoft.com/en-us/graph/api/resources/manage-focused-inbox?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create Override](https://learn.microsoft.com/en-us/graph/api/inferenceclassification-post-overrides?view=graph-rest-1.0) | [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) | Create an override for a sender identified by an SMTP address. Future messages from that SMTP address will be consistently classified as specified in the override. |
| [List Overrides](https://learn.microsoft.com/en-us/graph/api/inferenceclassification-list-overrides?view=graph-rest-1.0) | [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) collection | Get the overrides that a user has set up to always classify messages from certain senders in specific ways. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| overrides | [inferenceClassificationOverride](https://learn.microsoft.com/en-us/graph/api/resources/inferenceclassificationoverride?view=graph-rest-1.0) collection | A set of overrides for a user to always classify messages from specific senders in certain ways: `focused`, or `other`. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)"
}
```
