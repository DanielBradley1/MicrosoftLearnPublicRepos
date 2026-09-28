<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-powershell-samples -->
<!-- Sitemap-Last-Modified: 2026-03-11 -->

# Microsoft Entra application proxy PowerShell examples

## Overview

The following table includes links to PowerShell script examples for Microsoft Entra application proxy. These samples require the [Microsoft Graph Beta PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation) 2.10 or newer, unless otherwise noted.

For more information about the cmdlets used in these samples, see [application proxy application management](https://learn.microsoft.com/en-us/powershell/module/azuread/#application_proxy_application_management) and [private network connector management](https://learn.microsoft.com/en-us/powershell/module/azuread/#application_proxy_connector_management).

| Link | Description |
| --- | --- |
| **Application proxy apps** |  |
| [List basic information for all application proxy apps](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-app-proxy-apps-basic) | Lists basic information \(AppId, DisplayName, ObjId\) about all the application proxy apps in your directory. |
| [List extended information for all application proxy apps](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-app-proxy-apps-extended) | Lists extended information \(AppId, DisplayName, ExternalUrl, InternalUrl, ExternalAuthenticationType\) about all the application proxy apps in your directory. |
| [List all application proxy apps by connector group](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-app-proxy-apps-by-connector-group) | Lists information about all the application proxy apps in your directory and which connector groups the apps are assigned to. |
| [Get all application proxy apps with a token lifetime policy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-app-proxy-apps-with-policy) | Lists all application proxy apps in your directory with a token lifetime policy and its details. |
| **Connector groups** |  |
| [Get all connector groups and connectors in the directory](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-connectors) | Lists all the connector groups and connectors in your directory. |
| [Move all apps assigned to a connector group to another connector group](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-move-all-apps-to-connector-group) | Moves all applications currently assigned to a connector group to a different connector group. |
| **Users and group assigned** |  |
| [Display users and groups assigned to an application proxy application](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-display-users-group-of-app) | Lists the users and groups assigned to a specific application proxy application. |
| [Assign a user to an application](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-assign-user-to-app) | Assigns a specific user to an application. |
| [Assign a group to an application](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-assign-group-to-app) | Assigns a specific group to an application. |
| **External URL configuration** |  |
| [Get all application proxy apps using default domains \(.msappproxy.net\)](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-default-domain-apps) | Lists all the application proxy applications using default domains \(.msappproxy.net\). |
| [Get all application proxy apps using wildcard publishing](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-wildcard-apps) | Lists all application proxy apps using wildcard publishing. |
| **Custom Domain configuration** |  |
| [Get all application proxy apps using custom domains and certificate information](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-custom-domains-and-certs) | Lists all application proxy apps that are using custom domains and the certificate information associated with the custom domains. |
| [Get all Microsoft Entra ID Proxy application apps published with no certificate uploaded](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-all-custom-domain-no-cert) | Lists all application proxy apps that are using custom domains but don't have a valid TLS/SSL certificate uploaded. |
| [Get all Microsoft Entra ID Proxy application apps published with the identical certificate](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-custom-domain-identical-cert) | Lists all the Microsoft Entra ID Proxy application apps published with the identical certificate. |
| [Get all Microsoft Entra ID Proxy application apps published with the identical certificate and replace it](https://learn.microsoft.com/en-us/entra/identity/app-proxy/scripts/powershell-get-custom-domain-replace-cert) | For Microsoft Entra ID Proxy application apps that are published with an identical certificate, allows you to replace the certificate in bulk. |
