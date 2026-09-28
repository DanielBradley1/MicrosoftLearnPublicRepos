<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-integrate-with-traffic-manager -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Add your own Traffic Manager solution to application proxy

## Overview

This article explains how to configure Microsoft Entra application proxy and Azure Traffic Manager.

With the application proxy geo-routing feature, you can optimize which region of application proxy your connector groups use. You can combine this functionality with a Traffic Manager solution of your choice. This combination enables a fully dynamic geo-aware solution based on your user location. It unlocks the rich rule set of your preferred Traffic Manager solution to prioritize how traffic is routed to the apps that you help protect by using application proxy. With this combination, users can use a single URL to access the instance of the app that's closest to them.

![Diagram that shows Traffic Manager integration with application proxy.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-integrate-with-traffic-manager/application-proxy-integrate-with-traffic-manager-diagram.png)

## Prerequisites

- A Traffic Manager solution.
- Apps that exist in different regions. Geo-routing is enabled per connector group colocated with the app.
- A custom domain to use for each app.

## Configure application proxy

To use Traffic Manager, you must configure application proxy. The configuration steps that follow refer to these URL definitions:

- **Regional URL**: The application proxy endpoints for each app. For example, `nam.contoso.com` and `india.contoso.com`.
- **Alternate URL**: The URL configured for the Traffic Manager solution. For example, `contoso.com`.

To configure application proxy for Traffic Manager:

1. Install connectors for each location that contains your app instances. For each connector group, use the geo-routing feature to assign the connectors to their respective regions.
2. Set up your app instances with application proxy:

   1. For each app, upload a custom domain. Include the alternate URL to use for the apps as a subject alternative name \(SAN\) URL to the uploaded certificate.
   2. Assign each app to its respective connector group.
   3. If you prefer the alternate URL to be maintained throughout the user session, register each app and add the URL as a reply URL. This step is optional.

3. In the Traffic Manager solution, add the regional URLs for application proxy that you created for each app as endpoints.
4. Configure the Traffic Manager solution's load-balancing rules with a standard license.
5. To give your Traffic Manager solution a user-friendly URL, create a `CNAME` record that points the alternate URL to the Traffic Manager solution's endpoint.
6. Configure the alternate URL on the app by using the Microsoft Graph API to update the `alternateUrl` property on the [`onPremisesPublishing` resource type](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishing). The `alternateUrl` property isn't available in the Microsoft Entra admin center. You must configure it by using the Graph API. For more information, see [Update application](https://learn.microsoft.com/en-us/graph/api/application-update).

   The following example shows the request body for setting `alternateUrl`:

   ```http
   PATCH https://graph.microsoft.com/beta/applications/{id}
   Content-Type: application/json

   {
     "onPremisesPublishing": {
       "alternateUrl": "https://www.contoso.com"
     }
   }
   ```


   Note


   The `onPremisesPublishing` property can't be updated in the same request as other application properties.

7. If you want the alternate URL to be maintained throughout the user session, set the `useAlternateUrlForTranslationAndRedirect` flag to `true` in the same `onPremisesPublishing` object:

   ```http
   PATCH https://graph.microsoft.com/beta/applications/{id}
   Content-Type: application/json

   {
     "onPremisesPublishing": {
       "alternateUrl": "https://www.contoso.com",
       "useAlternateUrlForTranslationAndRedirect": true
     }
   }
   ```

## Sample application proxy configuration

The following table shows a sample application proxy configuration. This configuration uses the sample app domain `www.contoso.com` as the alternate URL.

|  | North America-based app | India-based app | Additional information |
| --- | --- | --- | --- |
| **Internal URL** | `contoso.com` | `contoso.com` | If the apps are hosted in different regions, you can use the same internal URL for each app. |
| **External URL** | `nam.contoso.com` | `india.contoso.com` | Configure a custom domain for each app. |
| **Custom domain certificate** | Domain Name System \(DNS\): `nam.contoso.com`  <br>SAN: `www.contoso.com` | DNS: `india.contoso.com`  <br>SAN: `www.contoso.com` | In the certificate that you upload for each app, set the SAN value to the alternate URL. The alternate URL is the URL that all users use to reach the app. |
| **Connector group** | North America Geo Group | India Geo Group | Ensure that you assign each app to the correct connector group by using the geo-routing functionality. |
| **Redirects** | \(Optional\) To maintain redirects for the alternate URL, add the application registration for the app. | \(Optional\) To maintain redirects for the alternate URL, add the application registration for the app. | This step is required if the alternate URL `www.contoso.com` will be maintained for all redirections. |
| **Reply URL** | `www.contoso.com` | `www.contoso.com` |  |

## Configure Traffic Manager

Follow these steps to configure Traffic Manager:

1. Create a Traffic Manager profile with your preferred routing rules.
2. In Traffic Manager, add the North America endpoint: `nam.contoso.com`.
3. Add the India endpoint: `india.contoso.com`.
4. Add the app proxy endpoints.
5. Add a `CNAME` record to point `www.contoso.com` to the Traffic Manager solution's URL. For example, use `contoso.trafficmanager.net`. The alternate URL now points to the Traffic Manager solution.

## Related content

- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
