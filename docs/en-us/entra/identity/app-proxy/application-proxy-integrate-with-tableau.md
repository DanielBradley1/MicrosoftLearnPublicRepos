<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-integrate-with-tableau -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Microsoft Entra application proxy and Tableau

## Overview

Microsoft and Tableau worked together so you can use application proxy to provide remote access for your Tableau deployment.

## Prerequisites

- Configure [Tableau](https://help.tableau.com/current/server/en-us/proxy.htm#azure).
- Install a [private network connector](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application).

## Enabling application proxy for Tableau

Application proxy supports the OAuth 2.0 Grant Flow, which is required for Tableau to work properly. This means that there are no longer any special steps required to enable this application, other than configuring it by following the publishing steps.

## Publish your applications in Microsoft Entra

To publish Tableau, you need to publish an application in the Microsoft Entra admin center.

- Steps 1 through 8 are detailed in the application proxy tutorial. For more information, see [Publish applications using Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application).
- Information about how to find Tableau values for the application proxy fields, see the Tableau documentation.

**To publish your app**:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. Select **New application** at the top of the page.
4. Select **On-premises application**.
5. Fill out the required fields with information about the new app.

   - **Internal URL**: This application should have an internal URL that is the Tableau URL itself. For example, `https://adventure-works.tableau.com`.
   - **Pre-authentication method**: Microsoft Entra ID \(recommended but not required\).

6. Select **Add** at the top of the page. Your application is added, and the quick start menu opens.
7. In the quick start menu, select **Assign a user for testing**, and add at least one user to the application. Make sure this test account has access to the on-premises application.
8. Select **Assign** to save the test user assignment.
9. \(Optional\) On the app management page, select **Single sign-on**. Choose **Integrated Windows Authentication** from the drop-down menu, and fill out the required fields based on your Tableau configuration. Select **Save**.

## Testing

Your application is now ready to test. Access the external URL you used to publish Tableau, and sign in as a user assigned to both applications.

## Next steps

- [How to provide secure remote access to on-premises applications](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy)
