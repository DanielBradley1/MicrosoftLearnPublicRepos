<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-create-tenant -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Create a governed workforce tenant

This article is for IT administrators who need to create an add-on tenant that is governed from an existing Microsoft Entra tenant. Review the prerequisites before you use the secure add-on tenant creation flow.

When you create a tenant using the **Governed Workforce** option in the Microsoft Entra admin center, the secure add-on tenant creation flow automatically:

- Creates the new workforce tenant
- Establishes a [governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships) between your home tenant and the new tenant if your home tenant has a default [governance policy template](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
- Provisions a [Microsoft Entra ID Free billing asset](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/microsoft-entra-id-free) under your selected Azure subscription and resource group

This article doesn't cover creating an external tenant configuration for consumer-facing apps. For customer identity and access management scenarios, see [Microsoft Entra External ID for customers](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam).

## Prerequisites

Before you create a governed workforce tenant, review the following requirements:

- Your home tenant has at least one paid, license-based Microsoft product \(for example, Microsoft Entra ID P1 or P2, Microsoft 365, or Windows Enterprise E3\). Free and trial licenses don't qualify.
- You have either a paid [Enterprise Agreement \(EA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/understand-ea-roles) or [Pay-As-You-Go](https://azure.microsoft.com/pricing/offers/ms-azr-0003p?cid=msft_learn) subscription. Both [Microsoft Online Subscription Agreement \(MOSA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts#microsoft-online-services-program) and [Microsoft Customer Agreement \(MCA\)](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts#microsoft-customer-agreement) billing accounts are supported. To identify your billing account type, see [View your billing accounts in the Azure portal](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/view-all-accounts).
- Your account has the [Tenant Creator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#tenant-creator) role. This role is required regardless of the [**Restrict non-admin users from creating tenants**](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#restrict-member-users-default-permissions) setting.
- You have the required Azure Resource Manager \(ARM\) permissions for the selected subscription through the **Tenant Contributor** or **Subscription Owner/Creator** role.
- \(Optional\) Your home tenant has a configured **default** [governance policy template](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates). The tenant creation service uses only the default template \(ID: `default`\). If the default template isn't defined, the secure add-on tenant creation flow doesn't establish a governance relationship, even if other templates exist.

## Create the tenant

For step-by-step instructions on creating a governed workforce tenant, see the **Governed Workforce** tab in [Quickstart: Create a new tenant in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/create-new-tenant).

## What happens after tenant creation

After the system creates the tenant:

1. If your home tenant has a [default governance policy template](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates), a governance relationship forms between your home tenant and the new tenant. The template provisions resources, including cross-tenant access settings, granular delegated admin privileges \(GDAP\) assignments, and service principals.
2. A [Microsoft Entra ID Free billing asset](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/microsoft-entra-id-free) appears in your Azure subscription under the resource group you selected.
3. The new tenant appears in your [related tenants](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/related-tenants) inventory.

To learn more about governance relationships and policy templates, see [Governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships) and [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates).

## Related content

- [Tenant governance overview](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/overview)
- [Governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships)
- [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
- [Quickstart: Create a new tenant in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/create-new-tenant)
