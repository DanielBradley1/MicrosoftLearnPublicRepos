<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-debug-apps -->
<!-- Sitemap-Last-Modified: 2026-03-27 -->

# Debug application proxy issues

## Overview

This article explains how to troubleshoot issues with Microsoft Entra application proxy. Use the flowchart to fix remote access issues for an on-premises web application.

## Before you begin

First, check the connector. Learn how in [Troubleshoot private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-connectors).

## Flowchart for application issues

This flowchart helps you debug and fix common issues with the Microsoft Entra application proxy.

The table after the flowchart contains details about each step.

![Diagram of a flowchart that helps debug an application for Microsoft Entra application proxy issues.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-debug-apps/application-proxy-apps-debugging-flowchart.png)

| Step | Goal | Action |
| --- | --- | --- |
| 1 | Sign in and check for user-related errors | Open a browser and sign into the app with your username and password. Check for errors like [This corporate app can't be accessed](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-sign-in-bad-gateway-timeout-error). |
| 2 | Verify user permissions and test app access | Make sure your user account has permissions for the app from inside the corporate network. Then test signing into the app by following the steps in [Test the application](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application#test-the-application). If sign-in issues continue, check [Troubleshoot sign-in errors](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs?context=azure/active-directory/manage-apps/context/manage-apps-context). |
| 3 | Confirm correct application proxy configuration | Open a browser and use the app. If an error appears immediately, check if the application proxy is set up correctly. For details about specific error messages, see [Troubleshoot application proxy problems and error messages](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-troubleshoot). |
| 4 | Ensure custom domain setup is correct or troubleshoot errors | If the page doesn't display, check if your custom domain is set up correctly. Review the information in [Work with custom domains](https://learn.microsoft.com/en-us/entra/identity/app-proxy/how-to-configure-custom-domain).  <br>  <br>If the page doesn't load and an error message appears, troubleshoot the error using the information in [Troubleshoot application proxy problems and error messages](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-troubleshoot).  <br>  <br>If it takes longer than 20 seconds before an error message appears, there might be a connectivity issue. Follow the steps in [Troubleshoot private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-connectors). |
| 5 | Debug connectivity issues between the proxy and the connector | If issues persist, try connector debugging. Complete the steps described in [Troubleshoot private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-connectors). |
| 6 | Publish all resources and resolve publishing issues | Ensure the publishing path includes all the necessary images, scripts, and style sheets for your application. For details, see [Add an on-premises app to Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application).  <br>  <br>Use the browser's developer tools \(F12 tools in Internet Explorer or Microsoft Edge\) for troubleshooting publishing issues. See [Application page doesn't display correctly](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-troubleshoot).  <br>  <br>Review options to fix broken links in [Links on the page don't work](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-page-links-broken-problem). |
| 7 | Minimize network latency | If the page loads slowly, explore ways to reduce network latency in [Considerations for reducing latency](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-network-topology#considerations-for-reducing-latency). |
| 8 | Access more troubleshooting resources | If issues persist, review more articles about [troubleshooting application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-troubleshoot). |

## Related content

- [Understand private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connectors).
- [Work with existing on-premises proxy servers](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-configure-connectors-with-proxy-servers).
- [Troubleshoot application proxy and connector errors](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-troubleshoot).
