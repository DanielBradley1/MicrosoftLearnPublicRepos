<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualendpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# virtualEndpoint resource type

Namespace: microsoft.graph

Represents a container for APIs to manage Cloud PCs.

Use the Cloud PC API to provision and manage virtual desktops for employees in an organization, or along with the [Intune API](https://learn.microsoft.com/en-us/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) to manage physical and virtual endpoints.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List auditEvents](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-auditevents?view=graph-rest-1.0) | [cloudPcAuditEvent](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditevent?view=graph-rest-1.0) collection | List properties and relationships of the [cloudPcAuditEvent](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditevent?view=graph-rest-1.0) objects. |
| [List cloudPCs](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-cloudpcs?view=graph-rest-1.0) | [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) collection | List the [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) devices in a tenant. |
| [List onPremisesConnections](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-onpremisesconnections?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) collection | List properties and relationships of the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) objects. |
| [List deviceImages](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-deviceimages?view=graph-rest-1.0) | [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) collection | List the properties and relationships of [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) objects \(operating system images\) uploaded to Cloud PC. |
| [List galleryImages](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-galleryimages?view=graph-rest-1.0) | [cloudPcGalleryImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgalleryimage?view=graph-rest-1.0) collection | List the properties and relationships of [cloudPcGalleryImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgalleryimage?view=graph-rest-1.0) objects. |
| [List provisioningPolicies](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-provisioningpolicies?view=graph-rest-1.0) | [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) collection | List properties and relationships of the [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) objects. |
| [List service plans](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-serviceplans?view=graph-rest-1.0) | [cloudPcServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0) collection | List the currently available [service plans](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0) that an organization can purchase for their Cloud PCs. |
| [List userSettings](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-usersettings?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) collection | Get a list of [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) objects and their properties. |
| [Create cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-deviceimages?view=graph-rest-1.0) | [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) | Create a new [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) object. |
| [Create cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-provisioningpolicies?view=graph-rest-1.0) | [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) | Create a new [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) object. |
| [Create cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-onpremisesconnections?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) | Create a new [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object. |
| [Create cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-usersettings?view=graph-rest-1.0) | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) | Create a new [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier \(ID\) for the virtual endpoint. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| auditEvents | [cloudPcAuditEvent](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcauditevent?view=graph-rest-1.0) collection | A collection of Cloud PC audit events. |
| cloudPCs | [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0) collection | A collection of cloud-managed virtual desktops. |
| deviceImages | [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) collection | A collection of device image resources on Cloud PC. |
| galleryImages | [cloudPcGalleryImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgalleryimage?view=graph-rest-1.0) collection | A collection of gallery image resources on Cloud PC. |
| onPremisesConnections | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) collection | A defined collection of Azure resource information that can be used to establish Azure network connections for Cloud PCs. |
| provisioningPolicies | [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) collection | A collection of Cloud PC provisioning policies. |
| report | [cloudPcReport](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcreport?view=graph-rest-1.0) | Cloud PC-related reports. Read-only. |
| servicePlans | [cloudPcServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0) collection | A collection of Cloud PC service plans. |
| userSettings | [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) collection | A collection of Cloud PC user settings. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEndpoint",
  "id": "String (identifier)"
}
```
