<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# certificateBasedAuthConfiguration resource type

Namespace: microsoft.graph

Microsoft Entra ID authenticates you with a client certificate on a Windows, Android, or iOS device when you connect your Exchange Online account to:

- Microsoft mobile applications such as Outlook and Word
- Exchange ActiveSync \(EAS\) clients

Configuring this feature eliminates the need to enter a username and password combination into certain mail and Microsoft Office applications on your mobile device.

Certificate-based authentication configuration is provided through a collection of certificate authorities. Microsoft Entra ID uses the certificate authorities to establish a trusted certificate chain, which enables it to authenticate clients with a client certificate.

Learn more about [certificate-based authentication in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/authentication/active-directory-certificate-based-authentication-get-started).

Note

Administrators are highly recommended to configure the new scalable platform for [PKI \(Public Key Infrastructure\) based store](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0). This new PKI-based CA store supports up to 250 certificate authorities. It also allows each CA file to be as large as 8 KB. Additionally, it introduces new features such as issuer hints.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthconfiguration-list?view=graph-rest-1.0) | [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0) | List the properties of the **certificateBasedAuthConfiguration** collection. |
| [Create](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthconfiguration-post-certificatebasedauthconfiguration?view=graph-rest-1.0) | [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0) | Create a new **certificateBasedAuthConfiguration** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthconfiguration-get?view=graph-rest-1.0) | [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0) | Read the properties of a **certificateBasedAuthConfiguration** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/certificatebasedauthconfiguration-delete?view=graph-rest-1.0) | None | Delete a **certificateBasedAuthConfiguration** object. |

Note

Updating **certificateBasedAuthConfiguration** is not supported. To change a **certificateBasedAuthConfiguration**, first delete and then create a new **certificateBasedAuthConfiguration**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorities | [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-1.0) collection | Collection of certificate authorities which creates a trusted certificate chain. |
| id | String | The unique identifier of the certificate based auth configuration. Read-only. |

## Relationships

None,

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "certificateAuthorities": {"@odata.type": "collection(microsoft.graph.certificateAuthority)"},
  "id": "String (identifier)"
}
```
