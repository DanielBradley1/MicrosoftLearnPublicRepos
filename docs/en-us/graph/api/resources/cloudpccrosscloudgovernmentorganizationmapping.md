<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cloudPcCrossCloudGovernmentOrganizationMapping resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Cloud PC organization mapping between a public and a US Government Community Cloud \(GCC\) organization.

For GCC customers, the Microsoft Entra ID for the tenant is in a public cloud, but the Microsoft Entra resources and Windows 365 Cloud PCs are in the US government cloud. Therefore, tenant mapping should be set up and maintained while updating the security and compliance requirements for the FedRAMP certification and onboarding to the US Government cloud. Tenant mapping is required for customer administrators when setting up and configuring Windows 365 and for GCC end users accessing their Windows 365 Cloud PCs.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-crosscloudgovernmentorganizationmapping?view=graph-rest-beta) | [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) | Create a new [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpccrosscloudgovernmentorganizationmapping-get?view=graph-rest-beta) | [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcCrossCloudGovernmentOrganizationMapping](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrosscloudgovernmentorganizationmapping?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The tenant ID of the GCC tenant in public cloud. |
| organizationIdsInUSGovCloud | String collection | The tenant ID in the Azure Government cloud corresponding to the GCC tenant in the public cloud. Currently, 1:1 mappings are supported, so this collection can only contain one tenant ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcCrossCloudGovernmentOrganizationMapping",
  "id": "String (identifier)",
  "organizationIdsInUSGovCloud": [
    "String"
  ]
}
```
