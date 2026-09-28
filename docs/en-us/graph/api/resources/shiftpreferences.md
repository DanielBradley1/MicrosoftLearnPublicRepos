<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftpreferences?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-30 -->

# shiftPreferences resource type

Namespace: microsoft.graph

Represents a user's availability to be assigned shifts in the [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/shiftpreferences-get?view=graph-rest-1.0) | [shiftPreferences](https://learn.microsoft.com/en-us/graph/api/resources/shiftpreferences?view=graph-rest-1.0) | Read the properties and relationships of a **shiftPreferences** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/shiftpreferences-put?view=graph-rest-1.0) | [shiftPreferences](https://learn.microsoft.com/en-us/graph/api/resources/shiftpreferences?view=graph-rest-1.0) | Update a **shiftPreferences** object. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| availability | [shiftAvailability](https://learn.microsoft.com/en-us/graph/api/resources/shiftavailability?view=graph-rest-1.0) collection | Availability of the user to be scheduled for work and its recurrence pattern. |
| createdDateTime | DateTimeOffset | Timestamp corresponding to when the entity was created. |
| id | String | The identifier of the entity. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the entity. |
| lastModifiedDateTime | DateTimeOffset | Timestamp corresponding to when the entity was last modified. |
| @odata.etag | String | The change key for the entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "availability": [{"@odata.type": "microsoft.graph.shiftAvailability"}]
}
```
