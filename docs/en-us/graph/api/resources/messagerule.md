<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# messageRule resource type

Namespace: microsoft.graph

Represents a rule that applies to messages in the Inbox of a user.

In Outlook, you can set up rules for incoming messages in the Inbox to carry out specific actions upon certain conditions.

Programmatically, you can access rules through the **messageRules** navigation property of the Inbox [folder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0). Each rule is represented by this **messageRule** resource, available rule actions are represented by the [messageRuleActions](https://learn.microsoft.com/en-us/graph/api/resources/messageruleactions?view=graph-rest-1.0) complex type, and available rule conditions and exceptions are represented by the [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) complex type.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List rules](https://learn.microsoft.com/en-us/graph/api/mailfolder-list-messagerules?view=graph-rest-1.0) | [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) collection | Get all the **messageRule** objects defined for the user's Inbox. |
| [Get rule](https://learn.microsoft.com/en-us/graph/api/messagerule-get?view=graph-rest-1.0) | [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) | Read the properties and relationships of a **messageRule** object. |
| [Create rule](https://learn.microsoft.com/en-us/graph/api/mailfolder-post-messagerules?view=graph-rest-1.0) | [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) | Create a **messageRule** object by specifying a set of conditions and actions. |
| [Update rule](https://learn.microsoft.com/en-us/graph/api/messagerule-update?view=graph-rest-1.0) | [messageRule](https://learn.microsoft.com/en-us/graph/api/resources/messagerule?view=graph-rest-1.0) | Change writable properties on a **messageRule** object and save the changes. |
| [Delete rule](https://learn.microsoft.com/en-us/graph/api/messagerule-delete?view=graph-rest-1.0) | None | Delete the specified **messageRule** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | [messageRuleActions](https://learn.microsoft.com/en-us/graph/api/resources/messageruleactions?view=graph-rest-1.0) | Actions to be taken on a message when the corresponding conditions are fulfilled. |
| conditions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Conditions that when fulfilled trigger the corresponding actions for that rule. |
| displayName | String | The display name of the rule. |
| exceptions | [messageRulePredicates](https://learn.microsoft.com/en-us/graph/api/resources/messagerulepredicates?view=graph-rest-1.0) | Exception conditions for the rule. |
| hasError | Boolean | Indicates whether the rule is in an error condition. Read-only. |
| id | String | The unique identifier of the rule. Read-only. |
| isEnabled | Boolean | Indicates whether the rule is enabled to be applied to messages. |
| isReadOnly | Boolean | Indicates if the rule is read-only and cannot be modified or deleted by the rules REST API. |
| sequence | Int32 | Indicates the order in which the rule is executed, among other rules. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "actions": {"@odata.type": "microsoft.graph.messageRuleActions"},
  "conditions": {"@odata.type": "microsoft.graph.messageRulePredicates"},
  "displayName": "String",
  "exceptions": {"@odata.type": "microsoft.graph.messageRulePredicates"},
  "hasError": "Boolean",
  "id": "String",
  "isEnabled": "Boolean",
  "isReadOnly": "Boolean",
  "sequence": "Int32"
}
```
