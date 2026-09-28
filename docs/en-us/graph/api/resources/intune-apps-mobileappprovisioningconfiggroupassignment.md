<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileAppProvisioningConfigGroupAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains the properties used to assign an App provisioning configuration to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileAppProvisioningConfigGroupAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappprovisioningconfiggroupassignment-list?view=graph-rest-beta) | [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) collection | List properties and relationships of the [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) objects. |
| [Get mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappprovisioningconfiggroupassignment-get?view=graph-rest-beta) | [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) | Read properties and relationships of the [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) object. |
| [Create mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappprovisioningconfiggroupassignment-create?view=graph-rest-beta) | [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) | Create a new [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) object. |
| [Delete mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappprovisioningconfiggroupassignment-delete?view=graph-rest-beta) | None | Deletes a [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta). |
| [Update mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappprovisioningconfiggroupassignment-update?view=graph-rest-beta) | [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) | Update the properties of a [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| targetGroupId | String | The ID of the AAD group in which the app provisioning configuration is being targeted. |
| id | String | Key of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileAppProvisioningConfigGroupAssignment",
  "targetGroupId": "String",
  "id": "String (identifier)"
}
```
