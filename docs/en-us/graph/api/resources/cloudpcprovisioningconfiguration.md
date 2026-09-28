<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# cloudPcProvisioningConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the policy-derived configuration applied to a Cloud PC during provisioning. Contains properties inherited from the provisioning policy that were applied during the most recent provisioning or reprovisioning.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainJoinType | [cloudPcDomainJoinType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoinconfiguration?view=graph-rest-beta#cloudpcdomainjointype-values) | Specifies the method by which the Cloud PC is joined to Microsoft Entra ID. The possible values are: `azureADJoin`, `hybridAzureADJoin`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningConfiguration",
  "domainJoinType": "String"
}
```
