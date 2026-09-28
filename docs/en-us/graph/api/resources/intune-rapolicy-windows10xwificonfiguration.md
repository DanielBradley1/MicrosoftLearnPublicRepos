<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10XWifiConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows X WifiXml configuration profile

Inherits from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10XWifiConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xwificonfiguration-list?view=graph-rest-beta) | [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) objects. |
| [Get windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xwificonfiguration-get?view=graph-rest-beta) | [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) | Read properties and relationships of the [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) object. |
| [Create windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xwificonfiguration-create?view=graph-rest-beta) | [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) | Create a new [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) object. |
| [Delete windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xwificonfiguration-delete?view=graph-rest-beta) | None | Deletes a [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta). |
| [Update windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xwificonfiguration-update?view=graph-rest-beta) | [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) | Update the properties of a [windows10XWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xwificonfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile identifier Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| version | Int32 | Version of the profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| displayName | String | Profile display name Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| description | String | Profile description Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| creationDateTime | DateTimeOffset | DateTime profile was created Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime profile was last modified Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| roleScopeTagIds | String collection | Scope Tags Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| serverApplicabilityRules | [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta) collection | The list of Applicability Rules for a Device Configuration Profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| authenticationCertificateId | Guid | ID to the Authentication Certificate |
| customXmlFileName | String | Custom Xml file name. |
| customXml | Binary | Custom XML commands that configures the VPN connection. \(UTF8 byte encoding\) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10XWifiConfiguration",
  "id": "String (identifier)",
  "version": 1024,
  "displayName": "String",
  "description": "String",
  "creationDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "serverApplicabilityRules": [
    {
      "@odata.type": "microsoft.graph.applicabilityRule",
      "filterType": "String"
    }
  ],
  "authenticationCertificateId": "Guid",
  "customXmlFileName": "String",
  "customXml": "binary"
}
```
