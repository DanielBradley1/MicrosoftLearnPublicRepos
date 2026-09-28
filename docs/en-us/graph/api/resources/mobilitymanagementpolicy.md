<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mobilitymanagementpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# mobilityManagementPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In Microsoft Entra ID, a mobility management policy represents an autoenrollment configuration for a mobility management \(MDM or MAM\) application. These policies are only applicable to devices based on Windows 10 OS and its derivatives such as Surface Hub and HoloLens. [Autoenrollment](https://learn.microsoft.com/en-us/windows/client-management/azure-ad-and-microsoft-intune-automatic-mdm-enrollment-in-the-new-portal) automatically enrolls Windows 10 devices into mobility management applications during [Microsoft Entra join](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join) or [Microsoft Entra register](https://learn.microsoft.com/en-us/entra/identity/devices/concept-device-registration) processes.

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesTo | policyScope | Indicates the user scope of the mobility management policy. The possible values are: `none`, `all`, `selected`. |
| complianceUrl | String | Compliance URL of the mobility management application. |
| description | String | Description of the mobility management application. |
| discoveryUrl | String | Discovery URL of the mobility management application. |
| displayName | String | Display name of the mobility management application. |
| id | String | Object Id of the mobility management application. |
| isValid | Boolean | Whether policy is valid. Invalid policies may not be updated and should be deleted. |
| termsOfUseUrl | String | Terms of Use URL of the mobility management application. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includedGroups | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) collection | Microsoft Entra groups under the scope of the mobility management application if appliesTo is `selected` |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "appliesTo": "String",
  "complianceUrl": "String",
  "description": "String",
  "discoveryUrl": "String",
  "displayName": "String",
  "isValid": "Boolean",
  "termsOfUseUrl": "String"
}
```
