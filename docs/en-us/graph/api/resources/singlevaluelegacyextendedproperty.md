<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# singleValueLegacyExtendedProperty resource type

Namespace: microsoft.graph

An extended property that contains a single value.

For more information about when to use open extensions or extended properties, and how to specify extended properties, See [Extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | A supported resource instance: [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0), [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0), [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0), or [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0). Group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) and [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) aren't supported. | Create a **singleValueLegacyExtendedProperty** in a new or existing instance of a supported resource. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | One or a collection of supported resource instance \([message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0), [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0), [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0), [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0), [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0), or group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0)\), or one such instance expanded with a [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) object. | Get a resource instance with an extended property using `$expand` or `$filter`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The property ID used to identify the property. Read-only. |
| value | string | A property value. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "value": "string"
}
```
