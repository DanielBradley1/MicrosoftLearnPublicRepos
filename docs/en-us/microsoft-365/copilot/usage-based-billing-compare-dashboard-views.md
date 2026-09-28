<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-compare-dashboard-views -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# Usage-based billing: What you see in the Microsoft 365 admin center vs. your Azure bill

Use this article to understand how Copilot Credit consumption appears across admin and billing experiences. The Microsoft 365 admin center gives IT admins detailed operational views for usage-based billing policies and consumption. Azure Cost Management and Azure invoices show the billing view for the Azure subscription connected to the billing method. These views are related, but they don't show the same level of detail.

Important

This article focuses on Copilot experiences managed through Cost Management in the Microsoft 365 admin center including Copilot Cowork and Work IQ API usage. Other usage-based services might use different setup, reporting, or admin experiences. For example, Power Platform and Copilot Studio usage details are managed in the Power Platform admin center.

## The one currency: Copilot Credits

Copilot Credits are the common currency for eligible Microsoft AI experiences enabled by usage-based billing, including Copilot Cowork, Microsoft Copilot Studio, Power Platform workloads, and Work IQ APIs. Organizations can access credits through capacity packs, Copilot Credit pre-purchase plans, or pay-as-you-go billing. How credits are purchased, allocated, and consumed depends on the billing method and the experience using them.

Usage-based billing means charges are based on the work performed rather than a flat per-user fee. The number of credits a task consumes varies with the models used, the amount of context retrieved, the runtime needed to plan and complete the work, and the tools the task calls.

## View billing information in the Azure portal

In the Microsoft 365 admin center, you can use **Billing > Bills & payments** to view invoices and a high-level snapshot of charges associated with your billing account. For more detailed billing analysis, including cost breakdowns and billing data by subscription, resource, meter, or invoice period, use Azure Cost Management and Azure billing tools.

Use Azure Cost Management and Azure billing views to understand billed charges for the Azure subscription connected to your billing method. Azure shows billing data by billing scope, subscription, resource, meter, and invoice period. Billed amounts update daily, but usage can take up to 24 hours to appear in Azure Cost Management.

In Azure Cost Management, you can filter billing details by meter or Azure resource. Copilot Cowork, Copilot Studio, and Work IQ API consumption appears under the Microsoft Copilot Studio service rather than separate services for each experience.

Azure Cost Management shows pay-as-you-go charges and purchase or amortized cost information for Copilot Credit pre-purchase plans \(P3\) and Microsoft Agent pre-purchase plans \(P3\). P3 appears as a reservation benefit in Azure Cost Management.

Copilot Credit pre-purchase plans provide discounted commit units for eligible Copilot Credit usage during a one-year term. You can pay for the plan up front or through monthly payments. If you pay up front, Azure charges the one-time purchase to the linked subscription. The amortized cost view distributes the purchase cost across the plan term based on credit consumption.

Important

Azure Cost Management doesn't show consumption against Prepaid Capacity packs. Use the Microsoft 365 admin center or Power Platform admin center, as applicable, to monitor Prepaid Capacity Pack credit usage.

| Azure view | Use it to answer | Important difference from Microsoft 365 admin center |
| --- | --- | --- |
| Azure Cost Management | What amount is billed or accrued for the linked Azure subscription? | Shows billing-oriented cost data, such as costs by subscription, service, resource, meter, or invoice period. It doesn't show the same user-level or spending-policy context as the Microsoft 365 admin center. |
| Actual cost | What charges appear on the bill? | Shows pay-as-you-go charges and P3 purchases when they're charged to the subscription. |
| Amortized cost | How should the cost of a P3 purchase be distributed over the plan term for internal showback or chargeback? | Distributes the P3 purchase cost across the plan term based on credit consumption. Actual and amortized cost views can show different totals for the same date range. Consumption doesn't rise in a smooth, steady line, but it might climb at different rates from day to day depending on how much agentic work your organization runs. For more information, see [View amortized costs](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/view-amortized-costs) |
| Invoice | What is the payable invoice amount for the billing period? | Invoice line items are billing summaries. Shows finalized billing line items. Copilot Credit consumption for Copilot Cowork, Copilot Studio, and Work IQ APIs can appear under the **Microsoft Copilot Studio** service rather than as separate service line items. |

## View detailed usage information in the Microsoft 365 admin center

Use **Copilot > Cost Management** in the Microsoft 365 admin center when you want to manage and monitor Copilot Credit usage for services governed by Microsoft 365 usage-based billing policies. This view is designed for operational and governance questions, such as who is using credits, which policy applies, and whether usage is approaching configured limits.

Navigate to **Copilot > Cost Management** to unlock AI experiences enabled by usage-based billing, to set up spending policies, and monitor how Copilot Credits are consumed across supported services. Everything in this view is expressed in Copilot Credits, not currency.

