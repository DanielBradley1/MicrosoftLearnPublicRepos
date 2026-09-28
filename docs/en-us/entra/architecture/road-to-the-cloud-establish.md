<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-establish -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Establish a Microsoft Entra footprint

Before you migrate identity and access management \(IAM\) from Active Directory to Microsoft Entra ID, you need to set up Microsoft Entra ID.

## Required tasks

If you're using Microsoft Office 365, Exchange Online, or Teams, then you're already using Microsoft Entra ID. Your next step is to establish more Microsoft Entra capabilities:

- Establish hybrid identity synchronization between Active Directory and Microsoft Entra ID by using [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect) or [Microsoft Entra Connect cloud sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync).
- [Select authentication methods](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn). We strongly recommend password hash synchronization.
- Secure your hybrid identity infrastructure by following [Five steps to securing your identity infrastructure](https://learn.microsoft.com/en-us/azure/security/fundamentals/steps-secure-identity).

## Optional tasks

The following functions aren't specific or mandatory to move from Active Directory to Microsoft Entra ID, but we recommend incorporating them into your environment. These items are also recommended in the [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/) guidance.

### Deploy passwordless authentication

In addition to the security benefits of [passwordless credentials](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2), passwordless authentication simplifies your environment because the management and registration experience is already native to the cloud. Microsoft Entra ID provides passwordless credentials that align with various use cases. Use the information in this article to plan your deployment: [Plan a passwordless authentication deployment in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-passwordless-deployment).

After you roll out passwordless credentials to your users, consider reducing the use of password credentials. You can use the [reporting and insights dashboard](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity) to continue to drive the use of passwordless credentials and reduce the use of passwords in Microsoft Entra ID.

Important

During your application discovery, you might find applications that have a dependency or assumptions around passwords. Users of these applications need to have access to their passwords until those applications are updated or migrated.

### Configure Microsoft Entra hybrid join for existing Windows clients

You can configure Microsoft Entra hybrid join for existing Active Directory-joined Windows clients to benefit from cloud-based security features such as [co-management](https://learn.microsoft.com/en-us/mem/configmgr/comanage/overview), Conditional Access, and Windows Hello for Business. New devices should be Microsoft Entra joined and not Microsoft Entra hybrid joined.

To learn more, check [Plan your Microsoft Entra hybrid join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan).

## Next steps

- [Introduction](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-introduction)
- [Cloud transformation posture](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-posture)
- [Implement a cloud-first approach](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-implement)
- [Transition to the cloud](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-migrate)
