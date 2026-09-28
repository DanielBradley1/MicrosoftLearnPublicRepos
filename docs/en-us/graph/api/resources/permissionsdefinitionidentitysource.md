<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionidentitysource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsDefinitionIdentitySource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

An abstract type that defines the source of an identity that's requesting permissions through Permissions Management. This is an abstract type from which the following resources are derived:

- [samlIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/samlidentitysource?view=graph-rest-beta) resource type
- [awsIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/awsidentitysource?view=graph-rest-beta) resource type
- [edIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/edidentitysource?view=graph-rest-beta) resource type
- [localIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/localidentitysource?view=graph-rest-beta) resource type

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsDefinitionIdentitySource"
}
```
