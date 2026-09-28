<!-- Source: https://learn.microsoft.com/en-us/entra/identity/domain-services/tshoot-ldaps -->
<!-- Sitemap-Last-Modified: 2025-02-19 -->

# Troubleshoot secure LDAP connectivity issues to a Microsoft Entra Domain Services managed domain

Applications and services that use lightweight directory access protocol \(LDAP\) to communicate with Microsoft Entra Domain Services can be [configured to use secure LDAP](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-configure-ldaps). An appropriate certificate and required network ports must be open for secure LDAP to work correctly.

This article helps you troubleshoot issues with secure LDAP access in Microsoft Entra Domain Services.

## Common connection issues

If you have trouble connecting to a Microsoft Entra Domain Services managed domain using secure LDAP, review the following troubleshooting steps. After each troubleshooting step, try to connect to the managed domain again:

- The issuer chain of the secure LDAP certificate must be trusted on the client. You can add the Root certification authority \(CA\) to the trusted root certificate store on the client to establish the trust.

  - Make sure you [export and apply the certificate to client computers](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-configure-ldaps#export-a-certificate-for-client-computers).

- Verify the secure LDAP certificate for your managed domain has the DNS name in the *Subject* or the *Subject Alternative Names* attribute.

  - Review the [secure LDAP certificate requirements](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-configure-ldaps#create-a-certificate-for-secure-ldap) and create a replacement certificate if needed.

- Verify that the LDAP client, such as *ldp.exe* connects to the secure LDAP endpoint using a DNS name, not the IP address.

  - The certificate applied to the managed domain doesn't include the IP addresses of the service, only the DNS names.

- Check the DNS name the LDAP client connects to. It must resolve to the public IP address for secure LDAP on the managed domain.

  - If the DNS name resolves to the internal IP address, update the DNS record to resolve to the external IP address.

- For external connectivity, the network security group must include a rule that allows the traffic to TCP port 636 from the internet.

  - If you can connect to the managed domain using secure LDAP from resources directly connected to the virtual network but not external connections, make sure you [create a network security group rule to allow secure LDAP traffic](https://learn.microsoft.com/en-us/entra/identity/domain-services/tutorial-configure-ldaps#lock-down-secure-ldap-access-over-the-internet).

## Next steps

If you still have issues, [open an Azure support request](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/how-to-get-support) for additional troubleshooting assistance.
