<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-with-continuous-access-evaluation -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Build resilience by using Continuous Access Evaluation

[Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation) allows Microsoft Entra applications to subscribe to critical events that can then be evaluated and enforced. CAE includes evaluation of the following events:

- User account deleted or disabled
- Password for user changed
- MFA enabled for user
- Administrator explicitly revokes a token
- Elevated user risk detected

As a result, applications can reject unexpired tokens based on the events signaled by Microsoft Entra ID as depicted in the following diagram.

![conceptualiagram of CAE](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-with-cae/admin-resilience-continuous-access-evaluation.png)

## How does CAE help?

The CAE mechanism allows Microsoft Entra ID to issue longer-lived tokens while enabling applications to revoke access and force reauthentication only when needed. The net result of this pattern is fewer calls to acquire tokens, which means that the end-to-end flow is more resilient.

To use CAE, both the service and the client must be CAE-capable. Microsoft 365 services such as Exchange Online, Teams, and SharePoint Online support CAE. On the client side, browser-based experiences that use these Office 365 services \(such as Outlook Web App\) and specific versions of Office 365 native clients are CAE-capable. More Microsoft cloud services will become CAE-capable.

Microsoft is working with the industry to build [standards](https://openid.net/wg/sse/) that will allow third party applications to use CAE capability. You can also develop applications that are CAE-capable. For more information about CAE-capable application development, see [How to build resilience in your application](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview).

## How do I implement CAE?

- [Update your code to use CAE-enabled APIs](https://learn.microsoft.com/en-us/entra/identity-platform/app-resilience-continuous-access-evaluation).
- [Enable CAE](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation) in the Microsoft Entra Security Configuration.
- Ensure that your organization is using [compatible versions](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation) of Microsoft Office native applications.
- [Optimize your reauthentication prompts](https://learn.microsoft.com/en-us/entra/identity/authentication/concepts-azure-multi-factor-authentication-prompts-session-lifetime).

## Next steps

### Resilience resources for administrators and architects

- [Build resilience with credential management](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-credentials)
- [Build resilience with device states](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-device-states)
- [Build resilience in external user authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2b-authentication)
- [Build resilience in your hybrid authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid)
- [Build resilience in application access with Application Proxy](https://learn.microsoft.com/en-us/entra/architecture/resilience-on-premises-access)

### Resilience resources for developers

- [Build IAM resilience in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
- [Build resilience in your CIAM systems](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
