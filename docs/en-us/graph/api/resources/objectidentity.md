<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/objectidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-17 -->

# objectIdentity resource type

Namespace: microsoft.graph

Represents an identity used to sign in to a user account. An identity can be provided by Microsoft, by organizations, or by social identity providers such as Facebook, Google, or Microsoft. This enables the user to sign in to the user account with any of those associated identities.

The **identities** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) resource is an **objectIdentity** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| signInType | String | Specifies the user sign-in types in your directory, such as `emailAddress`, `userName`, `federated`, or `userPrincipalName`. `federated` represents a unique identifier for a user from an issuer that can be in any format chosen by the issuer. Setting or updating a `userPrincipalName` identity updates the value of the **userPrincipalName** property on the user object. The validations performed on the `userPrincipalName` property on the user object, for example, verified domains and acceptable characters, are performed when setting or updating a `userPrincipalName` identity. Extra validation is enforced on **issuerAssignedId** when the sign-in type is set to `emailAddress` or `userName`. This property can also be set to any custom string.  <br>For more information about filtering behavior for this property, see [Filtering on the identities property of a user](#filtering). |
| issuer | String | Specifies the issuer of the identity, for example `facebook.com`. 512 character limit.  <br>  <br>For local accounts \(where **signInType** isn't `federated`\), this property is the local default domain name for the tenant, for example `contoso.com`.  <br>For guests from other Microsoft Entra organizations, this is the domain of the federated organization, for example `contoso.com`. For more information about filtering behavior for this property, see [Filtering on the identities property of a user](#filtering). |
| issuerAssignedId | String | Specifies the unique identifier assigned to the user by the issuer. 64 character limit. The combination of **issuer** and **issuerAssignedId** must be unique within the organization. Represents the sign-in name for the user, when **signInType** is set to `emailAddress` or `userName` \(also known as local accounts\).  <br>When **signInType** is set to:<br><br>- `emailAddress` \(or a custom string that starts with `emailAddress` like `emailAddress1`\), **issuerAssignedId** must be a valid email address<br>- `userName`, **issuerAssignedId** must begin with an alphabetical character or number, and can only contain alphanumeric characters and the following symbols: `-` or `_` |

### Filtering

When filtering on the **identities** property for an **issuerAssignedId**:

- Filtering on **issuer** alone is supported for the following values: `google.com`, `facebook.com`, `mail`, and `phone`.
- Filtering for entries with a **signInType** of `federated` requires a valid **issuer** and **issuerAssignedId**.
- Filtering for entries with a **signInType** of `userName` or `emailAddress` requires a valid **issuer** and **issuerAssignedId** but ignores the issuer value. This is by design.
- Filtering for entries with a **signInType** of `userPrincipalName` isn't supported. You can filter on the **userPrincipalName** property on the user object instead.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "signInType": "string",
  "issuer": "string",
  "issuerAssignedId": "string"
}
```
