<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policyuserscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# policyUserScope resource type

Namespace: microsoft.graph

Defines the scope of a data governance policy as it applies to a specific user.

Returned from [compute protection scopes](https://learn.microsoft.com/en-us/graph/api/userprotectionscopecontainer-compute?view=graph-rest-1.0).

Inherits from [policyScopeBase](https://learn.microsoft.com/en-us/graph/api/resources/policyscopebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activities | microsoft.graph.security.userActivityTypes | Flags specifying the user activities the calling application supports or is interested. Possible values are `none`, `uploadText`, `uploadFile`, `downloadText`, `downloadFile`, `unknownFutureValue`. Required. This object is a multi-valued enumeration. |
| executionMode | microsoft.graph.security.executionMode | Policy execution mode for this user. Possible values are `evaluateInline` and `evaluateOffline`. Inherited from `policyScopeBase`. Inline evaluation requires caller to wait for API response before allowing user activity to proceed. Required. |
| locations | Collection\([microsoft.graph.policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0)\) | Locations protected for this user. Inherited from `policyScopeBase`. Required. |
| policyActions | Collection\([microsoft.graph.dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-1.0)\) | Enforcement actions applicable to this user. Inherited from `policyScopeBase`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyUserScope",
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
  ]
}
```
