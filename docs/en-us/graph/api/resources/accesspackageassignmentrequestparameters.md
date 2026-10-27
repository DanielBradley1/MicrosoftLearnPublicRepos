<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestparameters?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# accessPackageAssignmentRequestParameters resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), this resource represents additional parameters that can be supplied when creating an [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0). Use it to control how the request is processed, such as bypassing the approval requirement that's configured on the access package policy.

In entitlement management, this object is configured in the **parameters** property of the [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bypassApproval | Boolean | When `true`, bypasses the approval requirement configured on the access package policy for this request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestParameters",
  "bypassApproval": "Boolean"
}
```
