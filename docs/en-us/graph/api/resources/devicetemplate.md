<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-02 -->

# deviceTemplate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents property values that are common to a set of [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) objects. The properties on the template are stamped on any **device** object that is created based on this template. This object is immutable.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/template-list-devicetemplates?view=graph-rest-beta) | [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) collection | Get a list of [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) objects registered in the directory. |
| [Create](https://learn.microsoft.com/en-us/graph/api/template-post-devicetemplates?view=graph-rest-beta) | [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) | Create a new [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) used to identify attributes and manage a group of devices with similar characteristics. |
| [Get](https://learn.microsoft.com/en-us/graph/api/devicetemplate-get?view=graph-rest-beta) | [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) | Get the properties and relationships of a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/devicetemplate-delete?view=graph-rest-beta) | None | Delete a registered [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta). |
| [List owners](https://learn.microsoft.com/en-us/graph/api/devicetemplate-list-owners?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Get a list of owners for a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object. |
| [Add owner](https://learn.microsoft.com/en-us/graph/api/devicetemplate-post-owners?view=graph-rest-beta) | None | Add a new owner to a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object. |
| [Remove owner](https://learn.microsoft.com/en-us/graph/api/devicetemplate-delete-owners?view=graph-rest-beta) | None | Remove an owner from a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object. |
| [Create device from template](https://learn.microsoft.com/en-us/graph/api/devicetemplate-createdevicefromtemplate?view=graph-rest-beta) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) | Create a new [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) from a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when this object was deleted. Always `null` when the object hasn't been deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). |
| deviceAuthority | String | A tenant-defined name for the party that's responsible for provisioning and managing devices on the Microsoft Entra tenant. For example, Tailwind Traders \(the manufacturer\) makes security cameras that are installed in customer buildings and managed by Lakeshore Retail \(the device authority\). This value is provided to the customer by the device authority \(manufacturer or reseller\). |
| id | String | The unique identifier for the object. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta). Read-only. Supports `$filter` \(`eq`, `in`\). |
| manufacturer | String | Manufacturer name. |
| model | String | Model name. |
| mutualTlsOauthConfigurationId | String | Object ID of the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta). This value isn't required if self-signed certificates are used. This value is provided to the customer by the device authority \(manufacturer or reseller\). |
| mutualTlsOauthConfigurationTenantId | String | ID \(tenant ID for device authority\) of the tenant that contains the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta). This value isn't required if self-signed certificates are used. This value is provided to the customer by the device authority \(manufacturer or reseller\). |
| operatingSystem | String | Operating system type. Supports `$filter` \(`eq`, `in`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceInstances | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) collection | Collection of **device** objects created based on this template. |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Collection of directory objects that can manage the device template and the related **deviceInstances**. Owners can be represented as [service principals](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta), [users](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-beta), or [applications](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta). An owner has full privileges over the device template and doesn't require other administrator roles to create, update, or delete devices from this template, as well as to add or remove template owners. There can be a maximum of 100 owners on a device template.  <br>  <br>Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceTemplate",
  "deletedDateTime": "String (timestamp)",
  "deviceAuthority": "String",
  "id": "String (identifier)",
  "manufacturer": "String",
  "model": "String",
  "mutualTlsOauthConfigurationId": "String",
  "mutualTlsOauthConfigurationTenantId": "String",
  "operatingSystem": "String"
}
```
