<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventspolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# authenticationEventsPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A resource that specifies the events in the authentication experience, with each event further defining the available types of listeners that can be created for the event. Events are inherent to the authentication experience; this resource isn't user configurable.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List listeners](https://learn.microsoft.com/en-us/graph/api/authenticationeventspolicy-list-onsignupstart?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) collection | Get the collection of authenticationListener resources supported by the onSignupStart event. |
| [Create listener](https://learn.microsoft.com/en-us/graph/api/authenticationeventspolicy-post-onsignupstart?view=graph-rest-beta) | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) | Create a new authenticationListener object for the onSignupStart event. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| onSignupStart | [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) collection | A list of applicable actions to be taken on sign-up. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationEventsPolicy",
  "id": "String (identifier)"
}
```