For more information on how to monitor usage in the Microsoft 365 admin center, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

Note

The Microsoft 365 admin center is the best place to understand usage in the context of spending policies and users. It's not the same as an invoice view. Dashboard totals and exports might be point-in-time views and can refresh at different intervals.

## Understanding Purchasing Plans as they relate to Billing

Organizations can access Copilot Credits through capacity packs, Copilot Credit pre-purchase plans \(P3\) and Microsoft Agent pre-purchase plans \(P3\), or pay-as-you-go billing. Each option has a different purchasing and billing model.

- **Capacity packs** are license-based purchases available through the Microsoft 365 Marketplace. Their credits can support eligible Microsoft Copilot, SharePoint agent, Copilot Studio, and Copilot Cowork usage. Admins manage and allocate capacity-pack credits in the Power Platform admin center.
- **Copilot Credit pre-purchase plans \(P3\)** are commitment-based purchases available through the Azure portal and the Microsoft 365 admin center. They provide discounted commit units for eligible Copilot Credit usage during the plan term.
- **Pay-as-you-go** bills eligible Copilot Credit usage to the linked Azure subscription without an upfront credit commitment. It can also cover usage after available P3 credits or Capacity packs are exhausted when pay-as-you-go is enabled.

### How credit sources are consumed

If your organization has more than one credit source, usage can draw from Prepaid Capacity before pay-as-you-go charges apply. The exact billing outcome depends on which billing methods are enabled and whether available prepaid balances remain.

| If this is available | What happens first | What happens next |
| --- | --- | --- |
| **Prepaid Capacity pack credits** | Usage draws from the prepaid credit pool. | If the prepaid pool is exhausted, the next available credit source or pay-as-you-go billing can apply, depending on policy configuration. |
| **Copilot Credit pre-purchase plan \(P3\)** | Available P3 commit units are consumed before pay-as-you-go overage. | Usage beyond available pre-purchased credits can be billed as pay-as-you-go if pay-as-you-go is enabled. |
| **Microsoft Agent pre-purchase plan \(P3\)** | Available P3 commit units are consumed before pay-as-you-go overage. | Usage beyond available pre-purchased credits can be billed as pay-as-you-go if pay-as-you-go is enabled. |
| **Pay-as-you-go billing** | Usage beyond available Prepaid Capacity pack credits or P3 commit units is billed to the linked Azure subscription. | Usage remains subject to configured spending limits. |
| **No available Prepaid Capacity pack credits or Copilot Credit Pre-purchase plans \(P3\) commit units, and pay-as-you-go isn't enabled** | Requests are blocked when limits or available credit sources are exhausted. | Admins can update the billing method or spending policy if additional usage should be allowed. |

## Frequently asked questions

### Will I see a separate Copilot Cowork line item on my Azure bill?

Not currently. Cowork, Copilot Studio, and Work IQ consumption is billed through a single common Copilot Credits service that is labeled as **Microsoft Copilot Studio**. To attribute cost to a specific service, separate it by Azure subscription or resource group, or use service tags as they become available.

### Why doesn't my Azure bill match the credits shown in the Microsoft 365 admin center?

Everything in the Microsoft 365 admin center view is expressed in Copilot Credits, not currency. In addition, the two views capture data at different times and for different purposes. The Microsoft 365 admin center shows daily usage and can include non-billable usage, while the Azure bill reflects finalized, billable consumption at the close of the month. Small differences are expected. Use the monthly billing record for reconciliation, not the usage dashboards.

### How is a task's credit cost determined?

Credits consumed vary by task based on the models used, the context retrieved, the runtime required, and the tools called. Usage isn't a fixed amount per request, so more complex or multistep work generally consumes more credits.

### What's the difference between capacity packs and pay-as-you-go?

Capacity packs are credits you buy in advance and draw down as you use them. Pay-as-you-go bills you for consumption beyond your Prepaid Capacity, in arrears, through your connected Azure subscription. The Microsoft 365 admin center's **Prepaid Capacity pack credits used** tile shows what the user consumes from capacity packs.

### What's the difference between pre-purchase plans and pay-as-you-go?

Copilot Credit pre-purchase plans \(P3\) provide discounted commit units that automatically cover eligible Copilot Credit usage during a one-year term or until the units run out. Pay-as-you-go has no upfront commitment and bills eligible usage to the linked Azure subscription at the applicable rate. P3 can provide savings for predictable usage, while pay-as-you-go offers flexibility for variable or uncertain demand. If both are available, eligible usage draws down the P3 balance first; after the balance is exhausted, additional usage can be billed through pay-as-you-go when it is enabled. For purchasing requirements, sizing guidance, and plan management, see [Optimize Copilot Credit costs with a pre-purchase plan](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/copilot-credit-p3).

## Related articles

- [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits)
- [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [View usage and billing information - Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/pay-as-you-go-usage-costs)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
