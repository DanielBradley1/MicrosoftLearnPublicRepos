<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# onPremisesPublishingProfile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Various Azure services \(for example, Microsoft Entra Connect [Passthrough Authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta), [Workday to Microsoft Entra users provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workday-inbound-tutorial), and [Application Proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) allow access to various on-premises resources from outside the corporate network.

[On-premises agents](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) \(or [connectors](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) for Application Proxy\) installed by an administrator can be configured to route requests to a particular [published resource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta). [Agent groups](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) \(or [connector groups](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) for Application Proxy\) enable an administrator to assign specific agents to serve specific published on-premises resources. Administrators can also group multiple agents together, and then assign each published resource to an agent group. The entire set of entities of the same on-premises publishing type is represented by **onPremisesPublishingProfile**.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-get?view=graph-rest-beta) | [onPremisesPublishingProfile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta) | Read the properties and relationships of an **onPremisesPublishingProfile** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onpremisespublishingprofile-update?view=graph-rest-beta) | None | Update an [onPremisesPublishingProfile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hybridAgentUpdaterConfiguration | [hybridAgentUpdaterConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hybridagentupdaterconfiguration?view=graph-rest-beta) | Represents a **hybridAgentUpdaterConfiguration** object. |
| id | String | Represents a publishing type. The possible values are: `applicationProxy`, `exchangeOnline`, `authentication`, `provisioning`, `adAdministration`. Read-only. |
| isDefaultAccessEnabled | Boolean | Specifies whether default access for app proxy is enabled or disabled. |
| isEnabled | Boolean | Represents if [Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/) is enabled for the tenant. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agentGroups | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) collection | List of existing **onPremisesAgentGroup** objects. Read-only. Nullable. |
| agents | [onPremisesAgent](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) collection | List of existing **onPremisesAgent** objects. Read-only. Nullable. |
| applicationSegments | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) collection | Represents the segment configurations that are allowed for an on-premises non-web application published through Microsoft Entra application proxy. |
| connectorGroups | [connectorGroup](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) collection | List of existing **connectorGroup** objects for applications published through Application Proxy. Read-only. Nullable. |
| connectors | [connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) collection | List of existing **connector** objects for applications published through Application Proxy. Read-only. Nullable. |
| publishedResources | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) collection | List of existing **publishedResource** objects. Read-only. Nullable. |
| sensors | [privateAccessSensor](https://learn.microsoft.com/en-us/graph/api/resources/privateaccesssensor?view=graph-rest-beta) collection | A lightweight agent installed on domain controllers that helps secure access and enforce MFA to on-premise resources. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesPublishingProfile",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "isDefaultAccessEnabled": "Boolean",
  "hybridAgentUpdaterConfiguration": {
    "@odata.type": "microsoft.graph.hybridAgentUpdaterConfiguration"
  }
}
```
