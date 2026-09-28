<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcautomaticdiscoveredappdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# cloudPcAutomaticDiscoveredAppDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents properties of a [cloud app](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) that was automatically discovered from the *start* menu.

Inherits from [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| commandLineArguments | String | Specifies the command-line arguments for the cloud app. These parameters are passed to the cloud app when it's launched. The maximum allowed length for this property is 2,048 characters. For example, `-fullscreen -loop`. Inherited from [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta). |
| filePath | String | Specifies the path to the executable file for the application within the operating system of the hosting Cloud PC. The value should be an absolute path to a Windows or Universal app. For example, `C:\\app.exe` or `shell:AppsFolder\\appname!App`. Inherited from [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta). |
| iconIndex | Int32 | Specifies the index of the icon within the file specified by the **iconPath** property. The default value is `0`. Inherited from [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta). |
| iconPath | String | Specifies the path to the icon file for the application within the operating system of the hosting Cloud PC. Inherited from [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail",
  "commandLineArguments": "String",
  "filePath": "String",
  "iconIndex": "Int32",
  "iconPath": "String"
}
```
