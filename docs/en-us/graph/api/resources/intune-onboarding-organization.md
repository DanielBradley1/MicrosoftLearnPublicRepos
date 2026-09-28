<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# organization resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The organization resource represents an instance of global settings and resources which operate and are provisioned at the tenant-level.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List organizations](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-organization-list?view=graph-rest-1.0) | [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) collection | List properties and relationships of the [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) objects. |
| [Get organization](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-organization-get?view=graph-rest-1.0) | [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) | Read properties and relationships of the [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) object. |
| [Update organization](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-organization-update?view=graph-rest-1.0) | [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) | Update the properties of a [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) object. |
| [setMobileDeviceManagementAuthority action](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-organization-setmobiledevicemanagementauthority?view=graph-rest-1.0) | Int32 | Set mobile device management authority |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object. |
| mobileDeviceManagementAuthority | [mdmAuthority](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mdmauthority?view=graph-rest-1.0) | Mobile device management authority. The possible values are: `unknown`, `intune`, `sccm`, `office365`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.organization",
  "id": "String (identifier)",
  "mobileDeviceManagementAuthority": "String"
}
```
