<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-on-premises-access -->
<!-- Sitemap-Last-Modified: 2024-04-12 -->

# Build resilience in application access with Application Proxy

Application Proxy is a feature of Microsoft Entra ID that enables users to access on premises web applications from a remote client. Application Proxy includes the Application Proxy service in the cloud and the private network connectors that run on an on-premises server.

Users access on premises resources through a URL published via Application Proxy. They're redirected to the Microsoft Entra sign-in page. The Application Proxy service in Microsoft Entra ID then sends a token to the private network connector in the corporate network that passes the token to the on-premises Active Directory. The authenticated user can then access the on-premises resource. In the diagram below, [connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connectors) are shown in a [connector group](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connector-groups).

Important

When you publish your applications via Application Proxy, you must implement [capacity planning and appropriate redundancy for the private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connectors#specifications-and-sizing-requirements).

![Architecture diagram of Application y](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-on-prem-access/admin-resilience-app-proxy.png)\)

## How do I implement Application Proxy?

To implement remote access with Microsoft Entra application proxy, see the following resources.

- [Planning an Application Proxy deployment](https://learn.microsoft.com/en-us/entra/identity/app-proxy/conceptual-deployment-plan)
- [High availability and load balancing best practices](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-high-availability-load-balancing)
- [Configure proxy servers](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-configure-connectors-with-proxy-servers)
- [Design a resilient access control strategy](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-resilient-controls)

## Next steps

### Resilience resources for administrators and architects

- [Build resilience with credential management](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-credentials)
- [Build resilience with device states](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-device-states)
- [Build resilience by using Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-continuous-access-evaluation)
- [Build resilience in external user authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2b-authentication)
- [Build resilience in your hybrid authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid)

### Resilience resources for developers

- [Build IAM resilience in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
- [Build resilience in your CIAM systems](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
