<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-application-gateway-waf -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Use Application Gateway WAF to protect your applications

## Overview

Add Web Application Firewall \(WAF\) protection for apps published with Microsoft Entra application proxy.

For more information about Web Application Firewall, see [What is Azure Web Application Firewall on Azure Application Gateway?](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview).

## Deployment steps

This article provides the steps to securely expose a web application on the Internet using Microsoft Entra application proxy with Azure WAF on Application Gateway.

![Architecture diagram showing web application traffic flow from Internet through Azure WAF and Application Gateway to Microsoft Entra application proxy and internal application servers.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-proxy-waf.png)

### Configure Azure Application Gateway to send traffic to your internal application

Some steps of the Application Gateway configuration are omitted in this article. For a detailed guide on creating and configuring an Application Gateway, see [Quickstart: Direct web traffic with Azure Application Gateway - Microsoft Entra admin center](https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-portal).

### 1. Create a private-facing HTTPS listener

Create a listener so users can access the web application privately when connected to the corporate network.

![Application Gateway listener configuration page showing private access settings for corporate network users.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-listener.png)

### 2. Create a backend pool with the web servers

In this example, the backend servers have Internet Information Services \(IIS\) installed.

![Application Gateway backend pool configuration showing IIS web servers.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-backend.png)

### 3. Create a backend setting

A backend setting determines how requests reach the backend pool servers.

![Application Gateway backend settings configuration page showing request routing parameters.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-backend-settings.png)

### 4. Create a routing rule that ties the listener, the backend pool, and the backend setting created in the previous steps

![Application Gateway routing rule configuration page showing listener selection step.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-add-rule-1.png) ![Application Gateway routing rule configuration page showing backend pool and backend settings selection.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-add-rule-2.png)

### 5. Enable the WAF in the Application Gateway and set it to Prevention mode

![Application Gateway WAF configuration page showing WAF enabled with Prevention mode selected.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-enable-waf.png)

## Configure your application to be remotely accessed through application proxy in Microsoft Entra ID

Both connector VMs, the Application Gateway, and the backend servers are deployed in the same virtual network in Azure. The setup also applies to applications and connectors deployed on-premises.

For a detailed guide on how to add your application to application proxy in Microsoft Entra ID, see [Tutorial: Add an on-premises application for remote access through application proxy in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application). For more information about performance considerations concerning the private network connectors, see [Optimize traffic flow with Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-network-topology).

![Microsoft Entra application proxy configuration showing matching internal and external URLs for port 443 access.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-proxy-configuration.png)

In this example, the same URL was configured as the internal and external URL. Remote clients access the application over the Internet on port 443, through the application proxy. A client connected to the corporate network accesses the application privately. Access is through the Application Gateway directly on port 443. For a detailed step on configuring custom domains in application proxy, see [Configure custom domains with Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/how-to-configure-custom-domain).

An [Azure Private Domain Name System \(DNS\) zone](https://learn.microsoft.com/en-us/azure/dns/private-dns-getstarted-portal) is created with an A record. The A record points `www.fabrikam.one` to the private frontend IP address of the Application Gateway. The record ensures the connector VMs send requests to the Application Gateway.

## Test the application

After [adding a user for testing](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application#add-a-user-for-testing), you can test the application by accessing `https://www.fabrikam.one`. The user is prompted to authenticate in Microsoft Entra ID, and upon successful authentication, accesses the application.

![Microsoft Entra ID sign-in page prompting user for authentication.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/sign-in-2.png) ![Browser showing successful application access after authentication.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/application-gateway-response.png)

## Simulate an attack

To test if the WAF is blocking malicious requests, you can simulate an attack using a basic SQL injection signature. For example, "https://www.fabrikam.one/api/sqlquery?query=x%22%20or%201%3D1%20--".

![Browser showing HTTP 403 Forbidden error from WAF blocking SQL injection attempt.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/waf-response.png)

An HTTP 403 response confirms that WAF blocked the request.

The Application Gateway [Firewall logs](https://learn.microsoft.com/en-us/azure/application-gateway/application-gateway-diagnostics#firewall-log) provide more details about the request and why WAF is blocking it.

![Application Gateway Firewall log entry showing blocked request details and SQL injection rule violation.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-waf/waf-log.png)

## Next steps

- [Web Application Firewall rules](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/application-gateway-customize-waf-rules-portal)
- [Web Application Firewall exclusion lists](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/application-gateway-waf-configuration?tabs=portal)
- [Web Application Firewall custom rules](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/create-custom-waf-rules)
