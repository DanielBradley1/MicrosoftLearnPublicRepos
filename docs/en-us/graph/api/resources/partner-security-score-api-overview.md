<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-score-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# Use the partner security score API in Microsoft Graph \(preview\)

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The Microsoft Partner Center ecosystem provides a security score to indirect providers or direct bill partners in the Cloud Solution Provider \(CSP\), Value Added Reseller, or Advisor programs. The goal of the score and requirements is to help partners understand the security posture of their tenant and their customer's tenants. The partner security score builds on the Identity and Microsoft 365 security scores to provide suggestions specific to their scenario. The [partner security score API](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) is a pivotal tool designed to empower Microsoft partners by providing a quantifiable measure of their security performance. This API facilitates partners in enhancing their security posture by offering a comprehensive security score based on their adherence to Microsoft's security requirements.

The partner security score API is defined in the OData subnamespace `microsoft.graph.partners.security`.

## Objectives

The primary objectives of the security score API include:

- **Quantifying security performance:** Offering partners a numerical score that reflects their current security status.
- **Guiding security enhancements with actionable insights:** Providing actionable insights and recommendations to help partners bolster their security measures.
- **Monitoring security evolution:** Enabling partners to track their security improvements over time, fostering a culture of continuous security enhancement.

Use the Microsoft Graph [partner security score API](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) to retrieve the score and insights into your customer security posture.

> **Note:** In order to take actions for the security requirements, choose the action URL provisioned in the API response to go to the relevant UI.

## Common use cases

The following table shows common requests for working with the partner security alert API in Microsoft Graph.

| Use case | REST operation | Try it in Graph Explorer |
| :--- | :--- | :--- |
| Get partner security score | [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-get?view=graph-rest-beta) | [https://graph.microsoft.com/beta/security/partner/securityScore](https://developer.microsoft.com/graph/graph-explorer?request=security/partner/securityScore&method=GET&version=beta&GraphUrl=https://graph.microsoft.com) |
| List customer security insights | [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-customerinsights?view=graph-rest-beta) | [https://graph.microsoft.com/beta/security/partner/securityScore/customerInsights](https://developer.microsoft.com/graph/graph-explorer?request=security/partner/securityScore/customerInsights&method=GET&version=beta&GraphUrl=https://graph.microsoft.com) |

## Related content

The partner security score API in Microsoft Graph provides a summary of your security posture and provides actions to improve. Follow these steps to get started:

- Drill down on the requirements and properties of the [partnerSecurityScore](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) resource.
- Try the API in the [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
