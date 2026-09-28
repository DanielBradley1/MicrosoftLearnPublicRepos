<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestparameters?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# accessPackageAssignmentRequestParameters resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-beta), this resource represents additional parameters that can be supplied when creating an [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta). Use it to control how the request is processed, such as bypassing the approval requirement that's configured on the access package policy.

In entitlement management, this object is configured in the **parameters** property of the [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bypassApproval | Boolean | When `true`, bypasses the approval requirement configured on the access package policy for this request. The default value is `false`. |

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
