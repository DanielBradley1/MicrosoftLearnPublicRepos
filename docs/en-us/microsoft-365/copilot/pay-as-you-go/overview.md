<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Microsoft Copilot pay-as-you-go service overview

The Microsoft Copilot pay-as-you-go service lets organizations access Copilot features with flexible, usage-based billing. This article explains how to set up pay-as-you-go billing, manage costs, and take advantage of scalable AI services for your organization.

Note

This article applies to Microsoft Copilot Chat, SharePoint Agents, and Microsoft Copilot Retrieval API \(Preview\).

Looking for information on Copilot Cowork or Work IQ API billing? These services are managed through the Microsoft admin center. See [Usage-based Billing and Cost Management for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits).

## What is a pay-as-you-go service?

The Microsoft Copilot pay-as-you-go service offers a flexible and scalable solution for organizations looking to use AI capabilities without the commitment of a full license. When you enable usage-based billing, administrators can better manage costs and provide users with access to Copilot features as needed.

The following services are available for pay-as-you-go billing:

- [Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/overview)
- [SharePoint agents](https://learn.microsoft.com/en-us/sharepoint/get-started-sharepoint-agents)
- [Microsoft Copilot Retrieval API \(Preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview)

For information about Copilot Studio pay-as-you-go billing, see [Copilot Studio pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#copilot-studio-pay-as-you-go).

The following list includes common use cases for Copilot pay-as-you-go services:

- **Establish usage patterns** - Admins can understand adoption patterns for new apps to determine if prepaid licenses make financial sense for your organization.
- **Scalability** - Organizations can scale their usage based on demand, paying only for the usage.

## How does the pay-as-you-go service work?

As an admin, when you use the pay-as-you-go service, you set up billing and users access declarative agents on a usage basis. You can manage billing, view costs, set spending budgets, and turn off services as needed.

The following administrator roles can view and manage pay-as-you-go services in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339):

- Global administrator
- Billing administrator
- AI administrator
- Global reader \(read-only access\)

Caution

Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.

To learn more about these roles, see [Microsoft 365 admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Understand the billing process

The billing process requires two steps:

1. Add a billing policy
2. Connect a billing policy to a Copilot service

### Add a billing policy

The billing policy acts as a unique billing identifier that you can associate with a group responsible for the incurred cost. The main objectives of a pay-as-you-go billing policy are:

- To allocate billing responsibilities across departments
- To facilitate the reuse of billing configurations across various pay-as-you-go scenarios
- To enable administrators to enforce governance
- To link users to a policy, establishing billing rules for a group of users

As an admin, you can add a budget limit to a billing policy and configure the budget to send email notifications when certain percentage milestones are reached.

For the steps to add or update a billing policy and add a budget, see [Set up Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).

#### What you need to know

- **Creating a billing policy** defines the billing infrastructure for a pay-as-you-go service that consists of an Azure subscription and a set of users. Creating a billing policy doesn't complete the billing setup. You must connect the billing policy to the Copilot service to complete the setup.
- **Deleting a billing policy** removes the billing infrastructure. Any connected services are disconnected from pay-as-you-go billing.

### Connect a billing policy to a Copilot service

After you create a billing policy, you must link it to a Copilot service, like Microsoft Copilot Chat or SharePoint agents. This connection grants access to the Copilot servie to all users covered by the billing policy.

As an admin, you can disconnect a billing policy when it's no longer needed for the service. Upon disconnection, users linked to that billing policy lose access to the metered agents in the Copilot service.

When you manage billing policies, the following conditions apply:

- Admins can connect or disconnect a billing policy one at a time.
- Before you connect to a user-specific billing policy, disconnect any existing "all users" billing policy.

## Process for new feature releases

When Microsoft adds new features that use pay-as-you-go billing, it announces them in a [message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center) post. When the new features are available, users in your organization can take advantage of their capabilities. By default, pay-as-you-go billing is disabled. A Global Administrator or subscription owner can enable or disable Microsoft 365 pay-as-you-go features in the Microsoft 365 admin center.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Pricing details

When you use a Microsoft pay-as-you-go service linked to an Azure subscription, the service gets billed through the Azure subscription that you specified when you set up pay-as-you-go billing. The Azure subscription uses the Azure meter set up for the service.

To learn more about meters, see [Meters for Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/meters).

## Monitoring and billing

You can monitor your organization's usage of the pay-as-you-go service in the Microsoft 365 admin center on the **Cost Management** page for each pay-as-you-go service that you use. To learn how to monitor the services, see [View costs and billing for Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/view-cost).

Administrators can also view the cost breakdown and analysis in the Azure portal. For more information, see [Microsoft Cost Management](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/overview-cost-management).

## Related articles

- [Set up Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup) \(article\)
- [Meters for Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/meters) \(article\)
- [View costs and billing for Microsoft Copilot pay-as-you-go services](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/view-cost) \(article\)
