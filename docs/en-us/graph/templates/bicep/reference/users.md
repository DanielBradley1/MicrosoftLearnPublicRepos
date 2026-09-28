<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/reference/users?view=graph-bicep-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Microsoft.Graph users

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Permissions for personal Microsoft accounts cannot be used to deploy Microsoft Graph resources declared in Bicep files.

### Read existing resources only

Choose the least privileged permission from the following table to read a Microsoft.Graph/users resource using the `existing` keyword.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | User.ReadWrite, User.ReadBasic.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.Read | User.ReadWrite |
| Application | User.Read.All | User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## Resource format

To create a Microsoft.Graph/users resource, add the following Bicep to your template.

```bicep
resource symbolicname 'Microsoft.Graph/users@v1.0' existing = {
  userPrincipalName: 'string'
}
```

## Property values

### users

| Name | Description | Value |
| --- | --- | --- |
| apiVersion | The resource api version | 'v1.0' \(ReadOnly\) |
| businessPhones | The telephone numbers for the user. NOTE: Although it's a string collection, only one number can be set for this property. Read-only for users synced from the on-premises directory. | string\[\] \(ReadOnly\) |
| deletedDateTime | Date and time when this object was deleted. Always null when the object hasn't been deleted. | string \(ReadOnly\) |
| displayName | The name displayed in the address book for the user. This value is usually the combination of the user's first name, middle initial, and family name. This property is required when a user is created and it can't be cleared during updates. Maximum length is 256 characters. | string \(ReadOnly\) |
| givenName | The given name \(first name\) of the user. Maximum length is 64 characters. | string \(ReadOnly\) |
| id | The unique identifier for an entity. Read-only. | string \(ReadOnly\) |
| jobTitle | The user's job title. Maximum length is 128 characters. | string \(ReadOnly\) |
| mail | The SMTP address for the user, for example, jeff@contoso.com. Changes to this property update the user's proxyAddresses collection to include the value as an SMTP address. This property can't contain accent characters. NOTE: We don't recommend updating this property for Azure AD B2C user profiles. Use the otherMails property instead. | string \(ReadOnly\) |
| mobilePhone | The primary cellular telephone number for the user. Read-only for users synced from the on-premises directory. Maximum length is 64 characters. | string \(ReadOnly\) |
| officeLocation | The office location in the user's place of business. | string \(ReadOnly\) |
| preferredLanguage | The preferred language for the user. The preferred language format is based on RFC 4646. The name is a combination of an ISO 639 two-letter lowercase culture code associated with the language, and an ISO 3166 two-letter uppercase subculture code associated with the country or region. Example: 'en-US', or 'es-ES'. | string \(ReadOnly\) |
| surname | The user's surname \(family name or last name\). Maximum length is 64 characters. | string \(ReadOnly\) |
| type | The resource type | 'Microsoft.Graph/users' \(ReadOnly\) |
| userPrincipalName | The user principal name \(UPN\) of the user. The UPN is an Internet-style sign-in name for the user based on the Internet standard RFC 822. By convention, this value should map to the user's email name. The general format is alias@domain, where the domain must be present in the tenant's collection of verified domains. This property is required when a user is created. The verified domains for the tenant can be accessed from the verifiedDomains property of organization.NOTE: This property can't contain accent characters. Only the following characters are allowed A - Z, a - z, 0 - 9, '. - \_ ! # ^ ~. For the complete list of allowed characters, see username policies. | string \(Required\) |

## Related content

- [Microsoft Graph API reference](https://learn.microsoft.com/en-us/graph/api/resources/user)
