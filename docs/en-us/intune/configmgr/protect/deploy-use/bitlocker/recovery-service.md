<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/recovery-service -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About the BitLocker recovery service

*Applies to: Configuration Manager \(current branch\)*

Important

Starting in version 2103, the implementation of the recovery service changed. It's no longer using legacy MBAM components, but is still conceptually referred to as the *recovery service*. All version 2103 clients use the *message processing engine* component of the management point as their recovery service. They escrow their recovery keys over the secure client notification channel. With this change, you can enable the Configuration Manager site for [enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http). This configuration doesn't affect the functionality of BitLocker management in Configuration Manager.

When both the site and clients are running Configuration Manager version 2103 or later, clients send their recovery keys to the management point over the secure client notification channel. If any clients are on version 2010 or earlier, they need an HTTPS-enabled recovery service on the management point to escrow their keys.

The BitLocker recovery service is a server component that receives BitLocker recovery data from Configuration Manager clients. The site deploys the recovery service when you create a BitLocker management policy. Configuration Manager automatically installs the recovery service on each management point with an HTTPS-enabled website.

Configuration Manager stores the recovery information in the site database. Without a BitLocker management encryption certificate, Configuration Manager stores the key recovery information in plain text. For more information, see [Encrypt recovery data in the database](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data).

Starting in version 2010, you can manage BitLocker policies and escrow recovery keys over a cloud management gateway \(CMG\). When domain-joined clients communicate via the CMG, they don't use the legacy recovery service, but the message processing engine component of the management point. Microsoft Entra hybrid joined devices also use the message processing engine.

Starting in version 2103, all supported clients use the message processing engine component of the management point as the recovery service. This change reduces dependencies on legacy MBAM components, and enables support for [enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http).

Note

For version 2010, the message processing engine channel only escrows keys for OS and fixed drive volumes. It doesn't support recovery keys for removable drives or the TPM password hash.

Starting in version 2103, BitLocker management policies over a CMG support the following capabilities:

- Recovery keys for removable drives
- TPM password hash, otherwise known as TPM owner authorization

## Rotate keys

When you recover a key with the self-service or helpdesk portals, since it's disclosed, Configuration Manager requires the client to rotate the key. Rotating the key means that the client generates a new key for BitLocker recovery. It then escrows the new key to the [recovery service](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/recovery-service).

Note

When you migrate from MBAM, when the device receives a BitLocker management policy from Configuration Manager, it first rotates its key. It then sends the new key to the Configuration Manager recovery service.

## Next steps

[Migrate from MBAM](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/migration-considerations)

[Set up BitLocker reports and portals](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/setup-websites)
