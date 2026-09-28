<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-explicit-forward-proxy -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Configure Explicit Forward Proxy

With Explicit Forward Proxy, you can use the secure web and AI gateway capabilities of Microsoft Entra Internet Access without installing the Global Secure Access client. Explicit Forward Proxy works with any browser that supports proxy automatic configuration \(PAC\).

## Prerequisites

- Ensure that you have the following Microsoft Entra admin roles:

  - The Global Secure Access Administrator role to manage the Global Secure Access features
  - The Conditional Access Administrator role to create and manage Microsoft Entra Conditional Access policies

- Complete the [guide for getting started with Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-access-admin-center).
- Review the [Explicit Forward Proxy concepts](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-explicit-forward-proxy) and [Explicit Forward Proxy session management concepts](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-explicit-forward-proxy-session-management).
- Enable the Internet Access traffic-forwarding profile.
- Configure Transport Layer Security \(TLS\) inspection.

## Enable Explicit Forward Proxy

You can enable and manage Explicit Forward Proxy by using the Microsoft Entra admin center:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Go to **Global Secure Access** > **Session management**, and then select the **Explicit Forward Proxy** tab.
3. Set the **Internet Access** toggle to **Enabled**. By default, smart session management is enabled when you enable Explicit Forward Proxy.
4. Optionally, enable HTTP header session management. For more information, see [Configure HTTP header session management](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-explicit-forward-proxy-headers).

[![Screenshot of the tab in the Microsoft Entra admin center for configuring Explicit Forward Proxy.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-configure-explicit-forward-proxy/enable-explicit-forward-proxy.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-configure-explicit-forward-proxy/enable-explicit-forward-proxy.png#lightbox)

Important

Explicit Forward Proxy session management relies on IP affinity as one of the session management anchors. We recommend that you configure a Conditional Access policy that restricts the use of Explicit Forward Proxy to networks you trust. For more information, see [Explicit Forward Proxy session management](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-explicit-forward-proxy-session-management) and [Configure a Conditional Access policy for Explicit Forward Proxy](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-conditional-access-policy-for-explicit-forward-proxy).

## Related content

- [Configure a Conditional Access policy for Explicit Forward Proxy](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-conditional-access-policy-for-explicit-forward-proxy)
- [Configure HTTP header session management](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-explicit-forward-proxy-headers)
- [Configure Explicit Forward Proxy in Microsoft Edge by using Intune mobile application management](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-explicit-forward-proxy-intune-policy)
