<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/claims-mapping -->
<!-- Sitemap-Last-Modified: 2025-06-17 -->

# B2B collaboration user claims mapping in Microsoft Entra External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

With Microsoft Entra External ID, you can customize the claims that are issued in the SAML token for [B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b) users. When a user authenticates to the application, Microsoft Entra ID issues a SAML token to the app that contains information \(or claims\) about the user that uniquely identifies them. By default, this claim includes the user's user name, email address, first name, and family name.

In the [Microsoft Entra admin center](https://entra.microsoft.com), you can view or edit the claims that are sent in the SAML token to the application. To access the settings, browse to **Entra ID** > **Enterprise apps** > the application that's configured for single sign-on > **Single sign-on**. See the SAML token settings in the **User Attributes** section.

![Screenshot of the SAML token attributes in the UI.](https://learn.microsoft.com/en-us/entra/external-id/media/claims-mapping/view-claims-in-saml-token-attributes.png)

You might need to edit the claims issued in the SAML token for two reasons:

1. The application requires a different set of claim URIs or claim values.
2. The application requires the NameIdentifier claim to be different from the user principal name [\(UPN\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-userprincipalname#what-is-userprincipalname) stored in Microsoft Entra ID.

Learn how to add and edit claims in [Customizing claims issued in the SAML token for enterprise applications in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization).

## UPN claims behavior for B2B users

If you need to issue the UPN value as an application token claim, the actual claim mapping might behave differently for B2B users. If the B2B user authenticates with an external Microsoft Entra identity and you issue `user.userprincipalname` as the source attribute, Microsoft Entra ID issues the UPN attribute from the home tenant for this user.

For all [other external identity types](https://learn.microsoft.com/en-us/entra/external-id/redemption-experience#invitation-redemption-flow), such as SAML/WS-Fed, Google, and Email one-time passcode \(OTP\) when you use `user.userprincipalname` as a claim, the system issues the user's UPN instead of their email address. If you want the actual UPN to be issued in the token claim for all B2B users, set `user.localuserprincipalname` as the source attribute instead.

Note

The behavior mentioned in this section is the same for both cloud-only B2B users and synced users who were [invited/converted to B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/invite-internal-users).

## Related content

- For information about B2B collaboration user properties, see [Properties of a Microsoft Entra B2B collaboration user](https://learn.microsoft.com/en-us/entra/external-id/user-properties).
