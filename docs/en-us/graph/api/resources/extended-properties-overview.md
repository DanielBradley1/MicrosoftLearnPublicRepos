<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-07 -->

# Outlook extended properties overview

Namespace: microsoft.graph

Extended properties allow storing custom data and specifically serve as a fallback mechanism for apps to access custom data for Outlook MAPI properties when these properties aren't already exposed in the Microsoft Graph API metadata\_. You can use extended properties REST API to store or get such custom data in the following user resources:

- [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0)
- [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0)
- [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0)
- [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0)
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0)
- [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0)

Or, in the following Microsoft 365 group resources:

- group [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- group [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0)

## Use extended properties or open extensions?

In most common scenarios, you should be able to use open extensions \(represented by [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0), formerly known as Office 365 data extensions\) to store and access custom data for resource instances in a user's mailbox. Use extended properties only if you need to access custom data for Outlook MAPI properties that aren't already exposed in the [Microsoft Graph API metadata](https://learn.microsoft.com/en-us/graph/call-api#microsoft-graph-api-metadata).

## Types of extended properties

Depending on whether you intend to store a single or multiple values \(of the same type\) in an extended property, you can create an extended property as a [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0), or [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0).

Each of these types identifies the property by its **id** and stores data in **value**.

You can use **id** to get a specific resource instance together with that extended property, or filter on a single-value extended property to get all the instances that have that property.

**Note** You can't use the REST API to get all the extended properties of a specific instance in one call.

### id formats

You can specify **id** of an extended property in one of three formats:

- As a named property, identified by the extended property type, namespace, and a string name.
- As a named property, identified by the extended property type, namespace, and a numeric identifier.
- In a proptag format, identified by the extended property type and a [MAPI property tag](https://learn.microsoft.com/en-us/office/client-developer/outlook/mapi/mapi-property-tags).

The next two tables describe these formats as applied to single and multi-value extended properties. {*type*} represents the type of the value or values of the extended property. Shown in the examples are string, integer, and arrays of these types.

**Valid id formats for single-value extended properties**

| **Format** | **Example** | **Description** |
| :--- | :--- | :--- |
| "{*type*} {*guid*} **Name** {*name*}" | `"String {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"` | Identifies a property by the namespace \(the GUID\) it belongs to, and a string name. |
| "{*type*} {*guid*} **Id** {*id*}" | `"Integer {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8012"` | Identifies a property by the namespace \(the GUID\) it belongs to, and a numeric identifier. |
| "{*type*} {*proptag*}" | `"String 0x4001"` | Identifies a predefined property by its property tag. |

**Valid id formats for multi-value extended properties**

| **Format** | **Example** | **Description** |
| :--- | :--- | :--- |
| "{*type*} {*guid*} **Name** {*name*}" | `"StringArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"` | Identifies a property by the namespace \(the GUID\) and a string name. |
| "{*type*} {*guid*} **Id** {*id*}" | `"IntegerArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8013"` | Identifies a property by the namespace \(the GUID\) and a numeric identifier. |
| "{*type*} {*proptag*}" | `"StringArray 0x4002"` | Identifies a predefined property by its property tag. |

Use either of the named property formats to define a single-value or multi-value extended property as a custom property. Among the two formats, the first one that takes a string name \(**Name**\) is the preferred format for ease of reference. Named properties have their [property identifiers](https://learn.microsoft.com/en-us/office/client-developer/outlook/mapi/mapi-property-identifier-overview) in the 0x8000-0xfffe range.

Use the proptag format to access properties predefined by MAPI, or by a client or server, and that haven't already been exposed in Microsoft Graph. These properties have property identifiers in the 0x0001-0x7fff range. Don't try to define a custom property using the proptag format.

You can find information about mapping an extended property to an existing MAPI property, such as the property identifier and GUID, in \[MS-OXPROPS\] Microsoft Corporation, ["Exchange Server Protocols Master Property List"](https://learn.microsoft.com/en-us/openspecs/exchange_server_protocols/ms-oxprops/f6ab1613-aefe-447d-a49c-18217230b148).

**Note** After you have chosen one format for the **id**, you should access that extended property by only that format.

### REST API operations

Single-value extended property operations:

- [Create an extended property in a new or existing resource instance](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0)
- [Get one or a collection of resource instances with an extended property using `$expand` or `$filter`](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0)

Multi-value extended property operations:

- [Create an extended property in a new or existing resource instance](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0)
- [Get a resource instance with an extended property using `$expand`](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0)
