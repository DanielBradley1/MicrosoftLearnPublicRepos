<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/okta-attack-disruption -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Enable attack disruption actions in Okta with Microsoft Sentinel \(preview\)

Microsoft Defender XDR's [automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) capabilities can help protect your Okta-managed identities by automatically responding to threats. When an identity managed by Okta is compromised, Defender XDR can take remediation actions directly in Okta to contain the attack, limit lateral movement, and reduce overall impact.

This article describes how to set up the Okta integration in Microsoft Defender for Identity to enable attack disruption actions in your Okta environment. Before you begin, review the [prerequisites](#prerequisites) to ensure your Okta and Microsoft environments are properly configured.

## Prerequisites

Make sure you meet these requirements:

### Okta requirements

You need an Okta account with admin access. You also need a developer or enterprise license.

### Microsoft requirements

Complete these steps before you continue:

- Connect your Microsoft Sentinel analytic workspace to the unified security operations portal.
- Deploy and enable the Okta connector for Microsoft Sentinel.

Note

During public preview, only the Okta single sign-in connector is supported.

## Step 1: Create the Okta integration

To create the integration from an Okta account with admin privileges, follow these steps:

1. [Find your Okta domain](https://developer.okta.com/docs/guides/find-your-domain/main/#find-your-okta-domain)
2. [Create an Okta API key](https://help.okta.com/en-us/content/topics/security/api.htm#create-okta-api-token)

   - Provide a friendly name for your token
   - Make sure to keep the generated token value to be used later when creating the integration profile in the Defender portal.

Note

This token is a secret that allows connecting to your Okta environment and performing actions. Don't share its value or save it in any visible or public location.

## Step 2: Create the integration from the Defender portal

To create the integration in the Defender portal, follow these steps:

1. Log in to the [Defender portal](https://security.microsoft.com/)
2. Navigate **Microsoft Sentinel** -> **Configuration** -> **Automation**.
3. In the **Integrations profiles** tab, select **+Create** to create a new integration.

   ![Screenshot of the Integrations profile tab in the Automation page with the Create button highlighted.](https://learn.microsoft.com/en-us/defender-xdr/media/okta-attack-disruption/create-new-integration.png)
4. Fill in the following values, then select **Create**:

   1. **Integration name**
   2. **Description**
   3. **Base API URL**: Enter your full Okta domain starting with `https://`
   4. **Authentication method**: Select API Key

      1. **API key name**
      2. **API key**: Enter `SSWS <API-Key>`, replacing `<API-Key>` with the value of the API token you generated in Okta. There should be a space between `SSWS` and your API Key. For more information, see the [Okta documentation for API Key usage](https://developer.okta.com/docs/reference/core-okta-api/#authentication)
      3. **API key identifier**: Leave empty
      4. Enable the **Send SPI key in header** switch.


   [![Screenshot of the integration details form with fields for Integration name, Description, Base API URL, and Authentication method.](https://learn.microsoft.com/en-us/defender-xdr/media/okta-attack-disruption/integration-details.png)](https://learn.microsoft.com/en-us/defender-xdr/media/okta-attack-disruption/integration-details.png#lightbox)

## Related content

- [Automatic attack disruption in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption)
- [Configure automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption)
- [Enable attack disruption actions on AWS with Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/aws-disruption?toc=/defender-xdr/toc.json&bc=/defender-xdr/breadcrumb/toc.json)
- [How Microsoft Defender for Identity protects your Okta accounts](https://learn.microsoft.com/en-us/defender-for-identity/okta-defender-for-identity-overview)
- [Connect Okta to Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/okta-integration)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
