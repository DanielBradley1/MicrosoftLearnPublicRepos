<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# authorizationInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identifiers that can be used to identify and authenticate a user in non-Azure AD environments. Common uses include storing identifiers for smartcard-based certificates that a user uses for access to on-premises Active Directory deployments or for federated access, and storing the Subject Alternate Name \(SAN\) that's associated with a Common Access Card \(CAC\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateUserIds | String collection | The collection of unique identifiers that can be associated with a user and can be used to bind the Microsoft Entra user to a certificate for authentication and authorization into non-Azure AD environments. The identifiers must be unique in the tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationInfo",
  "certificateUserIds": [
    "String"
  ]
}
```
