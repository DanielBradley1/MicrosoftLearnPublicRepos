<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-plugin?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# plugin resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a plugin scoped to a [workspace](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-workspace?view=graph-rest-beta) in Security Copilot. For more information, see [Plugins in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/plugin-overview).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-workspace-list-plugins?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.plugin](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-plugin?view=graph-rest-beta) collection | Get a list of the plugin objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorization | [microsoft.graph.security.securityCopilot.pluginAuth](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-pluginauth?view=graph-rest-beta) | Authorization for the plugin. |
| catalogScope | microsoft.graph.security.securityCopilot.pluginCatalogScope | Lists the scope available for the use of the plugin. The possible values are: `none`, `user`, `workspace`, `tenant`, `global`, `geoGlobal`, `userWorkspace`, `unknownFutureValue`. |
| category | microsoft.graph.security.securityCopilot.pluginCategory | Category of the plugin. The possible values are: `hidden`, `microsoft`, `microsoftConnectors`, `other`, `web`, `testing`, `plugin`, `unknownFutureValue`. |
| description | String | Brief description of the plugin. |
| displayName | String | Display name of the plugin.  <br>  <br>Supports `$filter` \(`eq`\). |
| isEnabled | Boolean | Displays whether the plugin is enabled for use within the catalogScope.  <br>  <br>Supports `$filter` \(`eq`\). |
| name | String | Represents the name of the plugin. Primary key.  <br>  <br>Supports `$filter` \(`eq`, `contains`\). |
| previewState | microsoft.graph.security.securityCopilot.pluginPreviewStates | Describes the use and availability of the plugin. The possible values are: `ga`, `public`, `private`, `unknownFutureValue`. |
| settings | [microsoft.graph.security.securityCopilot.pluginSetting](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-pluginsetting?view=graph-rest-beta) collection | Settings for the plugin. |
| supportedAuthTypes | microsoft.graph.security.securityCopilot.pluginAuthTypes | Authorization types used for the plugin. The possible values are: `none`, `basic`, `aPIKey`, `oAuthAuthorizationCodeFlow`, `oAuthClientCredentialsFlow`, `aad`, `serviceHttp`, `aadDelegated`, `oAuthPasswordGrantFlow`, `unknownFutureValue`. Currently unsupported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.plugin",
  "name": "String (identifier)",
  "description": "String",
  "displayName": "String",
  "category": "String",
  "catalogScope": "String",
  "previewState": "String",
  "isEnabled": "Boolean",
  "settings": [
    {
      "@odata.type": "microsoft.graph.security.securityCopilot.pluginSetting"
    }
  ],
  "authorization": {
    "@odata.type": "microsoft.graph.security.securityCopilot.pluginAuth"
  },
  "supportedAuthTypes": "String"
}
```
