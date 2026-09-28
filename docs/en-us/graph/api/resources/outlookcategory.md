<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# outlookCategory resource type

Namespace: microsoft.graph

Represents a category by which a user can group Outlook items such as messages and events. The user defines categories in a master list, and can apply one or more of these user-defined categories to an item.

Using the REST API, you can [create](https://learn.microsoft.com/en-us/graph/api/outlookuser-post-mastercategories?view=graph-rest-1.0) and define categories in the master list of categories for a user. You can also [get this master list of categories](https://learn.microsoft.com/en-us/graph/api/outlookuser-list-mastercategories?view=graph-rest-1.0), [get a specific category](https://learn.microsoft.com/en-us/graph/api/outlookcategory-get?view=graph-rest-1.0), [update](https://learn.microsoft.com/en-us/graph/api/outlookcategory-update?view=graph-rest-1.0) the color associated with a category, or [delete](https://learn.microsoft.com/en-us/graph/api/outlookcategory-delete?view=graph-rest-1.0) a category. You can apply a category to an item by assigning the **displayName** property of the category to the **categories** collection of the item. Resources that can be assigned categories include [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0), and [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0).

Each category is attributed by 2 properties: **displayName** and **color**. The **displayName** value must be unique in a user's master list. The **color** however does not have to be unique; multiple categories in the master list can be mapped to the same color. You can map up to 25 different colors to categories in a user's master list.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/outlookuser-list-mastercategories?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) collection | Get all the categories that have been defined for the user. |
| [Get](https://learn.microsoft.com/en-us/graph/api/outlookcategory-get?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) | Get the properties and relationships of the specified **outlookCategory** object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/outlookuser-post-mastercategories?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) | Create an **outlookCategory** object in the user's master list of categories. |
| [Update](https://learn.microsoft.com/en-us/graph/api/outlookcategory-update?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) | Update the writable property, **color**, of the specified **outlookCategory** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/outlookcategory-delete?view=graph-rest-1.0) | None | Delete the specified **outlookCategory** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | categoryColor | A pre-set color constant that characterizes a category, and that is mapped to one of 25 predefined colors. For more details, see the following note. |
| displayName | String | A unique name that identifies a category in the user's mailbox. After a category is created, the name cannot be changed. Read-only. |

> **Note** The possible values for **color** are pre-set constants such as `None`, `preset0` and `preset1`. Each pre-set constant is further mapped to a color; the actual color is dependent on the Outlook client that the categories are being displayed in. The following table shows the colors mapped to each pre-set constant for Outlook \(desktop client\).

| Pre-set constant | Color mapped to in Outlook |
| :--- | :--- |
| None | No color mapped |
| Preset0 | Red |
| Preset1 | Orange |
| Preset2 | Brown |
| Preset3 | Yellow |
| Preset4 | Green |
| Preset5 | Teal |
| Preset6 | Olive |
| Preset7 | Blue |
| Preset8 | Purple |
| Preset9 | Cranberry |
| Preset10 | Steel |
| Preset11 | DarkSteel |
| Preset12 | Gray |
| Preset13 | DarkGray |
| Preset14 | Black |
| Preset15 | DarkRed |
| Preset16 | DarkOrange |
| Preset17 | DarkBrown |
| Preset18 | DarkYellow |
| Preset19 | DarkGreen |
| Preset20 | DarkTeal |
| Preset21 | DarkOlive |
| Preset22 | DarkBlue |
| Preset23 | DarkPurple |
| Preset24 | DarkCranberry |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "String",
  "displayName": "String"
}
```
