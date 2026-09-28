<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# profile resource type \(for networkAccess\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for forwarding policies. It's an abstract type from which the [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) resource type is derived.

Inherits from [microsoft.graph.networkaccess.baseEntity](https://learn.microsoft.com/en-us/graph/api/resources/baseentity?view=graph-rest-beta).

## Methods

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description. |
| id | String | The identifier for the profile. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the profile was last modified. |
| name | String | The name of the profile. Inherited from [microsoft.graph.networkaccess.baseEntity](https://learn.microsoft.com/en-us/graph/api/resources/baseentity?view=graph-rest-beta). |
| state | microsoft.graph.networkaccess.status | the status of the profile. The possible values are: `enabled` and `disabled`. |
| version | String | Profile version. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policies | [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta) collection | The traffic forwarding policies associated with this profile. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.profile",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "state": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
