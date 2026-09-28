<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outlookuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# outlookUser resource type

Namespace: microsoft.graph

Represents the Outlook services available to a user.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create category](https://learn.microsoft.com/en-us/graph/api/outlookuser-post-mastercategories?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) | Create an **outlookCategory** object in the user's master list of categories. |
| [List categories](https://learn.microsoft.com/en-us/graph/api/outlookuser-list-mastercategories?view=graph-rest-1.0) | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) collection | Get all the categories that have been defined for the user. |
| [Get language choices](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedlanguages?view=graph-rest-1.0) | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0) collection | Get the list of locales and languages that is supported for the user, as configured on the user's mailbox server. |
| [Get time zone choices](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedtimezones?view=graph-rest-1.0) | [timeZoneInformation](https://learn.microsoft.com/en-us/graph/api/resources/timezoneinformation?view=graph-rest-1.0) collection | Get the list of time zones that is supported for the user, as configured on the user's mailbox server. |

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| masterCategories | [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) collection | A list of categories defined for the user. |

```json
{
}
```
