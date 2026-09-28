<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# multiValueLegacyExtendedProperty resource type

Namespace: microsoft.graph

An extended property that contains a collection of values.

See [Extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information about when to use open extensions or extended properties, and how to specify extended properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | A supported resource instance: [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0), or [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0). Group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) or [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) isn't supported. | Create a **multiValueLegacyExtendedProperty** in a new or existing instance of a supported resource. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | A supported resource instance \([message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0), [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0), [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0), or group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0)\) expanded with a [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) object. | Get a resource instance with an extended property using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The property identifier. Read-only. |
| value | string collection | A collection of property values. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "value": ["string"]
}
```
