<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/configure-firewalls-ports-domains -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Network infrastructure considerations for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

To prepare your network to support Configuration Manager, you may need to configure some infrastructure components. For example, open firewall ports to pass the communications used by Configuration Manager.

## Ports and protocols

Different Configuration Manager features use different network ports. Some ports are required, and some you can customize.

Most Configuration Manager communications use common ports like port 80 for HTTP or 443 for HTTPS. Some site system roles support the use of custom websites and custom ports. For more information, see [Websites for site system servers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/websites-for-site-system-servers).

Before you deploy Configuration Manager, identify the ports that you plan to use, and set up firewalls as needed.

After you install Configuration Manager, if you need to change a port, don't forget to update firewalls on devices and the network. Also change the configuration of the port in Configuration Manager.

For more information, see the following articles:

- [How to configure client communication ports](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-communication-ports)
- [Ports used in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/ports)

## Internet access requirements

Some Configuration Manager features rely on internet connectivity for full functionality. If your organization restricts network communication with the internet using a firewall or proxy device, make sure to allow the necessary endpoints.

For more information, see [Internet access requirements](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/internet-endpoints)

## Proxy servers

You can specify separate proxy servers for different site system servers and clients. You make these configurations when you install a site system role or client, or change them later as needed.

For more information, see [Proxy server support](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support).
