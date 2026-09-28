<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-18 -->

# identitySet resource type

Namespace: microsoft.graph

Represents a keyed collection of [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) resources. It is used to represent a set of identities associated with various events for an item, such as *created by* or *last modified by*.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The application associated with this action. |
| applicationInstance | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The application instance associated with this action. |
| conversation | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The team or channel associated with this action. |
| conversationIdentityType | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. Indicates whether the **conversation** property identifies a team or channel. |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The device associated with this action. |
| encrypted | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The encrypted identity associated with this action. |
| onPremises | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The on-premises identity associated with this action. |
| guest | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The guest identity associated with this action. |
| phone | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The phone number associated with this action. |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Optional. The user associated with this action. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "applicationInstance": {"@odata.type": "microsoft.graph.identity"},
  "conversation": {"@odata.type": "microsoft.graph.identity"},
  "conversationIdentityType": {"@odata.type": "microsoft.graph.identity"},
  "device": {"@odata.type": "microsoft.graph.identity"},
  "encrypted": {"@odata.type": "microsoft.graph.identity"},
  "onPremises": {"@odata.type": "microsoft.graph.identity"},
  "guest": {"@odata.type": "microsoft.graph.identity"},
  "phone": {"@odata.type": "microsoft.graph.identity"},
  "user": {"@odata.type": "microsoft.graph.identity"}
}
```

## Related content

For examples about the usage of **identitySet** resources, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
