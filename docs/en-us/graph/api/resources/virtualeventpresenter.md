<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# virtualEventPresenter resource type

Namespace: microsoft.graph

Represents information about a presenter of a virtual event.

## Methods

| Method | Return Type | Description |
| --- | --- | --- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualevent-list-presenters?view=graph-rest-1.0) | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) collection | Get the list of all [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) objects of a virtual event. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualevent-post-presenters?view=graph-rest-1.0) | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) | Create a new [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventpresenter-get?view=graph-rest-1.0) | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/virtualeventpresenter-update?view=graph-rest-1.0) | [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) | Update the properties of a [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/virtualeventpresenter-delete?view=graph-rest-1.0) | None | Delete a [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| email | String | Email address of the presenter. |
| id | String | Unique identifier of the presenter. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| identity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Identity information of the presenter. The supported identities are: [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0) and [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0). |
| presenterDetails | [virtualEventPresenterDetails](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenterdetails?view=graph-rest-1.0) | Other details about the presenter. This property returns `null` when the virtual event type is [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventPresenter",
  "email": "String",
  "id": "String (identifier)",
  "identity": {"@odata.type": "microsoft.graph.identity"},
  "presenterDetails": {"@odata.type": "microsoft.graph.virtualEventPresenterDetails"}
}
```
