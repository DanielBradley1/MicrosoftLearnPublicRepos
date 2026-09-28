<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicyautopatch?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# cloudPcProvisioningPolicyAutopatch resource type

Namespace: microsoft.graph

Indicates the Windows Autopatch settings for Cloud PCs using this provisioning policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| autopatchGroupId | String | The unique identifier \(ID\) of a Windows Autopatch group. An Autopatch group is a logical container or unit that groups several Microsoft Entra groups and software update policies. Devices with the same Autopatch group ID share unified software update management. The default value is `null` that indicates that no Autopatch group is associated with the provisioning policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningPolicyAutopatch",
  "autopatchGroupId": "String (identifier)"
}
```
