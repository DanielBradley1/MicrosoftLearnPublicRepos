<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# cloudPcOnPremisesConnection resource type

Namespace: microsoft.graph

Represents a defined collection of Azure resource information that can be used to establish Azure network connectivity for Cloud PCs.

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-onpremisesconnections?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) collection | List properties and relationships of the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-get?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) | Read the properties and relationships of the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-onpremisesconnections?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) | Create a new [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-update?view=graph-rest-1.0) | [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) | Update the properties of a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-delete?view=graph-rest-1.0) | None | Delete a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object. You can’t delete a connection that’s in use. |
| [Run health checks](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-runhealthcheck?view=graph-rest-1.0) | None | Run health checks on the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0). |
| [Update Active Directory domain password](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-updateaddomainpassword?view=graph-rest-1.0) | None | Update the Active Directory domain password for a successful [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| adDomainName | String | The fully qualified domain name \(FQDN\) of the Active Directory domain you want to join. Maximum length is 255. Optional. |
| adDomainPassword | String | The password associated with the username of an Active Directory account \(**adDomainUsername**\). |
| adDomainUsername | String | The username of an Active Directory account \(user or service account\) that has permission to create computer objects in Active Directory. Required format: `admin@contoso.com`. Optional. |
| alternateResourceUrl | String | The interface URL of the partner service's resource that links to this Azure network connection. Requires `$select` to retrieve. |
| connectionType | [cloudPcOnPremisesConnectionType](#cloudpconpremisesconnectiontype-values) | Specifies how the provisioned Cloud PC joins to Microsoft Entra. It includes different types, one is Microsoft Entra ID join, which means there's no on-premises Active Directory \(AD\) in the current tenant, and the Cloud PC device is joined by Microsoft Entra. Another one is hybridAzureADJoin, which means there's also an on-premises Active Directory \(AD\) in the current tenant and the Cloud PC device joins to on-premises Active Directory \(AD\) and Microsoft Entra. The type also determines which types of users can be assigned and can sign into a Cloud PC. The azureADJoin type indicates that cloud-only and hybrid users can be assigned and signed into the Cloud PC. hybridAzureADJoin indicates only hybrid users can be assigned and signed into the Cloud PC. The default value is `hybridAzureADJoin`. |
| displayName | String | The display name for the Azure network connection. |
| healthCheckPaused | Boolean | Indicates whether regular health checks on the network or domain configuration are paused or active. `false` if the regular health checks on the network or domain configuration are currently active. `true` if the checks are paused. If you perform a create or update operation on a **onPremisesNetworkConnection** resource, this value is set to `false` for four weeks. If you retry a health check on network or domain configuration, this value is set to `false` for two weeks. If the **onPremisesNetworkConnection** resource is attached in a **provisioningPolicy** or used by a Cloud PC in the past four weeks, `healthCheckPaused` is set to `false`. Read-only. Default is `false`. |
| healthCheckStatus | [cloudPcOnPremisesConnectionStatus](#cloudpconpremisesconnectionstatus-values) | The status of the most recent health check done on the on-premises connection. For example, if the status is `passed`, the on-premises connection passed all checks run by the service. Possible values: `pending`, `running`, `passed`, `failed`, `warning`, `informational`. Default is `pending`. Read-only. |
| healthCheckStatusDetail | [cloudPcOnPremisesConnectionStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionstatusdetail?view=graph-rest-1.0) | Indicates the results of health checks performed on the on-premises connection. Read-only. Requires `$select` to retrieve. For an example that shows how to get the **inUse** property, see [Example 2: Get the selected properties of an Azure network connection, including healthCheckStatusDetail](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-get?view=graph-rest-1.0). Read-only. |
| id | String | Unique identifier for the Azure network connection. Read-only. |
| inUse | Boolean | When `true`, the Azure network connection is in use. When `false`, the connection isn't in use. You can't delete a connection that’s in use. Returned only on `$select`. For an example that shows how to get the **inUse** property, see [Example 2: Get the selected properties of an Azure network connection, including healthCheckStatusDetail](https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-get?view=graph-rest-1.0). Read-only. |
| inUseByCloudPc | Boolean | Indicates whether a Cloud PC is using this on-premises network connection. `true` if at least one Cloud PC is using it. Otherwise, `false`. Read-only. Default is `false`. |
| organizationalUnit | String | The organizational unit \(OU\) in which the computer account is created. If left null, the OU configured as the default \(a well-known computer object container\) in the tenant's Active Directory domain \(OU\) is used. Optional. |
| resourceGroupId | String | The unique identifier of the target resource group used associated with the on-premises network connectivity for Cloud PCs. Required format: “/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}” |
| scopeIds | String collection | The scope IDs of the corresponding permission. Currently, it's the Intune scope tag ID. |
| subnetId | String | The unique identifier of the target subnet used associated with the on-premises network connectivity for Cloud PCs. Required format: “/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkId}/subnets/{subnetName}” |
| subscriptionId | String | The unique identifier of the Azure subscription associated with the tenant. |
| subscriptionName | String | The name of the Azure subscription is used to create an Azure network connection. Read-only. |
| virtualNetworkId | String | The unique identifier of the target virtual network used associated with the on-premises network connectivity for Cloud PCs. Required format: “/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkName}” |
| virtualNetworkLocation | String | Indicates the resource location of the target virtual network. For example, the location can be eastus2, westeurope, etc. Read-only \(computed value\). |

