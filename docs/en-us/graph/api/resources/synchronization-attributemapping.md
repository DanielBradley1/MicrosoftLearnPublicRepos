<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemapping?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# attributeMapping resource type

Namespace: microsoft.graph

Defines how values for the given target attribute should flow during synchronization. This object is configured in the **attributeMappings** property of [objectMapping](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectmapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultValue | String | Default value to be used in case the **source** property was evaluated to `null`. Optional. |
| exportMissingReferences | Boolean | For internal use only. |
| flowBehavior | attributeFlowBehavior | Defines when this attribute should be exported to the target directory. The possible values are: `FlowWhenChanged` and `FlowAlways`. Default is `FlowWhenChanged`. |
| flowType | attributeFlowType | Defines when this attribute should be updated in the target directory. The possible values are:  <br><br><br><li><code>Always</code> (default) <br></li><br><br><li><code>ObjectAddOnly</code> - only when new object is created <br></li><br><br><li> <code>MultiValueAddOnly</code> - only when the change is adding new values to a multi-valued attribute <br></li><br><br><li> <code>ValueAddOnly</code> - If there is a current value, only flows &quot;Add&quot; operations; will not flow &quot;Remove&quot; operations  <br></li><br><br><li> <code>AttributeAddOnly</code> - Only propagates changes if no current value exists at all <br><br> <strong>Note:</strong> AD2AAD provisioning jobs don&#39;t respect the <code>flowType</code> property value.</li> |
| matchingPriority | Int32 | If higher than 0, this attribute will be used to perform an initial match of the objects between source and target directories. The synchronization engine will try to find the matching object using attribute with lowest value of matching priority first. If not found, the attribute with the next matching priority will be used, and so on a until match is found or no more matching attributes are left. Only attributes that are expected to have unique values, such as email, should be used as matching attributes. |
| source | [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) | Defines how a value should be extracted \(or transformed\) from the source object. |
| targetAttributeName | String | Name of the attribute on the target object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attributeMapping",
  "defaultValue": "String",
  "exportMissingReferences": "Boolean",
  "flowBehavior": "String",
  "flowType": "String",
  "matchingPriority": "Integer",
  "source": {
    "@odata.type": "microsoft.graph.attributeMappingSource"
  },
  "targetAttributeName": "String"
}
```
