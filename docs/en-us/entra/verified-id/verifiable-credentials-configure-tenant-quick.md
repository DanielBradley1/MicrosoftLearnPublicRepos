<!-- Source: https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant-quick -->
<!-- Sitemap-Last-Modified: 2026-04-02 -->

# Quick Microsoft Entra Verified ID setup

## Overview

Quick Verified ID setup removes several configuration steps an admin needs to complete with a single select on a **Get started** button. The quick setup takes care of signing keys, registering your decentralized ID, and verifying your domain ownership. It also creates a Verified Workplace Credential for you.

In this tutorial, you learn how to use the quick setup to configure your Microsoft Entra tenant to use the verifiable credentials service.

Specifically, you learn how to:

- Configure the Verified ID service using the quick setup.
- Control issuance of Verified Workplace Credentials in MyAccount.

Watch this video to quickly set up your Microsoft Entra tenant to use the verifiable credentials service.

<iframe src="https://www.youtube-nocookie.com/embed/0LfYrRd7Qzs?si=IlSzjKQ2ltfKOAgT" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Prerequisites

- You need the [Authentication Policy Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#authentication-policy-administrator) permission for the directory you want to configure. If you need to perform app registration tasks, you'll also need the [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) permission.
- Ensure that you have a [custom domain registered](https://learn.microsoft.com/en-us/entra/identity/users/domains-manage) for the Microsoft Entra tenant. If you don't have one registered, the setup defaults to the advanced setup experience.

Note

The Quick setup method is currently not supported in EDU Microsoft Entra tenants.

## How Quick Verified ID setup works

- Microsoft manages a shared signing key across multiple tenants within a given region. You no longer need to deploy Azure Key Vault.
- There's a two requests per second \(RPS\) per tenant limit for issuance and verifications.
- Since it's a shared key, the validityInterval of issued credentials is limited to a maximum of six months.
- Verified ID uses the [custom domain registered](https://learn.microsoft.com/en-us/entra/identity/users/domains-manage) for your Microsoft Entra tenant for domain verification. You no longer need to upload your DID configuration JSON to verify your domain. If you don't have a custom domain registered for your tenant, you can't set up Verified ID using the quick setup method.
- If you have customized your [tenant's branding](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-customize-branding#before-you-begin), the VerifiedEmployee default credential picks up logo and background color from there. If you haven't or prefer other values, you can make changes after setup is complete.
- The Decentralized identifier \(DID\) gets a name like `did:web:verifiedid.entra.microsoft.com:tenantid:authority-id` and the DID document is discoverable following [did:web specification](https://w3c-ccg.github.io/did-method-web/#create-register).

Note

If the quick setup doesn't meet your requirements, use the [Advanced setup](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant).

## Set up Verified ID

If you have a custom domain registered for your Microsoft Entra tenant, you see this **Get started** option. If you don't have a custom domain registered, either register it before setting up Verified ID or continue using the [advanced setup](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant).

![Screenshot that shows how to set up Verifiable Credentials.](https://learn.microsoft.com/en-us/entra/verified-id/media/verifiable-credentials-configure-tenant-quick/verifiable-credentials-getting-started.png)

To set up Verified ID, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with appropriate administrator permissions.
2. Select **Verified ID**.
3. From the left menu, select **Setup**.
4. Select the **Get started** button.
5. If you have multiple domains registered for your Microsoft Entra tenant, select the one you would like to use for Verified ID.

   ![Screenshot that shows how to select domain.](https://learn.microsoft.com/en-us/entra/verified-id/media/verifiable-credentials-configure-tenant-quick/verifiable-credentials-select-domain.png)

When the setup process is complete, you see a default workplace credential available to edit and offer to employees of your tenant on their MyAccount page.

![Screenshot that shows how to set up is completed.](https://learn.microsoft.com/en-us/entra/verified-id/media/verifiable-credentials-configure-tenant-quick/verifiable-credentials-setup-complete.png)

## MyAccount available now to simplify issuance of Workplace Credentials

Issuing Verified Workplace Credentials is now available via [myaccount.microsoft.com](https://myaccount.microsoft.com/). Users can sign in to **MyAccount** using their Microsoft Entra credentials and issue themselves a Verified Workplace Credential via the **Get my Verified ID** option.

![Screenshot that shows issuance via myaccount.](https://learn.microsoft.com/en-us/entra/verified-id/media/verifiable-credentials-configure-tenant-quick/verifiable-credentials-my-account-issue.png)

As an admin, you can either remove the option in MyAccount and create your custom application for issuing Verified Workplace Credentials. You can also select specific groups of users who can use MyAccount to issue credentials for themselves.

![Screenshot that shows controlling issuance via myaccount.](https://learn.microsoft.com/en-us/entra/verified-id/media/verifiable-credentials-configure-tenant-quick/verifiable-credentials-setup-groups.png)

Note

When you have made a configuration change for issuing credentials through My Account, expect some minutes of delay before the change takes effect.

## Register an application in Microsoft Entra ID

If you're planning to use custom credentials or set up your own application for issuing or verifying Verified ID, you need to register an application and grant the appropriate permissions for it. Follow this section in the advanced setup to [register an application](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant#register-an-application-in-microsoft-entra-id).

## Next steps

- [Learn how to issue Microsoft Entra Verified ID credentials from a web application](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-issuer).
- [Learn how to verify Microsoft Entra Verified ID credentials](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-verifier).
