<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-27 -->

# conditionalAccessRoot resource type

Namespace: microsoft.graph

The **conditionalAccessRoot** resource is the entry point for the Conditional Access \(CA\) object model. It doesn't contain any usable properties.

For more information on Conditional Access in Microsoft Entra ID, see [What is Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview)?

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authenticationContextClassReferences | [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified authentication context class references. |
| namedLocations | [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified named locations. |
| policies | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified Conditional Access \(CA\) policies. |
| templates | [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) collection | Read-only. Nullable. Returns a collection of the specified Conditional Access templates. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessRoot"
}
```
