<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/certificate-based-authentication-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions about Microsoft Entra certificate-based authentication

This article addresses frequently asked questions about how Microsoft Entra certificate-based authentication \(CBA\) works. Check back for updated content.

## Why don't I see an option to sign in to Microsoft Entra ID by using certificates after I enter my username?

An administrator must turn on CBA for the tenant to make the option to sign in by using a certificate available to users. For more information, see [Step 3: Configure the authentication binding policy](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-certificate-based-authentication#step-3-configure-an-authentication-binding-policy).

## Where can I get more diagnostic information after a user sign-in fails?

On the error page, select **More Details** for more information to help your tenant admin. The tenant admin can check the sign-in logs to investigate the error. For example, if a user certificate is revoked and is on the certification revocation list \(CRL\), authentication fails as intended.

## How do we turn on Microsoft Entra CBA?

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with at least the [Authentication Policy Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#authentication-policy-administrator) role assigned.
2. Go to **Entra ID** > **Authentication methods** > **Policies**.
3. Select the **Certificate-based authentication** policy.
4. On the **Enable and Target** tab, select **Enable**.

## Is Microsoft Entra CBA a free feature?

Microsoft Entra CBA is a free feature.

Every edition of Microsoft Entra ID includes Microsoft Entra CBA.

For more information about features in each Microsoft Entra edition, see [Microsoft Entra pricing](https://www.microsoft.com/security/business/identity-access-management/azure-ad-pricing).

## Does Microsoft Entra CBA support an alternate ID as the username instead of userPrincipalName?

No. Currently, sign-in by using a non-UPN value, such as an alternate email, isn't supported.

## Can I have more than one CRL distribution point for a certificate authority?

No, only one CRL distribution point \(CDP\) is supported per certificate authority \(CA\).

## Can I use a non-HTTP URL for a CDP?

No. CDP supports only HTTP URLs.

## How do I find the CRL for a CA, or how do I troubleshoot the error "AADSTS2205015: The Certificate Revocation List \(CRL\) failed signature validation"?

Download the CRL and compare the CA certificate and the CRL information to validate that the `crlDistributionPoint` value is valid for the CA you want to add. You can configure the CRL to the corresponding CA by matching the CA's issuer subject key identifier \(SKI\) to the authority key identifier \(AKI\) of the CRL \(CA Issuer SKI == CRL AKI\).

The following table and figure show how to map information from the CA certificate to the attributes of the downloaded CRL.

| CA certificate info | = | Downloaded CRL info |
| --- | :---: | --- |
| Subject | = | Issuer |
| Subject Key Identifier \(SKI\) | = | Authority Key Identifier \(KeyID\) |

![Screenshot that compares CA certificate fields with CRL information.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-certificate-based-authentication/certificate-crl-compare.png)

## How do I validate the CA configuration?

It's important to ensure that the Certificate Authority configuration in the trust store results in Microsoft Entra's ability to both validate the certificate authority trust chain. Additionally, it should successfully acquire the certificate revocation list \(CRL\) from the configured certificate authority CRL distribution point \(CDP\). To assist with this task, it's recommended to install the [MSIdentity Tools](https://aka.ms/msid) PowerShell module and run [Test-MsIdCBATrustStoreConfiguration](https://github.com/AzureAD/MSIdentityTools/wiki/Test-MsIdCBATrustStoreConfiguration). This PowerShell cmdlet will review the Microsoft Entra tenant certificate authority configuration and surface errors/warnings for common mis-configuration issues.

## Do changes to the authentication methods policy take effect immediately?

The policy is cached. After a policy update, it might take up to an hour for the changes to take effect.

## Why do I see the CBA option after it fails?

The authentication method policy always shows all available authentication methods to the user so that they can retry sign-in by using any method they prefer.

Microsoft Entra ID doesn't hide available methods based on the success or failure of a sign-in.

## Why does CBA loop after it fails?

The browser caches the certificate after the certificate picker appears. If the user retries authentication, the cached certificate is automatically used. The user should close the browser, and then reopen a new session to try CBA again.

## Why doesn't identity proof to register other authentication methods appear as an option when I use single-factor certificates?

A user is considered capable of multifactor authentication \(MFA\) when the user is in scope for CBA in the authentication methods policy. This policy requirement means that a user can't use identity proof as part of their authentication to register other available methods.

## How can I use single-factor certificates to complete MFA?

We support single-factor CBA to get MFA. CBA single-factor with passwordless phone sign-in and CBA single-factor with FIDO2 are the two supported combinations to get MFA by using single-factor certificates.

For more information, see [MFA with single-factor certificates](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-technical-deep-dive#mfa-authentication-flow-by-using-single-factor-certificates-and-passwordless-sign-in).

## The certificateUserIds update fails because it's an existing value. How can an admin query all the user objects that have the same value?

Tenant admins can run Microsoft Graph queries to find all the users that have a specific `certificateUserIds` value. For more information, see [`certificateUserIds` Graph queries](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-certificateuserids#update-certificateuserids-using-microsoft-graph-queries).

For example, this command returns all user objects that have the value `bob@contoso.com` in `certificateUserIds`:

```http
GET  https://graph.microsoft.com/v1.0/users?$filter=certificateUserIds/any(x:x eq 'bob@contoso.com')
```

## Can Microsoft Entra CBA be used on Microsoft Surface Hub?

Yes. CBA works out-of-the-box for most combinations of smart card and smart card reader. If the combination smart card and smart card reader requires other drivers, you must install the drivers before you can use the combination smart card and smart card reader on Surface Hub.

## Related content

If your question isn't answered here, see the following related articles:

- [Overview of Microsoft Entra CBA](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication)
- [Microsoft Entra CBA technical concepts](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-technical-deep-dive)
- [Microsoft Entra CBA on iOS devices](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-mobile-ios)
- [Microsoft Entra CBA on Android devices](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-mobile-android)
- [Set up Microsoft Entra CBA](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-certificate-based-authentication)
- [Windows smart card sign-in by using Microsoft Entra CBA](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-smartcard)
- [Certificate user IDs](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-certificateuserids)
- [Migrate federated users](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-migration)
