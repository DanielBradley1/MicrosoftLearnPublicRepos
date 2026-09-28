<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementResourceAccessProfileBase resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Base Profile Type for Resource Access

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementResourceAccessProfileBases](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofilebase-list?view=graph-rest-beta) | [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) objects. |
| [Get deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofilebase-get?view=graph-rest-beta) | [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofilebase-assign?view=graph-rest-beta) | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection |  |
| [queryByPlatformType action](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofilebase-querybyplatformtype?view=graph-rest-beta) | [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile identifier |
| version | Int32 | Version of the profile |
| displayName | String | Profile display name |
| description | String | Profile description |
| creationDateTime | DateTimeOffset | DateTime profile was created |
| lastModifiedDateTime | DateTimeOffset | DateTime profile was last modified |
| roleScopeTagIds | String collection | Scope Tags |
| serverApplicabilityRules | [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta) collection | The list of Applicability Rules for a Device Configuration Profile |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementResourceAccessProfileBase",
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
      "@odata.type": "microsoft.graph.osVersionApplicabilityRule",
      "filterType": "String",
      "minOSVersion": "String",
      "maxOSVersion": "String"
    }
  ]
}
```
