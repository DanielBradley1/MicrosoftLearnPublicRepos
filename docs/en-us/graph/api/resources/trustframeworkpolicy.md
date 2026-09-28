<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# trustFrameworkPolicy resource type

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Represents a [Trust Framework](https://learn.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-reference-trustframeworks-defined-ief-custom) policy \(also called [custom policy](https://learn.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview-custom)\) in [Azure Active Directory B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview). A Trust Framework policy gives full control over the user journeys. Use it to:

- Customize the sign-up and sign-in experiences fully.
- Federate to any SAML, OpenID Connect, or OAuth2 identity provider.
- Integrate with other systems or user data stores by calling REST endpoints.
- Transform claims and customize tokens issued to the relying party application.

For more information, see [Custom policies in Azure Active Directory B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview-custom).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/trustframework-post-trustframeworkpolicy?view=graph-rest-beta) | trustFrameworkPolicy | Create a new trustFrameworkPolicy. |
| [Get](https://learn.microsoft.com/en-us/graph/api/trustframeworkpolicy-get?view=graph-rest-beta) | trustFrameworkPolicy | Read properties of an existing trustFrameworkPolicy. |
| [List](https://learn.microsoft.com/en-us/graph/api/trustframework-list-trustframeworkpolicies?view=graph-rest-beta) | trustFrameworkPolicy collection | List all trustFrameworkPolicies configured in a tenant. |
| [Update](https://learn.microsoft.com/en-us/graph/api/trustframework-put-trustframeworkpolicy?view=graph-rest-beta) | None | Update an existing trustFrameworkPolicy. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/trustframeworkpolicy-delete?view=graph-rest-beta) | None | Delete an existing trustFrameworkPolicy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "id": "B2C_1A_Test"
}
```

## Related content

- [trustFrameworkPolicy schema](https://learn.microsoft.com/en-us/azure/active-directory-b2c/trustframeworkpolicy) for information about the schema elements.
- [trustFrameworkPolicy.xsd](https://github.com/Azure-Samples/active-directory-b2c-custom-policy-starterpack/blob/master/TrustFrameworkPolicy_0.3.0.0.xsd)
