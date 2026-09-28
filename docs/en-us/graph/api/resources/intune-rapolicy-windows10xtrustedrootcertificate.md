<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10XTrustedRootCertificate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows X Trusted Root Certificate configuration profile

Inherits from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10XTrustedRootCertificates](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xtrustedrootcertificate-list?view=graph-rest-beta) | [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) collection | List properties and relationships of the [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) objects. |
| [Get windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xtrustedrootcertificate-get?view=graph-rest-beta) | [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) | Read properties and relationships of the [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) object. |
| [Create windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xtrustedrootcertificate-create?view=graph-rest-beta) | [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) | Create a new [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) object. |
| [Delete windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xtrustedrootcertificate-delete?view=graph-rest-beta) | None | Deletes a [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta). |
| [Update windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xtrustedrootcertificate-update?view=graph-rest-beta) | [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) | Update the properties of a [windows10XTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xtrustedrootcertificate?view=graph-rest-beta) object. |

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
| trustedRootCertificate | Binary | Trusted Root Certificate |
| certFileName | String | File name to display in UI. |
| destinationStore | [certificateDestinationStore](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatedestinationstore?view=graph-rest-beta) | Destination store location for the Trusted Root Certificate. Possible values are: `computerCertStoreRoot`, `computerCertStoreIntermediate`, `userCertStoreIntermediate`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10XTrustedRootCertificate",
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
  "trustedRootCertificate": "binary",
  "certFileName": "String",
  "destinationStore": "String"
}
```
