<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# cloudPcCloudAppDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A base type entity that represents properties of a cloud app or a discovered app. This type can be used directly or through its derived types: [cloudPcAutomaticDiscoveredAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcautomaticdiscoveredappdetail?view=graph-rest-beta) for apps automatically discovered from the *start* menu, and [cloudPcFilePathAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcfilepathappdetail?view=graph-rest-beta) for apps that an admin manually created using a file path.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| commandLineArguments | String | Specifies the command-line arguments for the cloud app. These parameters are passed to the cloud app when it's launched. The maximum allowed length for this property is 2,048 characters. For example, `-fullscreen -loop`. |
| filePath | String | Specifies the path to the executable file for the application within the OS of the hosting Cloud PC. The value should be an absolute path to a Windows or Universal app. For example, `C:\\app.exe` or `shell:AppsFolder\\appname!App`. |
| iconIndex | Int32 | Specifies the index of the icon within the file specified by the **iconPath** property. For example, if **iconPath** is set to `C:\\Program Files\\MyApp\\myapp.ico` and **iconIndex** is set to `0`, the system uses the first icon in the `myapp.ico` file. The default value is `0`. |
| iconPath | String | Specifies the path to the icon file for the application within the OS of the hosting Cloud PC. When an admin updates the path of a cloud app, the value should be a rooted absolute path. For example, `C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\powershell_ise.exe`. If this property isn't defined, a default icon is used. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcCloudAppDetail",
  "commandLineArguments": "String",
  "filePath": "String",
  "iconIndex": "Int32",
  "iconPath": "String"
}
```
