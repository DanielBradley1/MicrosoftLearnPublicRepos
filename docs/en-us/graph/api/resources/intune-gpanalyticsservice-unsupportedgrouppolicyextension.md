<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# unsupportedGroupPolicyExtension resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Unsupported Group Policy Extension.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List unsupportedGroupPolicyExtensions](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-list?view=graph-rest-beta) | [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) collection | List properties and relationships of the [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) objects. |
| [Get unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-get?view=graph-rest-beta) | [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) | Read properties and relationships of the [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object. |
| [Create unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-create?view=graph-rest-beta) | [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) | Create a new [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object. |
| [Delete unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-delete?view=graph-rest-beta) | None | Deletes a [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta). |
| [Update unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-update?view=graph-rest-beta) | [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) | Update the properties of a [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| settingScope | [groupPolicySettingScope](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingscope?view=graph-rest-beta) | Setting Scope of the unsupported extension. Possible values are: `unknown`, `device`, `user`. |
| namespaceUrl | String | Namespace Url of the unsupported extension. |
| extensionType | String | ExtensionType of the unsupported extension. |
| nodeName | String | Node name of the unsupported extension. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.unsupportedGroupPolicyExtension",
  "id": "String (identifier)",
  "settingScope": "String",
  "namespaceUrl": "String",
  "extensionType": "String",
  "nodeName": "String"
}
```
