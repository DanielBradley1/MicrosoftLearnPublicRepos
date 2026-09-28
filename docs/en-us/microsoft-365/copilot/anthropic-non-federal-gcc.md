<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/anthropic-non-federal-gcc -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Anthropic operated models for non-federal customers in GCC

Note

- The information in this article applies only to non-federal customers in Government Community Cloud \(GCC\). It doesn’t apply to federal customers in GCC or to all customers in GCC High and Department of Defense \(DoD\) environments.
- For information about Anthropic as a subprocessor, see [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

As of July 22, 2026, a new setting is available in the Microsoft 365 admin center that allows non-federal customers in Government Community Cloud \(GCC\) to use Anthropic models. This capability is optional and the setting is disabled by default.

This setting allows non-federal GCC customers to use Anthropic-powered AI features in supported workflows, subject to specific technical, contractual, and compliance boundaries.

Important

When enabled, these Anthropic AI models process Customer Data outside Microsoft’s FedRAMP-authorized U.S. Government cloud. You should evaluate whether enabling this setting is consistent with your organization’s data handling requirements. For more information, see [Compliance considerations for using Anthropic operated models](#compliance-considerations-for-using-anthropic-operated-models).

If you choose to enable Anthropic models for your organization, users with a Microsoft 365 Copilot \(Premium\) license have access to Anthropic models. Currently, those models appear as an option in the dropdown model picker only in Copilot Chat in the Microsoft Copilot app and on the web.

## Configure the use of Anthropic operated models

You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To enable the use of Anthropic operated models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **Anthropic**.
4. Review the information in the **Terms and conditions** section, and if they’re acceptable, select the **I acknowledge and agree to the above terms** checkbox.
5. Under **Choose which users can access Anthropic models**, select **All users**, or specify users and groups, and then select **Save**.

To disable the use of Anthropic models, select **No users** in Step 5. After you disable Anthropic as a subprocessor, users won't have the option to use Anthropic operated models. You can choose to enable Anthropic operated models at a later date if desired.

## Compliance considerations for using Anthropic operated models

The following sections provide information about compliance considerations for non-federal customers in GCC when using Anthropic operated models.

### Data handling and use restrictions

- Customer Data isn’t used to train Anthropic’s foundation models or any other foundation models used by Microsoft 365 Copilot.
- Customer prompts and responses are processed solely for service provisioning and abuse monitoring, in accordance with [Microsoft Product Terms](https://www.microsoft.com/licensing/docs/view/Product-Terms), [Microsoft Products and Services Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA), and applicable privacy commitments.

### Data residency and transfer

- If you choose to enable Anthropic models, Customer Data will be processed in commercial environments. This doesn’t align with GCC expectations for sovereign processing.
- Customers must evaluate whether processing outside the GCC boundary is consistent with their organization’s requirements before enabling Anthropic models.

### Regulatory and compliance scope

- Anthropic capabilities in GCC aren’t covered under FedRAMP Moderate or DoD Security Requirements Guide \(SRG\) authorizations. Also, these capabilities aren’t included in existing compliance attestations, including Criminal Justice Information Services \(CJIS\), Internal Revenue Service \(IRS\) 1075, or similar regulated workloads.
- Customers must not use Anthropic-enabled features for regulated workloads that require in-boundary processing or higher accreditation levels.

### Feature and workload limitations

The following use cases aren’t supported:

- Processing Controlled Unclassified Information \(CUI\), classified, export-controlled, or highly sensitive government data.
- Use in workloads requiring strict auditability or full control-plane isolation.

### Administrative control and visibility

Tenant administrators are responsible for the following:

- Coordinating with their organization's compliance and procurement stakeholders before enabling Anthropic models in their tenant.
- Ensuring appropriate user access policies and data governance controls are in place if they choose to enable Anthropic models.

Note the following about audit logging and reporting that is currently available:

- It may not provide full granularity of Anthropic-specific interactions.
- It shouldn’t be relied on as the sole mechanism for regulatory notice or compliance documentation.
