<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/internetmessageheader?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# internetMessageHeader resource type

Namespace: microsoft.graph

A key-value pair that represents an Internet message header, as defined by [RFC5322](https://www.ietf.org/rfc/rfc5322.txt), that provides details of the network path taken by a message from the sender to the recipient.

For examples of an Internet message header, see [View e-mail message headers](https://support.office.com/en-us/article/View-e-mail-message-headers-CD039382-DC6E-4264-AC74-C048563D212C#bm4).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | string | Represents the key in a key-value pair. |
| value | string | The value in a key-value pair. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "string",
  "value": "string"
}
```
