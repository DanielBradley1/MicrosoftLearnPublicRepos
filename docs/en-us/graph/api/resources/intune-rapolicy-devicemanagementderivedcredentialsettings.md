<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementderivedcredentialsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementDerivedCredentialSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that describes tenant level settings for derived credentials

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementDerivedCredentialSettingses](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-list?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) objects. |
| [Get deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-get?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |
| [Create deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-create?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Create a new [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |
| [Delete deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta). |
| [Update deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-update?view=graph-rest-beta) | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Update the properties of a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the Derived Credential |
| helpUrl | String | The URL that will be accessible to end users as they retrieve a derived credential using the Company Portal. |
| displayName | String | The display name for the profile. |
| issuer | [deviceManagementDerivedCredentialIssuer](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementderivedcredentialissuer?view=graph-rest-beta) | The derived credential provider to use. Possible values are: `intercede`, `entrustDatacard`, `purebred`, `xTec`. |
| notificationType | [deviceManagementDerivedCredentialNotificationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementderivedcredentialnotificationtype?view=graph-rest-beta) | The methods used to inform the end user to open Company Portal to deliver Wi-Fi, VPN, or email profiles that use certificates to the device. Possible values are: `none`, `companyPortal`, `email`. |
| renewalThresholdPercentage | Int32 | The nominal percentage of time before certificate renewal is initiated by the client. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings",
  "id": "String (identifier)",
  "helpUrl": "String",
  "displayName": "String",
  "issuer": "String",
  "notificationType": "String",
  "renewalThresholdPercentage": 1024
}
```
