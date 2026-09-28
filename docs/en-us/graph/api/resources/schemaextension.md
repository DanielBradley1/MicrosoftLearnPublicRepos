<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-17 -->

# schemaExtension resource type \(schema extensions\)

Namespace: microsoft.graph

Schema extensions allow you to define a schema to extend and add strongly-typed custom data to a resource type. The custom data appears as a complex type on the extended resource. Schema extensions are supported by the following resource types:

- [user](https://learn.microsoft.com/en-us/graph/api/resources/user)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group)
- [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit)
- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)
- [device](https://learn.microsoft.com/en-us/graph/api/resources/device)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event) \(for both user and group calendars\)
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message)
- [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization)
- [post](https://learn.microsoft.com/en-us/graph/api/resources/post)

Use this resource and associated methods to manage the [schema extension definitions](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension). To manage the schema extension data on the extended resource instance, use the same REST request that you use to manage the resource instance. See the [schema extension example](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups) to learn how to add custom data to groups.

For more information about Microsoft Graph extensibility including limits for schema extensions, see [Add custom properties to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/schemaextension-post-schemaextensions?view=graph-rest-1.0) | [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0) | Create a schema extension definition and its associated schema extension property. |
| [List](https://learn.microsoft.com/en-us/graph/api/schemaextension-list?view=graph-rest-1.0) | [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0) | List the available schemaExtension definitions and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/schemaextension-get?view=graph-rest-1.0) | [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0) | Read the properties of a specific schemaExtension definition. |
| [Update](https://learn.microsoft.com/en-us/graph/api/schemaextension-update?view=graph-rest-1.0) | [schemaExtension](https://learn.microsoft.com/en-us/graph/api/resources/schemaextension?view=graph-rest-1.0) | Update a schemaExtension definition. Use this operation to update the description, status, target types, or add more properties to the schema extension definition. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/schemaextension-delete?view=graph-rest-1.0) | None | Delete a schemaExtension definition. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the schema extension. |
| id | String | The unique identifier for the schema extension definition.  <br>You can assign a value in one of two ways:<br><br>- Concatenate the name of one of your verified domains with a name for the schema extension to form a unique string in this format, {*﻿domainName*}\_{*﻿schemaName*}. As an example, `contoso_mySchema`.<br>- Provide a schema name, and let Microsoft Graph use that schema name to complete the **id** assignment in this format: ext{*﻿8-random-alphanumeric-chars*}\_{*﻿schema-name*}. An example would be `extkvbmkofy_mySchema`.<br><br>This property cannot be changed after creation. Supports `$filter` \(`eq`\). **Note:** We recommend that your **id** starts with an alphabetic letter between A-Z because query capabilities might be limited for IDs that begin with integers.  <br>  <br>Supports `$filter` \(`eq`\). |
| owner | String | The `appId` of the application that is the owner of the schema extension. The owner of the schema definition must be explicitly specified during the Create and Update operations, or it will be implied and auto-assigned by Microsoft Entra ID as follows:  <br><br><br>- In delegated access:<br><br>  - The signed-in user must be the owner of the app that calls Microsoft Graph to create the schema extension definition.<br><br><br>  - If the signed-in user isn't the owner of the calling app, they must explicitly specify the **owner** property, and assign it the **appId** of an app that they own.<br><br>- In app-only access:<br><br>  - The **owner** property isn't required in the request body. Instead, the calling app is assigned ownership of the schema extension.<br><br>  <br>So, for example, if creating a new schema extension definition using Graph Explorer, you **must** supply the owner property. Once set, this property is read-only and cannot be changed. Supports `$filter` \(`eq`\). |
| properties | [extensionSchemaProperty](https://learn.microsoft.com/en-us/graph/api/resources/extensionschemaproperty?view=graph-rest-1.0) collection | The collection of property names and types that make up the schema extension definition. |
| status | String | The lifecycle state of the schema extension. Possible states are `InDevelopment`, `Available`, and `Deprecated`. Automatically set to `InDevelopment` on creation. For more information about the possible state transitions and behaviors, see [Schema extensions lifecycle](#schema-extensions-lifecycle). Supports `$filter` \(`eq`\). |
| targetTypes | String collection | Set of Microsoft Graph types \(that can support extensions\) that the schema extension can be applied to. Select from **administrativeUnit**, **contact**, **device**, **event**, **group**, **message**, **organization**, **post**, **todoTask**, **todoTaskList**, or **user**. |

### Schema extensions lifecycle

When your app creates a schema extension definition, the app is marked as the owner of that schema extension.

The owner app can move the extension through different states of a lifecycle, using a PATCH operation on its **status** property. Depending on the current state, the owner app may be able to update or delete the extension. Any updates to a schema extension should always only be additive and non-breaking.

| State | Lifecycle state behavior |
| :--- | :--- |
| InDevelopment | - Initial state after creation. The owner app is still developing the schema extension.<br>- In this state, any app in the same directory where the owner app is registered can extend resource instances with this schema definition \(if the app has permissions to that resource\).<br>- For a multi-tenant owner app, only the instance of the owner app that's in a different directory from the home directory can extend resource instances with this schema definition \(if the app has permissions to that resource\), or read the extension data.<br>- Only the owner app can update the extension definition with additive changes.<br>- Only the owner app can delete the extension definition.<br>- The owner app can move the extension from `InDevelopment` to the `Available` state. |
| Available | - The schema extension is available for use by all apps in any tenant.<br>- After the owner app sets the extension to `Available`, any app can add custom data to instances of those resource types specified in the extension \(if the app has permissions to that resource\). The app can assign custom data when creating a new instance or updating an existing instance.<br>- Only the owner app can update the extension definition with additive changes. No app can delete the extension definition in this state.<br>- The owner app can move the schema extension from `Available` to the `Deprecated` state. |
| Deprecated | - The schema extension definition can no longer be read or modified.<br>- No app can view, update, add new properties, or delete the extension.<br>- Apps can, however, still read, update, or delete the existing extension *property values*. |

Note

Schema extension definitions \(marked as `Available`\) created by other developers from other tenants are visible to all developers \(by listing all schema extensions\). This is different from other APIs that only return tenant-specific data. On the other hand, extension data created based on schema extension definitions, is tenant-specific and can only be accessed by apps explicitly granted permission.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "id": "String (identifier)",
  "owner": "String",
  "properties": [{"@odata.type": "microsoft.graph.extensionSchemaProperty"}],
  "status": "String",
  "targetTypes": ["String"]
}
```

## Related content

- [Add custom properties to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
