<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data-transit -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Encrypt recovery data over the network

*Applies to: Configuration Manager \(current branch\)*

When you create a BitLocker management policy, Configuration Manager deploys the recovery service to a management point. On the **Client Management** page of the BitLocker management policy, when you **Configure BitLocker Management Services**, the client backs up key recovery information to the site database. This information includes BitLocker recovery keys, recovery packages, and TPM password hashes. When users are locked out of their protected device, you can use this information to help them recover access to the device.

Given the sensitive nature of this information, you need to protect it.

Important

Starting in version 2103, the implementation of the recovery service changed. It's no longer using legacy MBAM components, but is still conceptually referred to as the *recovery service*. All version 2103 clients use the *message processing engine* component of the management point as their recovery service. They escrow their recovery keys over the secure client notification channel. With this change, you can enable the Configuration Manager site for [enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http). This configuration doesn't affect the functionality of BitLocker management in Configuration Manager.

When both the site and clients are running Configuration Manager version 2103 or later, clients send their recovery keys to the management point over the secure client notification channel. If any clients are on version 2010 or earlier, they need an HTTPS-enabled recovery service on the management point to escrow their keys.

## HTTPS certificate requirements

Note

These requirements only apply if the site is version 2010 or earlier, or if you deploy BitLocker management policies to devices with Configuration Manager client version 2010 or earlier.

Configuration Manager requires a secure connection between the client and the recovery service to encrypt the data in transit across the network. Use one of the following options:

- [HTTPS-enable the IIS website](#https-enable-the-iis-website) on the management point that hosts the recovery service, not the entire management point role.
- [Configure the management point for HTTPS](#configure-the-management-point-for-https). On the properties of the management point, the **Client connections** setting must be **HTTPS**.

Note

If your site has more than one management point, enable HTTPS on all management points at the site with which a BitLocker-managed client could potentially communicate. If the HTTPS management point is unavailable, the client could fail over to an HTTP management point, and then fail to escrow its recovery key.

This recommendation applies to both options: enable the management point for HTTPS, or enable the IIS website that hosts the recovery service on the management point.

### Configure the management point for HTTPS

In earlier versions of Configuration Manager current branch, to integrate the BitLocker recovery service you had to HTTPS-enable a management point. The HTTPS connection is necessary to encrypt the recovery keys across the network from the Configuration Manager client to the management point. Configuring the management point and all clients for HTTPS can be challenging for many customers.

### HTTPS-enable the IIS website

The HTTPS requirement is now for the IIS website that hosts the recovery service, not the entire management point role. This configuration relaxes the certificate requirements, and still encrypts the recovery keys in transit.

The **Client connections** property of the management point can be **HTTP** or **HTTPS**. If the management point is configured for **HTTP**, to support the BitLocker recovery service:

1. Acquire a server authentication certificate. Bind the certificate to the IIS website on the management point that hosts the BitLocker recovery service.
2. Configure clients to trust the server authentication certificate. There are two methods to accomplish this trust:

   - Use a certificate from a public and globally trusted certificate provider. Windows clients include trusted root certificate authorities \(CAs\) from these providers. By using a server authentication certificate that's issued by one of these providers, your clients should automatically trust it.
   - Use a certificate issued by a CA from your organization's public key infrastructure \(PKI\). Most PKI implementations add the trusted root CAs to Windows clients. For example, using Active Directory Certificate Services with group policy. If you issue the server authentication certificate from a CA that your clients don't automatically trust, add the CA trusted root certificate to clients.

Tip

The only clients that need to communicate with the recovery service are those clients that you plan to target with a BitLocker management policy and includes a **Client Management** rule.

## Troubleshoot the connection

On the client, use the **BitLockerManagementHandler.log** to troubleshoot this connection. For connectivity to the recovery service, the log shows the URL that the client is using. Locate an entry in the log based on the version of Configuration Manager:

- In version 2103 and later, the entry starts with `Recovery keys escrowed to MP`
- In version 2010 and earlier, the entry starts with `Checking for Recovery Service at`

## Next steps

[Encrypt recovery data in the database](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data) is an optional prerequisite before deploying policy for the first time.

[Deploy BitLocker management client](https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/deploy-management-agent)
