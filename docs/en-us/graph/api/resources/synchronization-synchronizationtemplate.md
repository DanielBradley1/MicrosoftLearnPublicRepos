<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# synchronizationTemplate resource type

Namespace: microsoft.graph

Provides preconfigured synchronization settings for a particular application. These settings are used by default for any [synchronization job](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) that is based on the template. The application developer specifies the template; anyone can retrieve the template to see the default settings, including the [synchronization schema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0).

You can provide multiple templates for an application, and designate a default template. If multiple templates are available for the application you're interested in, seek application-specific guidance to determine which one best meets your needs.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronization-list-templates?view=graph-rest-1.0) | [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) collection | List the templates that are available for an application or application instance \(service principal\). |
| [Get](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationtemplate-get?view=graph-rest-1.0) | [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) | Read the properties and relationships of the **synchronizationTemplate** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationtemplate-update?view=graph-rest-1.0) | [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) | Update the properties and relationships of the **synchronizationTemplate** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique template identifier. |
| applicationId | String | Identifier of the application this template belongs to. |
| default | Boolean | `true` if this template is recommended to be the default for the application. |
| description | String | Description of the template. |
| discoverable | String | `true` if this template should appear in the collection of templates available for the application instance \(service principal\). |
| factoryTag | String | One of the well-known factory tags supported by the synchronization engine. The **factoryTag** tells the synchronization engine which implementation to use when processing jobs based on this template. |
| metadata | [synchronizationMetadataEntry](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationmetadataentry?view=graph-rest-1.0) collection | Additional extension properties. Unless mentioned explicitly, metadata values should not be changed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| schema | [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) | Default synchronization schema for the jobs based on this template. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "applicationId": "String (identifier)",
  "default": true,
  "description": "String",
  "discoverable": true,
  "factoryTag": "String",
  "id": "String (identifier)",
  "metadata": [
    {
      "@odata.type": "microsoft.graph.synchronizationMetadataEntry"
    }
  ],
  "schema": {
    "@odata.type": "microsoft.graph.synchronizationSchema"
  }
}
```
