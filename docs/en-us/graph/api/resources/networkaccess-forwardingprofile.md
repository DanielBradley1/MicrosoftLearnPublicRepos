<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# forwardingProfile resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A forwarding profile determines which types of traffic are routed through the Global Secure Access services and which ones are skipped. The handling of specific traffic is determined by the forwarding policies that are added to the forwarding profile.

Inherits from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingprofiles?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object. |
| [List forwarding profiles for branch \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-list-forwardingprofiles?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) objects for a branch and their properties. |
| [Create forwarding profile for branch \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-post-forwardingprofiles?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) | Create a [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object for a branch. |
| [Update forwarding profile for branch \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-update?view=graph-rest-beta) | None | Update the properties of a [microsoft.graph.networkaccess.forwardingProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta) object for a branch. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associations | [microsoft.graph.networkaccess.association](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-association?view=graph-rest-beta) collection | Specifies the users, groups, devices, and remote networks whose traffic is associated with the given traffic forwarding profile. |
| description | String | Profile description. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| id | String | Identifier for the profile. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Profile last modified time. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| name | String | Profile name. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| priority | Int32 | Profile priority. |
| state | microsoft.graph.networkaccess.status | Determines whether the profile is active or inactive. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). The possible values are: `enabled`, `disabled`. |
| trafficForwardingType | microsoft.graph.networkaccess.trafficForwardingType | Profile traffic type. The possible values are: `m365`, `internet`, `private`. |
| version | String | Version. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policies | [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta) collection | The collection of policies that are linked to this traffic forwarding profile. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). Supports `$expand` and a nested `$expand` to retrieve the policy. That is `/forwardingProfiles?$expand=policies($expand=policy)`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.forwardingProfile",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "state": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "trafficForwardingType": "String",
  "associations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.association"
    }
  ],
  "priority": "Integer"
}
```
