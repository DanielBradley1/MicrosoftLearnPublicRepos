<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# zebraFotaArtifact resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Describes a single artifact for a specific device model.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List zebraFotaArtifacts](https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-list?view=graph-rest-beta) | [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) collection | List properties and relationships of the [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) objects. |
| [Get zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-get?view=graph-rest-beta) | [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) | Read properties and relationships of the [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object. |
| [Create zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-create?view=graph-rest-beta) | [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) | Create a new [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object. |
| [Delete zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-delete?view=graph-rest-beta) | None | Deletes a [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta). |
| [Update zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-update?view=graph-rest-beta) | [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) | Update the properties of a [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Artifact unique ID from Zebra |
| deviceModel | String | Applicable device model \(e.g.: `TC8300`\) |
| osVersion | String | Artifact OS version \(e.g.: `8.1.0`\) |
| patchVersion | String | Artifact patch version \(e.g.: `U00`\) |
| boardSupportPackageVersion | String | The version of the Board Support Package \(BSP. E.g.: `01.18.02.00`\) |
| releaseNotesUrl | String | Artifact release notes URL \(e.g.: `https://www.zebra.com/<filename.pdf>`\) |
| description | String | Artifact description. \(e.g.: `LifeGuard Update 98 \(released 24-September-2021\) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.zebraFotaArtifact",
  "id": "String (identifier)",
  "deviceModel": "String",
  "osVersion": "String",
  "patchVersion": "String",
  "boardSupportPackageVersion": "String",
  "releaseNotesUrl": "String",
  "description": "String"
}
```
