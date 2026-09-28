<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneragentsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# cloudPcExternalPartnerAgentSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the agent settings of external partner. This setting is used to deploy agent action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentSha256 | String | The hash value of agent file by sha256 algorithm. |
| agentUrl | String | The download link url of the agent, when admin sets this url, then partner can call deploy agent API to deploy this agent to targeted Cloud PCs. The format is like this: `https://www.external-partner.com/resources/agents/exampleAgentFile.exe` |
| autoDeploymentEnabled | Boolean | Indicates whether partner agent auto deployment is enabled. When true, then the partner agent will be deployed after the Cloud PC is provisioned. When false, auto deployment isn't performed. Default value is `false` |
| installParameters | String collection | The install command parameters to run the agent install command. The format is like this: `["/p paramValue", "/quiet"]` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcExternalPartnerAgentSetting",
  "agentUrl": "String",
  "agentSha256": "String",
  "installParameters": [
    "String"
  ],
  "autoDeploymentEnabled": "Boolean"
}
```
