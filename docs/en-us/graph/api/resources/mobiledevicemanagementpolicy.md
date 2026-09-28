<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# mobileDeviceManagementPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In Microsoft Entra ID, a Mobile Device Management \(MDM\) policy defines the configuration and enforcement rules for managing devices that access corporate resources. MDM policies are designed to ensure secure, compliant, and efficient access to corporate resources across employee devices. When a device is enrolled, it automatically receives required configurations, applications, and security policies without manual IT intervention.

Inherits from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-list?view=graph-rest-beta) | [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) collection | Get a list of the [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) objects and their properties for mobile device management applications. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-get?view=graph-rest-beta) | [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) | Read the properties and relationships of a [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) object for a mobile device management application. |
| [Update](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-update?view=graph-rest-beta) | None | Update the properties of a [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) object for a mobile device management application. |
| [List included groups](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-list-includedgroups?view=graph-rest-beta) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | List included groups for a [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) object for a mobile device management application. |
| [Add group to policy](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-post-includedgroups?view=graph-rest-beta) | None | Add a group to the [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) object for a mobile device management application. |
| [Delete group from policy](https://learn.microsoft.com/en-us/graph/api/mobiledevicemanagementpolicies-delete-includedgroups?view=graph-rest-beta) | None | Delete a group from the [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy?view=graph-rest-beta) object for a mobile device management application. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesTo | policyScope | Indicates the user scope of the MDM policy. The possible values are: `none`, `all`, `selected`. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). The possible values are: `none`, `all`, `selected`, `unknownFutureValue`. |
| isMdmEnrollmentDuringRegistrationDisabled | Boolean | Controls the option if users in an automatic enrollment configuration on Microsoft Entra registered devices are prompted to MDM enroll their device in the Entra account registration flow. |
| complianceUrl | String | Compliance URL of the mobility management application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| description | String | Description of the MDM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| discoveryUrl | String | Discovery URL of the MDM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| displayName | String | Display name of the MDM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| id | String | Object Id of the MDM application. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isValid | Boolean | Whether policy is valid. Invalid policies may not be updated and should be deleted. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |
| termsOfUseUrl | String | Terms of Use URL of the MDM application. Inherited from [mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | Microsoft Entra groups under the scope of the MDM policy if appliesTo is `selected`. Inherited from [microsoft.graph.mobilityManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mobileDeviceManagementPolicy",
  "id": "String (identifier)",
  "appliesTo": "String",
  "complianceUrl": "String",
  "description": "String",
  "discoveryUrl": "String",
  "displayName": "String",
  "termsOfUseUrl": "String",
  "isValid": "Boolean",
  "isMdmEnrollmentDuringRegistrationDisabled": "Boolean"
}
```
