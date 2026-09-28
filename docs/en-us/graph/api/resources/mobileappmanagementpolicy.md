<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# mobileAppManagementPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In Microsoft Entra ID, a Mobile Application Management \(MAM\) policy defines how corporate data is protected within mobile apps, regardless of device enrollment status. These policies are enforced through Intune app protection policies, which apply to both managed \(MDM-enrolled\) and unmanaged \(personal\) devices.

Inherits from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-list?view=graph-rest-beta) | [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) collection | Get a list of the [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) objects and their properties for mobile app management applications. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-get?view=graph-rest-beta) | [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) | Read the properties and relationships of a [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) object for a mobile app management application. |
| [Update](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-update?view=graph-rest-beta) | None | Update the properties of a [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) object for a mobile app management application. |
| [List included groups](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-list-includedgroups?view=graph-rest-beta) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | List included groups for a [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) object for a mobile app management application. |
| [Add group to policy](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-post-includedgroups?view=graph-rest-beta) | None | Add a group to the [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) object for a mobile app management application. |
| [Delete group from policy](https://learn.microsoft.com/en-us/graph/api/mobileappmanagementpolicies-delete-includedgroups?view=graph-rest-beta) | None | Delete a group from the [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy?view=graph-rest-beta) object for a mobile app management application. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesTo | policyScope | Indicates the user scope of the MAM policy. The possible values are: `none`, `all`, `selected`. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). The possible values are: `none`, `all`, `selected`, `unknownFutureValue`. |
| complianceUrl | String | Compliance URL of the mobility management application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| description | String | Description of the MAM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| discoveryUrl | String | Discovery URL of the MAM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| displayName | String | Display name of the MAM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| id | String | Object Id of the MAM application. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isValid | Boolean | Whether policy is valid. Invalid policies may not be updated and should be deleted. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| termsOfUseUrl | String | Terms of Use URL of the MAM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | Microsoft Entra groups under the scope of the MAM policy if appliesTo is `selected`. Inherited from [microsoft.graph.mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppManagementPolicy",
  "id": "String (identifier)",
  "appliesTo": "String",
  "complianceUrl": "String",
  "description": "String",
  "discoveryUrl": "String",
  "displayName": "String",
  "termsOfUseUrl": "String",
  "isValid": "Boolean"
}
```