### cloudPcOnPremisesConnectionType values

| Member | Description |
| :--- | :--- |
| azureADJoin | Indicates Cloud PC devices are joined only to Microsoft Entra ID. |
| hybridAzureADJoin | Indicates Cloud PC devices are joined to on-premises Active Directory and registered with Microsoft Entra ID. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcOnPremisesConnectionStatus values

| Member | Description |
| :--- | :--- |
| failed | Indicates Cloud PC Azure network connection health checks are now completed, with failures. The customer's environment isn't properly configured, which leads to provisioning Cloud PC failure. The customer needs to identify the issue and resolve it using the guidance provided by the on-premises connection for provisioning successfully. |
| informational | Indicates Cloud PC Azure network connection health checks are now completed, with health check information. Health checks provide information to customers about current or associated prerequisite checks status on Cloud PC add-on features such as Single Sign-On. It doesn't affect the provisioning of our customers' Cloud PCs but intends to optimize user experience. |
| passed | Indicates Cloud PC Azure network connection health checks are completed and passed. Customer can provision their Cloud PC without any issue.​ |
| pending | Default. Indicates Cloud PC Azure network connection health check is initiated and waiting for completion. |
| running | Indicates Cloud PC Azure network connection health checks are still running. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| warning | Indicates Cloud PC Azure network connection health checks are now completed, with failures. The customer's environment is not properly configured, which leads to provisioning Cloud PC failure. The customer needs to identify the issue and resolve it using the guidance provided by the on-premises connection for provisioning successfully. |

## Relationships

None.

## JSON representation

The following example shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnection",
  "adDomainName": "String",
  "adDomainPassword": "String",
  "adDomainUsername": "String",
  "alternateResourceUrl": "String",
  "connectionType": "String",
  "displayName": "String",
  "healthCheckPaused": "Boolean",
  "healthCheckStatus": "String",
  "healthCheckStatusDetail": { "@odata.type": "microsoft.graph.cloudPcOnPremisesConnectionStatusDetail" },
  "id": "String (identifier)",
  "inUse": "Boolean",
  "inUseByCloudPc": "Boolean",
  "organizationalUnit": "String",
  "resourceGroupId": "String",
  "scopeIds": ["String"],
  "subnetId": "String",
  "subscriptionId": "String",
  "subscriptionName": "String",
  "virtualNetworkId": "String"
}
```
