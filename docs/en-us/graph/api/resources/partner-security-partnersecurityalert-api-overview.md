<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-08 -->

# Use the partner security alert API in Microsoft Graph \(preview\)

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

As a partner in the Cloud Solution Provider \(CSP\) program, you're responsible for your customer's Azure consumption; therefore, it's important that you're aware of any anomalous usage in your customer's Azure subscriptions. Use Microsoft Graph [partner security alert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) API to detect patterns of fraudulent activities and misuse in Azure resources to help reduce your exposure to online transaction risks. Mitigating and responding to the alerts within 24 hours can significantly minimize the financial loss that your customers might incur during the compromise.

For information about how to contain a compromise on your customer's tenant or Azure subscriptions, see [What additional steps can you take to lower the risk of compromise](https://learn.microsoft.com/en-us/partner-center/azure-fraud-notification#what-additional-steps-can-you-take-to-lower-the-risk-of-compromise).

The partner security alert API is defined in the OData subnamespace `microsoft.graph.partners.security`.

## Common use cases

The following are requests for working with the partner security alert API in Microsoft Graph.

| Use cases | REST operations | Try it in Graph Explorer |
| :--- | :--- | :--- |
| List partner security alerts | [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-list-securityalerts?view=graph-rest-beta) | [https://graph.microsoft.com/beta/security/partner/securityAlerts](https://developer.microsoft.com/graph/graph-explorer?request=security/partner/securityAlerts&method=GET&version=beta&GraphUrl=https://graph.microsoft.com) |
| Get a partner security alert | [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-get?view=graph-rest-beta) | [https://graph.microsoft.com/beta/security/partner/securityAlerts/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/partner/securityAlerts/%7Bid%7D&method=GET&version=beta&GraphUrl=https://graph.microsoft.com) |
| Update a partner security alert | [Update](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-update?view=graph-rest-beta) | [https://graph.microsoft.com/beta/security/partner/securityAlerts/{id}](https://developer.microsoft.com/graph/graph-explorer?request=security/partner/securityAlerts/%7Bid%7D&method=PATCH&version=beta&GraphUrl=https://graph.microsoft.com) |

## Next steps

The partner security alert API in Microsoft Graph enables detection of fraudulent activities and misuse in Azure resources, which helps reduce your exposure to online transaction risks. Follow these steps to get started:

- Drill down on the methods and properties of the [partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) resource.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
