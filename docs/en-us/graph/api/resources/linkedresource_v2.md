<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# linkedResource\_v2 resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

Represents an item in a partner application related to a [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta). An example is an email from where the task was created. A **linkedResource** object stores information about that source application, and lets you link back to the related item. You can see the **linkedResource** in the task details view, as shown.

![Screenshot showing linked resource card in task details pane. Linked resource card shows Open in Jira, which is the partner application name, and Social media Plan which is the title of linked resource](https://learn.microsoft.com/en-us/graph/images/todo-linkedresource-taskdetail.png)

Some **linkedResource** objects aren't associated with any web URLs, in which case, the **webUrl** property isn't required. For example, the linked item can be from a custom business app or native platform app, such as an SMS app on a mobile phone. Here's how a **linkedResource** appears with and without a URL.

![Image showing how linked resource card with and without URL is displayed. Linked resource card with URL contains Open with partner application Name while linked resource card without URL contains just partner Application name.](https://learn.microsoft.com/en-us/graph/images/todo-linkedresource.png)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/basetask-list-linkedresources?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) collection | Get a list of the [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/basetask-post-linkedresources?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) | Create a new [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/linkedresource_v2-get?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) | Read the properties and relationships of a [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/linkedresource_v2-update?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) | Update the properties of a [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/linkedresource_v2-delete?view=graph-rest-beta) | None | Deletes a [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationName | String | Field indicating the app name of the source that is sending the **linkedResource**. |
| displayName | String | Field indicating the title of the **linkedResource**. |
| externalId | String | Id of the object that is associated with this task on the third-party/partner system. |
| id | String | Server generated ID for the **linkedResource**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| webUrl | String | Deep link to the **linkedResource**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.linkedResource_v2",
  "webUrl": "String",
  "applicationName": "String",
  "displayName": "String",
  "externalId": "String",
  "id": "String (identifier)"
}
```
