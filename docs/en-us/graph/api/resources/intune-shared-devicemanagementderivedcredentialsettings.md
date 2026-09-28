<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementDerivedCredentialSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The deviceManagementDerivedCredentialSettings resource represents a container whose contents vary according to workflow, including:

- Device configuration settings
- RA Policy

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicemanagementderivedcredentialsettings-get?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |
| [Update deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicemanagementderivedcredentialsettings-update?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Update the properties of a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |
| **Resource Access Policy** |  |  |
| [List deviceManagementDerivedCredentialSettingses](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicemanagementderivedcredentialsettings-list?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) objects. |
| [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Create a new [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |  |
| [Delete deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicemanagementderivedcredentialsettings-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the Derived Credential |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings",
  "id": "String (identifier)"
}
```
