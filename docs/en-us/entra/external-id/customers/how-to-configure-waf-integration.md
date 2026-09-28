<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-configure-waf-integration -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# Configure Cloudflare with Microsoft Entra External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

You can integrate third-party Web Application Firewall \(WAF\) solutions with Microsoft Entra External ID to improve overall security. A WAF helps protect your organization from attacks such as distributed denial of service \(DDoS\), malicious bots, and Open Worldwide Application Security Project [\(OWASP\) Top-10](https://owasp.org/www-project-top-ten/) security risks.

Cloudflare Web Application Firewall \([Cloudflare WAF](https://www.cloudflare.com/application-services/products/waf/)\) protects your web apps from common exploits and vulnerabilities. By integrating Cloudflare WAF with Microsoft Entra External ID, you add an extra layer of security for your applications.

This article provides step-by-step guidance to configure your external tenant with Cloudflare WAF.

## Solution overview

The solution uses three main components:

- **External tenant** – Acts as the identity provider \(IdP\) and authorization server, enforcing custom policies for authentication.
- **Azure Front Door \(AFD\)** – Handles custom domain routing and forwards traffic to Microsoft Entra External ID.
- **Cloudflare WAF** – The WAF that manages traffic sent to the authorization server.

## Prerequisites

To get started, you need:

- An [external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).
- A Microsoft [Azure Front Door \(AFD\)](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview) configuration. Traffic from the Cloudflare WAF routes to Azure Front Door, which then routes to the external tenant.
- A [Cloudflare WAF](https://www.cloudflare.com/application-services/products/waf/) that manages traffic sent to the authorization server.
- A [custom domain](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-url-domain) in your external tenant that’s enabled with Azure Front Door \(AFD\).

Learn about tenants and securing apps for consumers and customers with [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/external-identities-overview).

## Cloudflare setup steps

First, set up Cloudflare WAF to protect your custom URL domains for Microsoft Entra External ID. Follow these steps to configure Cloudflare WAF.

### Enable custom URL domains

The first step is to enable custom domains with AFD. Use the instructions in [Enable custom URL domains for apps in external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-url-domain).

### Create a Cloudflare account

1. Go to [Cloudflare.com/plans](https://www.cloudflare.com/plans/) to create an account.
2. To enable WAF, on the **Application Services** tab, select **Pro**.

### Configure the domain name server \(DNS\)

Enable WAF for a domain.

1. In the DNS console, for CNAME, enable the proxy setting.

   [![Screenshot of CNAME options.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/proxy-settings.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/proxy-settings-expanded.png#lightbox)
2. Under DNS, for **Proxy status**, select **Proxied**.
3. The status turns orange.

   [![Screenshot of proxied status.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/proxied-status.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/proxied-status-expanded.png#lightbox)

Note

Azure Front Door-managed certificates aren't automatically renewed if your custom domain’s CNAME record points to a DNS record other than the Azure Front Door endpoint’s domain \(for example, when using a third-party DNS service like Cloudflare\). To renew the certificate in such cases, follow the instructions in the [Renew Azure Front Door-managed certificates](https://learn.microsoft.com/en-us/azure/frontdoor/domain#renew-azure-front-door-managed-certificates) article.

### Cloudflare security controls

For optimal protection, enable Cloudflare security controls.

### DDoS protection

1. Go to the [Cloudflare dashboard](https://developers.cloudflare.com/workers/get-started/dashboard/).
2. Expand the Security section.
3. Select **DDoS**.
4. A message appears.

![Screenshot of bot protection options.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/bot-protection.png)

### Bot protection

1. Go to the [Cloudflare dashboard](https://developers.cloudflare.com/workers/get-started/dashboard/).
2. Expand the Security section.
3. Under **Configure Super Bot Fight Mode**, for **Definitely automated**, select **Block**.
4. For **Likely automated**, select **Managed Challenge**.
5. For **Verified bots**, select **Allow**.

![Screenshot of bot protection options.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/bot-protection.png)

### Firewall rules: Traffic from the Tor network

Block traffic that originates from the Tor proxy network, unless your organization needs to support the traffic.

Note

If you can't block Tor traffic, select **Interactive Challenge**, not **Block**.

### Block traffic from the Tor network

1. Go to the [Cloudflare dashboard](https://developers.cloudflare.com/workers/get-started/dashboard/).
2. Expand the Security section.
3. Select **WAF**.
4. Select **Create rule**.
5. For **Rule name**, enter a relevant name.
6. For **If incoming requests match**, for **Field**, select **Continent**.
7. For **Operator**, select **equals**.
8. For **Value**, select **Tor**.
9. For **Then take action**, select **Block**.
10. For **Place at**, select **First**.
11. Select **Deploy**.

![Screenshot of the create rule dialog.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/create-rule.png)

Note

You can add custom HTML pages for visitors.

### Firewall rules: Traffic from countries or regions

We recommend strict security controls on traffic from countries or regions where business is unlikely to occur, unless your organization has a business reason to support traffic from all countries or regions.

Note

If you can't block traffic from a country or region, select **Interactive Challenge**, not **Block**.

### Block traffic from countries or regions

For the following instructions, you can add custom HTML pages for visitors.

1. Go to the [Cloudflare dashboard](https://developers.cloudflare.com/workers/get-started/dashboard/).
2. Expand the Security section.
3. Select **WAF**.
4. Select **Create rule**.
5. For **Rule name**, enter a relevant name.
6. For **If incoming requests match**, for **Field**, select **Country/Region** or **Continent**.
7. For **Operator**, select **equals**.
8. For **Value**, select the country/region or continent to block.
9. For **Then take action**, select **Block**.
10. For **Place at**, select **Last**.
11. Select **Deploy**.

![Screenshot of the name field on the create rule dialog.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/create-rule-name.png)

### OWASP and managed rulesets

1. Select **Managed rules**.
2. For **Cloudflare Managed Ruleset**, select **Enabled**.
3. For **Cloudflare OWASP Core Ruleset**, select **Enabled**.

[![Screenshot of rule sets.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/rulesets.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/ruleset-expanded.png#lightbox)

## Verify Cloudflare WAF in External ID

After you set up your Cloudflare account, connect it to Microsoft Entra External ID. Use your Cloudflare [API token](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/) and [Zone ID](https://developers.cloudflare.com/fundamentals/account/find-account-and-zone-ids/#copy-your-zone-id) to complete the connection. You can do this in the admin center or by using Microsoft Graph API.

- [Microsoft Entra admin center](#tabpanel_1_admin-center)
- [Microsoft Graph API](#tabpanel_1_graph-api)

## WAF provider configuration

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Security Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to the external tenant you created earlier from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **Security Store**.
4. Select the **Protect apps from DDoS with WAF** tile by selecting **Get started**.
5. Under **Choose a WAF Provider** select **Cloudflare** and then select **Next**.

   ![Screenshot of the choose WAF provider page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/choose-waf.png)
6. Under **Configure Cloudflare WAF**, you can select an existing configuration or create a new one. If you're creating a new configuration, add the following information:

   - **Configuration name**: A name for the WAF configuration.
   - **API token**: The API token from your Cloudflare dashboard.
   - **Zone ID**: The Zone ID for your domain, from your Cloudflare dashboard.


   ![Screenshot of the configure WAF provider page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/configure-waf-provider.png)

7. Select **Next** to save your changes.

## Domain verification

Select the custom URL domains that Azure Front Door \(AFD\) enables to verify and connect them to your Cloudflare WAF configuration. This step ensures that the selected domains are protected with advanced security features.

1. Select **Verify domain** to start the verification process.
2. Select the custom URL domains you want to protect with Cloudflare WAF and then select **Verify**.

   ![Screenshot of the verify domain page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/verify-domain.png)
3. After verification, select **Done**.

You can use the Microsoft Graph API through [Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer) to configure the Cloudflare WAF integration.

Make sure the caller has the [Security Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader) role and has consented to the [RiskPreventionProviders.Read.All](https://learn.microsoft.com/en-us/graph/permissions-reference#riskpreventionprovidersreadall) permission.

![Screenshot showing consent to permissions.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/consent-to-permissions.png)

![Screenshot showing the consent button.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/consent-button.png)

This permission allows you to call `POST .../riskPrevention/webApplicationFirewallProviders` to create provider and then call `POST .../riskPrevention/webApplicationFirewallProviders/{webApplicationFirewallProviderId}/verify` to verify.

## Step 1: Create Cloudflare WAF provider with the API

Make sure that you have the **API token** you created in Cloudflare and the **Zone ID** for your domain. This information is required so the backend can call Cloudflare on your behalf to pull and verify the WAF configuration.

### Request

The following example shows a request to create a new Cloudflare WAF object.

```http
POST https://graph.microsoft.com/beta/identity/riskPrevention/webApplicationFirewallProviders
Content-Type: application/json
{
    "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
    "displayName": "Cloudflare Provider Example",
    "zoneId": "11111111111111111111111111111111",
    "apiToken": "cf_example_token_123"
}
```

### Response

The following example shows the response with Cloudflare WAF object.

```http
HTTP/1.1 201 Created
Content-Type: application/json
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identity/riskPrevention/webApplicationFirewallProviders/$entity",
    "@odata.type": "#microsoft.graph.cloudFlareWebApplicationFirewallProvider",
    "id": "00000000-0000-0000-0000-000000000001",
    "displayName": "Cloudflare Provider Example",
    "zoneId": "11111111111111111111111111111111"
}
```

## Step 2: Verify Cloudflare WAF provider with the API

The following example shows how to verify a domain via `webApplicationFirewallProvider` using the `hostName`.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/identity/riskPrevention/webApplicationFirewallProviders/{webApplicationFirewallProviderId}/verify
Content-Type: application/json
{
  "hostName": "www.contoso.com"
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.webApplicationFirewallVerificationModel",
    "id": "00000000-0000-0000-0000-000000000000",
    "verifiedHost": "www.contoso.com",
    "providerType": "cloudflare",
    "verificationResult": {
        "status": "success",
        "verifiedOnDateTime": "2025-10-04T00:50:26.4909654Z",
        "errors": [],
        "warnings": []
    },
    "verifiedDetails": {
        "@odata.type": "#microsoft.graph.cloudFlareVerifiedDetailsModel",
        "zoneId": "11111111111111111111111111111111",
        "dnsConfiguration": {
            "name": "www.contoso.com",
            "isProxied": true,
            "recordType": "cname",
            "value": "contoso.azurefd.net",
            "isDomainVerified": true
        },
        "enabledRecommendedRulesets": [
            {
                "rulesetId": "22222222222222222222222222222222",
                "name": "CloudFlare Managed Ruleset",
                "phaseName": "http_request_firewall_managed"
            }
        ],
        "enabledCustomRules": [
            {
                "ruleId": "33333333333333333333333333333333",
                "name": "Block SQL Injection",
                "action": "block"
            },
            {
                "ruleId": "44444444444444444444444444444444",
                "name": "Block XSS",
                "action": "block"
            }
        ]
    }
}
```

Note

CRUD \(Create, Read, Update, Delete\) operations on providers’ verification details may experience delays of up to 15 minutes. If you delete a domain, verification might take up to 15 minutes before you can add it back.

### Test the configuration

After you connect Cloudflare WAF with Microsoft Entra External ID, test the configuration to make sure everything works as expected.

![Screenshot showing configuration test results.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-configure-cloudflare-integration/configuration-test.png)

## Troubleshooting

The following table lists common issues you might encounter when integrating Cloudflare WAF with Microsoft Entra External ID, along with their details and resolutions.

| **Issue** | **Details** | **Resolution** |
| --- | --- | --- |
| Bad Request Response | "The provided API Key has insufficient permissions. Please reauthenticate and try again.\\r\\n CloudFlare Request ID: {CF-Ray-value}\\r\\nCorrelation ID: random-id-entry-value\\r\\nTimestamp: 2024-08-25 21:32:40Z" | Check the permission level mentioned in the preceding steps. |
| Couldn't reach the external tenant's well-known endpoint | "Could not reach the tenant's well-known endpoint via custom domain. Please check that your custom domain is properly configured to route traffic."  <br>At the Graph level, you might see **HTTP 200 OK** with status **failure** when Cloudflare returns error code **403**. This check is performed on our side before any API calls to Cloudflare. | Disable the captcha on the Cloudflare portal \(change the wildcard to disable\), then rerun the POST request. |

## Additional resources

- Cloudflare WAF [Get started guide](https://developers.cloudflare.com/waf/get-started/): Includes recommendations on how to best configure WAF and what basic protection and rules you can deploy.
- FAQ related to [External Tenant Overview - Microsoft Entra External ID \| Microsoft Learn](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam) for other best practices and considerations.
- Check traffic results in the Cloudflare dashboard: [Security Analytics · Cloudflare WAF docs](https://developers.cloudflare.com/waf/analytics/security-analytics/)
- Azure Front Door additional best practices [Domains in Azure Front Door \| Microsoft Learn](https://learn.microsoft.com/en-us/azure/frontdoor/domain)
- [API Troubleshooting · Cloudflare Fundamentals docs](https://developers.cloudflare.com/fundamentals/api/troubleshooting/)
- [Troubleshooting · Cloudflare Support docs](https://developers.cloudflare.com/support/troubleshooting/)

## Related content

- [What is Azure Web Application Firewall on Azure Application Gateway?](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/ag-overview)
- [Tutorial: Configure Cloudflare WAF with Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/partner-cloudflare)
