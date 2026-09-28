<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policytenantscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# policyTenantScope resource type

Namespace: microsoft.graph

Defines the scope of a data governance policy at the tenant level, including user binding information.

Returned from [compute protection scope](https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-1.0)

Inherits from [policyScopeBase](https://learn.microsoft.com/en-us/graph/api/resources/policyscopebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activities | microsoft.graph.security.userActivityTypes | Flags specifying the user activities the calling application supports or is interested. Possible values are `none`, `uploadText`, `uploadFile`, `downloadText`, `downloadFile`, `unknownFutureValue`. Required. This object is a multi-valued enumeration. |
| executionMode | microsoft.graph.security.executionMode | Policy execution mode at the tenant level. Possible values are `evaluateInline` and `evaluateOffline`. Inherited from `policyScopeBase`. Required. |
| locations | Collection\([microsoft.graph.policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0)\) | Locations protected at the tenant level. Inherited from `policyScopeBase`. Required. |
| policyActions | Collection\([microsoft.graph.dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0)\) | Enforcement actions at the tenant level. Inherited from `policyScopeBase`. Required. |
| policyScope | [microsoft.graph.policyBinding](https://learn.microsoft.com/en-us/graph/api/resources/policybinding?view=graph-rest-1.0) | Specifies the users and groups included in or excluded from this tenant-level policy scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyTenantScope",
  "activities": "String",
  "executionMode": "String",
  "locations": [
    {
      "@odata.type": "microsoft.graph.policyLocation"
    }
  ],
  "policyActions": [
    {
      "@odata.type": "microsoft.graph.dlpActionInfo"
    }
  ],
  "policyScope": {
    "@odata.type": "microsoft.graph.policyBinding"
  }
}
```
