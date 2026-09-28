<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile-root?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-14 -->

# On-premises publishing profiles

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Various Azure services \(for example, Microsoft Entra Connect [Passthrough Authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta), [Workday to Microsoft Entra users provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workday-inbound-tutorial), and [Application Proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy) allow access to various on-premises resources from outside the corporate network. [On-premises agents](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) \(or [connectors](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta) for Application Proxy\) installed by a tenant administrator can be configured to route requests to a particular [published resource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta). [Agent groups](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) \(or [connector groups](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta) for Application Proxy\) enable a tenant admin to assign specific agents to serve specific published on-premises resources. Tenant admins can group a number of agents together, and then assign each published resource to a group. The entire set of entities of the same on-premises publishing type is represented by [onPremisesPublishingProfile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta).

A tenant admin can configure for each **onPremisesPublishingProfile** the [time window](https://learn.microsoft.com/en-us/graph/api/resources/updatewindow?view=graph-rest-beta) during which agents can receive updates or defer updates to the agents. The [updater configuration](https://learn.microsoft.com/en-us/graph/api/resources/hybridagentupdaterconfiguration?view=graph-rest-beta) specified for an **onPremisesPublishingProfile** is applicable to all the agents within that **onPremisesPublishingProfile**.

For a tutorial about configuring Application Proxy, see [Automate the configuration of Application Proxy using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/application-proxy-configure-api).

## Related content

- [On-premises agent](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta)
- [On-premises agent group](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta)
- [On-premises publishing profile](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingprofile?view=graph-rest-beta)
- [Published resource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta)
- [Connector](https://learn.microsoft.com/en-us/graph/api/resources/connector?view=graph-rest-beta)
- [Connector group](https://learn.microsoft.com/en-us/graph/api/resources/connectorgroup?view=graph-rest-beta)
