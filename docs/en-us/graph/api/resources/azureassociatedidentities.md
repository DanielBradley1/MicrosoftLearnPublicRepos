<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureassociatedidentities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# azureAssociatedIdentities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

A container for the different kinds of Azure identities.

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| all | [azureIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azureidentity?view=graph-rest-beta) collection | The list of azure identities. |
| managedIdentities | [azureManagedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azuremanagedidentity?view=graph-rest-beta) collection | The list of Azure managed identities. |
| servicePrincipals | [azureServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/azureserviceprincipal?view=graph-rest-beta) collection | The list of Azure service principals. |
| users | [azureUser](https://learn.microsoft.com/en-us/graph/api/resources/azureuser?view=graph-rest-beta) collection | The list of Azure users. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureAssociatedIdentities"
}
```
