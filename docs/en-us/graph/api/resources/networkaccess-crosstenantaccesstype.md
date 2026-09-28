<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesstype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-04 -->

# crossTenantAccessType enum type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the type of cross-tenant access for a network [connection](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connection?view=graph-rest-beta) in Global Secure Access.

## Members

| Member | Description |
| :--- | :--- |
| none | No cross-tenant access. Indicates a single-tenant, non-B2B scenario. |
| b2bCollaboration | The connection involves B2B collaboration across tenants. |
| unknownFutureValue | Evolvable enumeration sentinel value. |
