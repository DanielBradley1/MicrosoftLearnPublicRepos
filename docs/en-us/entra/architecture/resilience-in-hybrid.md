<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Build resilience in your hybrid architecture

A hybrid infrastructure includes both cloud and on premises components. Hybrid authentication allows users to access cloud-based resources with their identities originating on premises, or to access on-premises resources with cloud-based identities.

- Cloud components include Microsoft Entra ID, Azure resources and services, your organization's cloud-based apps, and SaaS applications.
- on premises components include on premises applications, resources like SQL databases, and an identity provider like Windows Server Active Directory.

Important

As you plan for resilience in your hybrid infrastructure, it's key to minimize dependencies and single points of failure. On premises and cloud connectivity disruption can occur for many reasons, including hardware failure, power outages, natural disasters, and malware attacks.

Microsoft offers multiple mechanisms for hybrid authentication for applications connected to Microsoft Entra. If your organization has been relying upon Active Directory passwords and pass-through authentication or federation to authenticate users, we recommend that you implement password hash synchronization, if possible.

- [Password hash synchronization \(PHS\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs) uses Microsoft Entra Connect to sync the identity and a hash-of-the-hash of the password from Windows Server AD to Microsoft Entra ID. It enables users to sign in to Microsoft Entra to access cloud-based resources with the same password as it set in Active Directory. PHS has dependencies on AD only during synchronization, not during authentication.
- [Pass-through Authentication \(PTA\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta) redirects users to Microsoft Entra ID for sign-in. Then, the username and password are validated against Active Directory on premises through an agent that is deployed in the corporate network. PTA has a footprint of its Microsoft Entra PTA agents that reside on servers on premises. Those servers must be reachable during authentication and must be able to reach a domain controller.
- [Federation](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-fed) customers deploy a federation service such as Active Directory Federation Services \(AD FS\) as an identity provider. Microsoft Entra ID redirects users to authenticate to the identity provider federation service, then validates the SAML assertion produced by the federation service. The user must be able to connect to the identity provider, and the identity provider may also rely upon Active Directory.
- [Microsoft Entra certificate-based authentication\(CBA\)](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication) enables Microsoft Entra to authenticate users using X.509 certificates issued by an Enterprise Public Key Infrastructure \(PKI\) stored in Active Directory, Microsoft Entra ID, or both. Using Microsoft Entra CBA, customers can simplify and reduce dependencies on on-premises components by eliminating the need for Active Directory Federation Services \(AD FS\).

You may be using one or more of these methods in your organization. For more information, see [Choose the right authentication method for your Microsoft Entra hybrid identity solution](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn). This article contains a decision tree that can help you decide on your methodology.

## Password hash synchronization

The simplest and most resilient hybrid authentication option for Microsoft Entra ID is [Password Hash Synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs). It doesn't have any on premises identity infrastructure dependency when processing authentication requests. After identities with password hashes are synchronized to Microsoft Entra ID, users can authenticate to Microsoft Entra and cloud resources with no dependency on the on-premises identity components.

![Architecture diagram of PHS](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-in-hybrid/admin-resilience-password-hash-sync.png)

If you choose this authentication option, you won't experience disruption for access to Microsoft Entra and other cloud resources when on premises identity components become unavailable.

### How do I implement PHS?

To implement PHS, see the following resources:

- [Implement password hash synchronization with Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-password-hash-synchronization)
- [Enable password hash synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-password-hash-synchronization)

If your requirements are such that you can't use PHS, use Pass-through Authentication.

## Pass-through Authentication

Pass-through Authentication has a dependency on authentication agents that reside on premises on servers. A persistent connection, or service bus, is present between Microsoft Entra ID and the on-premises PTA agents. The firewall, servers hosting the authentication agents, and the on-premises Windows Server Active Directory \(or other identity provider\) are all potential failure points.

![Architecture diagram of PTA](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-in-hybrid/admin-resilience-pass-through-authentication.png)

### How do I implement PTA?

To implement Pass-through Authentication, see the following resources.

- [How Pass-through Authentication works](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta-how-it-works)
- [Pass-through Authentication security deep dive](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta-security-deep-dive)
- [Install Microsoft Entra pass-through authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta-quick-start)
- If you're using PTA, define a [highly available topology](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta-quick-start).

## Federation

Federation involves the creation of a trust relationship between Microsoft Entra ID and the federation service, which includes the exchange of endpoints, token signing certificates, and other metadata. When a request comes to Microsoft Entra ID, it reads the configuration and redirects the user to the endpoints configured. At that point, the user interacts with the federation service, which issues a SAML assertion that is validated by Microsoft Entra ID.

The following diagram shows a topology of an enterprise AD FS deployment that includes redundant federation and web application proxy servers across multiple on premises data centers. This configuration relies on enterprise networking infrastructure components like DNS, Network Load Balancing with geo-affinity capabilities, and firewalls. All on premises components and connections are susceptible to failure. Visit the [AD FS Capacity Planning Documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity) for more information.

Note

Federation has a high number of on premises dependencies. While this diagram shows AD FS, other on premises identity providers are subject to similar design considerations to achieve high availability, scalability, and fail over.

![Architecture diagram of federation](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-in-hybrid/admin-resilience-federation.png)

### How do I implement federation?

If you're implementing a federated authentication strategy or want to make it more resilient, see the following resources.

- [What is federated authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-fed)
- [How federation works](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-fed-whatis)
- [Microsoft Entra federation compatibility list](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-fed-compatibility)
- Follow the [AD FS capacity planning documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity)
- [Deploying AD FS in Azure IaaS](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/how-to-connect-fed-azure-adfs)
- [Enable PHS](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/tutorial-phs-backup) along with your federation

## Related architecture resources

For more architecture and deployment guidance related to hybrid identity, see:

- [Microsoft Entra deployment plans](https://learn.microsoft.com/en-us/entra/architecture/deployment-plans) — deployment guidance for authentication, apps, devices, and hybrid scenarios
- [Microsoft Entra architecture overview](https://learn.microsoft.com/en-us/entra/architecture/architecture) — service design, scalability, continuous availability, and datacenter architecture
- [Identity and access management architecture in Azure](https://learn.microsoft.com/en-us/azure/architecture/identity/identity-start-here) — reference architectures, baseline implementations, and design guidance for hybrid identity
- [Integrate on-premises AD with Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/identity/azure-ad) — full reference architecture with downloadable Visio diagrams
- [Choose the right authentication method](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn) — authentication decision tree for hybrid identity solutions
- [Data residency for Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/data-residency) — data storage locations, sovereign clouds, and environment constraints

## Next steps

### Resilience resources for administrators and architects

- [Build resilience with credential management](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-credentials)
- [Build resilience with device states](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-device-states)
- [Build resilience by using Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-continuous-access-evaluation)
- [Build resilience in external user authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2b-authentication)
- [Build resilience for your federated applications with colocated users](https://learn.microsoft.com/en-us/entra/architecture/resilience-for-federated-applications-with-colocated-users)
- [Build resilience in application access with Application Proxy](https://learn.microsoft.com/en-us/entra/architecture/resilience-on-premises-access)

### Resilience resources for developers

- [Build IAM resilience in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
- [Build resilience in your CIAM systems](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
