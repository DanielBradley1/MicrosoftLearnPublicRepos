<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-csp-partner-macc -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# Usage-based billing guidance for CSPs, partner-managed customers, and MACC

Use this guidance to connect the appropriate Azure subscription for Cloud Solution Provider \(CSP\), partner-managed, and Microsoft Azure Consumption Commitment \(MACC\) billing scenarios.

## For CSPs or partner-managed customers

Important

If you're a Cloud Solution Provider \(CSP\) or a partner-managed customer, see the [Partner-facing FAQs](https://aka.ms/CSPM365CopilotPartnerFAQ) for setup instructions and details.

Setup instructions are available in the FAQ under the question: **What steps are required to configure Cowork usage and billing for my customer?**

**Step 1**: Ensure an Azure subscription is set up and linked to your partner billing account.

If the customer already has an Azure subscription: → Ensure it's associated with your partner billing account.

If the customer doesn't have an Azure subscription: → Create a new subscription by using the Azure portal or Partner Center.

**Step 2**: Configure usage-based billing in Microsoft 365 admin center.

Connect the Azure subscription associated with your partner billing account [more details](https://learn.microsoft.com/en-us/partner-center/customers/purchase-azure-plan).

Configure user access controls \(who can use the services\), spending limits, and alerts [more details](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits#add-spending-policy).

Ensure the setting that allows users to discover and use usage-based services is turned on [more details](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

## Understanding Azure Consumption Commitment \(MACC\) in Microsoft Copilot

If your organization has an Azure Consumption Commitment \(MACC\), you can apply those committed funds toward eligible Copilot consumption. This approach helps you maximize existing investments while adopting AI-powered capabilities.

To ensure correct application of MACC, administrators must configure billing in the Microsoft 365 admin center by using an Azure subscription associated with the correct billing account. MACC benefits apply only when the selected subscription links to a billing account that includes the commitment. If you use a different billing account or subscription, you still pay for consumption, but it might not count toward your MACC. Therefore, proper setup is critical.

Administrators should:

- Verify access to the billing account that contains the MACC commitment.
- Select an Azure subscription associated with that billing account during setup.
- Ensure the correct billing relationship is established before enabling consumption-based services.

When you configure it correctly, eligible Copilot usage automatically applies against your MACC. You don't need to take any extra action during ongoing usage.

This model allows organizations to seamlessly extend their Azure investment into Microsoft Copilot scenarios while maintaining control over billing, governance, and cost visibility.

## Related articles

- [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup)
- [Manage AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
