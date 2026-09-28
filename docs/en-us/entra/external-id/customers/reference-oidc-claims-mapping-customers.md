<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/reference-oidc-claims-mapping-customers -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# OpenID Connect claims mapping

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In the OpenID Connect protocol, claims communicate information about the end user. Claims are pieces of user information that an identity provider includes in the ID token it issues for that user. The ID token contains claims about the end user. During sign-up, these claims help uniquely identify the user and provide additional profile information. The values are stored in the corresponding user attributes in your directory.

To set up claims mapping, create an identity provider \(IdP\) in your Microsoft Entra External ID tenant. The IdP configuration includes the **Claims mapping** section, where you can map standard OpenID Connect \(OIDC\) claims to the claims your identity provider provides in the ID token.

![Screenshot of the Configure OpenID Connect identity provider page in the Microsoft Entra admin center, highlighting the Claims mapping section.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/reference-oidc-claims-mapping-customers/oidc-claims-mapping.png)

## Claim and attribute mappings

Use the following table to map standard OpenID Connect claims to corresponding user flow attributes and your IdP claims.

| OIDC Standard Claim | User flow attribute | Description |
| :--- | :--- | :--- |
| sub | N/A | Subject - Identifier for the end-user at the Issuer. |
| name | Display Name | Full name in displayable form including all name parts, possibly including titles and suffixes, ordered according to the end-user's locale and preferences. |
| given\_name | First Name | Given name\(s\) or first name\(s\) of the end-user. |
| family\_name | Last Name | Surname\(s\) or family name of the end-user. |
| email \(required by default\) | Email | Preferred email address. You can [make it optional](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers#make-email-optional-for-external-identity-provider-sign-up) for external IdP sign-up scenarios. |
| email\_verified | N/A | Indicates whether the identity provider verified the end-user's email address. `true` means the identity provider took affirmative steps to ensure the email address was controlled by the end-user at the time the verification was performed. If the email claim is present, a value of `true` is required for account creation. If the email claim isn't present and [email is configured as optional](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers#make-email-optional-for-external-identity-provider-sign-up), account creation proceeds without an email address. |
| phone\_number | Phone number | The claim provides the phone number for the user. |
| phone\_number\_verified | N/A | In the received ID token, the value of this claim is true if the end-user's phone number has been verified; otherwise, false. When this claim value is true, this means that your identity provider took affirmative steps to verify the phone number. |
| street\_address | Street Address | Full mailing address, formatted for display or use on a mailing label. In the token response, this field MAY contain multiple lines, separated by newlines. Newlines can be represented either as a carriage return/line feed pair \("\\r\\n"\) or as a single line feed character \("\\n"\). |
| locality | City | City or locality. |
| region | State or Province | State, province, prefecture, or region. |
| postal\_code | ZIP or Postal Code | Zip code or postal code. |
| country | Country or Region | Country name. |

Note

For claims from the identity provider to be stored on the user object, the corresponding user flow attributes must be included in the user flow. First, map your external identity provider claims with the OIDC standard claims. Second, enable the corresponding user flow attributes in the user flow that the identity provider is attached to. If you don't want an attribute to be visible to the user during sign-up, you can [hide the attribute](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes#configure-attribute-visibility-and-editability-with-microsoft-graph) while still keeping it in the user flow so the claim value is stored.

## Review the identity provider

After you add the claims mapping, review the OIDC configuration on the **Review** tab. The **Review** tab displays the claims list and corresponding user flow attributes that you mapped to your IdP claims.

![Screenshot of the Review tab showing mapped OIDC claims and corresponding user flow attributes before saving the identity provider configuration.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/reference-oidc-claims-mapping-customers/review-oidc-config.png)
