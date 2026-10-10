<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing -->
<!-- Sitemap-Last-Modified: 2026-10-06 -->

# Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)

AI work can range from simple, everyday productivity tasks to complex operations that run across agents for extended periods. Microsoft groups this work into two categories:

- **Everyday AI:** AI that you give to your whole workforce, providing a wide set of foundational AI capabilities to help with productivity. This can include summarizing meetings, drafting documents, and analysis.
- **Advanced AI:** Complex, long-running agentic work you hand off—such as with Cowork, Code, Autopilots, or the latest frontier models.

Copilot supports these categories of AI work in different ways, including different ways of paying, so organizations can plan and manage costs as agents take on longer, more complex work.

## User subscription license \(USL\) and usage-based billing \(UBB\)

Microsoft provides two means of paying for these different kinds of work, offering organizations flexibility in how they manage licensing and billing. Each category has a corresponding billing approach, helping organizations align AI capabilities and costs with the value of the work.

- **User subscription licensing \(USL\):** The USL covers everyday AI work, providing a fixed-price AI foundation for your workforce. Typical productivity tasks can be covered by the USL, which is generally purchased by IT and provided across the organization. Auto, the default mode when using Copilot, anchors the USL—it weighs accuracy, speed, and cost for each request to route to the model and level of reasoning effort best suited to the job, without requiring users to choose a model. Model selection is also part of the USL, with some models included with fair use, such as GPT 5.6 and Sonnet, and others included with limits, such as Opus.
- **Usage-based billing \(UBB\):** UBB is used for advanced AI and frontier models, extending beyond the everyday AI included in the USL. It’s primarily used for agentic work that requires more time, compute, or specialized frontier models, helping you match cost to value. Because of this, UBB may be better funded by business units that can manage UBB along with cost-benefit tradeoffs. UBB is used in Copilot for capabilities such as Cowork, Code, Autopilot, new agentic experiences in SharePoint, or when working with newer agentic frontier models such as Astra and Fable. UBB experiences consume Copilot Credits and require a USL for access.

## Usage-based billing user experience

Users can encounter UBB when they:

1. **Reach usage limits in the USL \(coming soon\):** Users receive in-product notifications as they approach an applicable limit. After reaching the limit, they have the option to continue with UBB by consuming Copilot Credits or, if applicable, reroute to Auto to continue their work.
2. **Use advanced AI or frontier models:** Users can encounter UBB when using advanced AI experiences, such as Cowork or Code, when using frontier models, or when trying to use an advanced AI capability in an experience, such as some advanced capabilities in SharePoint.

Over time, we will introduce additional UBB UX to help provide users with greater transparency and control, such as new ways to view their credit consumption or request credits from their admin.

Important

Admins must set up a billing policy before a user can use AI experiences that require usage-based billing. For more information, see [Understand usage-based billing and cost management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

## AI cost management \(FinOps for AI\)

FinOps for AI includes AI cost management and optimization. Admins can apply FinOps practices to manage your organization's AI spending. In the Microsoft 365 admin center, admins can set up, assign, and manage the Microsoft 365 Copilot user subscription license and usage-based Copilot Credits.

### User subscription license

#### Set up Copilot and assign licenses

There are different license options for Microsoft Copilot. The license you choose depends on your organization’s needs and any existing Microsoft 365 subscriptions you have.

For more information, see [Set up Microsoft Copilot and assign licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-setup).

### Usage-based billing

#### Use the cost management dashboard

The cost management dashboard in the Microsoft 365 admin center provides a centralized place to govern and monitor AI experiences enabled by usage-based billing. For more information, see [Use the cost management dashboard](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits#use-the-cost-management-dashboard).

#### Set up and configure usage-based billing

You can set up and govern how AI experiences based on usage-based billing are enabled and controlled across your organization.

The Configuration experience gives you a centralized place to enable usage-based billing and define how spending is managed. For more information, see [Set up and configure Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup).

#### Monitor Copilot Credits spending

You can get clear visibility into how and where Copilot is used and how to optimize it. For more information, see [Monitor Copilot Credits spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).
