<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# Anthropic models in Microsoft Online Services

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. There are no changes to security, compliance, and privacy for organizations.

Microsoft is introducing a new offering with Anthropic AI models as part of Microsoft Online Services, delivering enterprise-grade commitments and safeguards to ensure secure and responsible use of Anthropic models within your organization.

To enable this change, Anthropic has onboarded as a Microsoft subprocessor. This change simplifies the experience and strengthens compliance and security under Microsoft's enterprise framework. The Microsoft Customer Copyright Commitment \(CCC\) applies to Anthropic models used within products covered by the CCC, including Microsoft Copilot and Copilot Studio.

As a subprocessor, Anthropic operates with Microsoft oversight through contractual safeguards and appropriate technical and organizational measures. Unless models are labeled "Anthropic models with Data Retention," the [Microsoft Product Terms](https://www.microsoft.com/licensing/terms) and [Microsoft Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA) apply to the use of Anthropic models through Microsoft's enterprise Online Services. Such use is also covered under our [Enterprise Data Protection](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). Anthropic models have built-in safeguards, instantiated and operated by Anthropic, to detect illegal content. Anthropic strictly prohibits Child Sexual Abuse Material \(CSAM\) on its services. For more information about these safeguards, see Anthropic’s [CSAM Detection and Reporting](https://support.claude.com/articles/9020328-csam-detection-and-reporting).

For more information about subprocessor data access, see [Microsoft Data Access Management](https://www.microsoft.com/trust-center/privacy/data-access). To see a list of Microsoft subprocessors, see [Service Trust Portal](https://aka.ms/subprocessor).

Microsoft enables Anthropic models on by default for most customers in commercial cloud \(excluding EU/EFTA and UK\). This update gives users in your organization the ability to use multiple AI models in their Microsoft offerings, such as in Microsoft Copilot, Researcher, Copilot Studio, Power Platform, and Copilot in Microsoft 365 apps. This affirms Microsoft's commitment to offering choice between leading AI models while maintaining enterprise-grade security and compliance.

Important

- Anthropic models deployed in Microsoft offerings such as Microsoft Copilot, Researcher, Copilot Studio, Power Platform, and Copilot in Microsoft 365 apps are currently excluded from the EU Data Boundary, and when applicable, in-country processing commitments. Customers within the EU Data Boundary and customers in the UK have Anthropic models disabled by default.
- For information about the availability of Anthropic models in U.S. government clouds \(GCC, GCC High, DoD\) and other sovereign clouds, see [Opt-in regions and exclusions](#opt-in-regions-and-exclusions).

Note

From time to time, some newly available and advanced models from Anthropic may still be made available with separate controls that allow Microsoft tenant admins to opt in to use certain models under Anthropic's separate [commercial terms](https://www.anthropic.com/legal/commercial-terms) and [data processing agreement](https://www.anthropic.com/legal/data-processing-addendum). For example, different terms apply to Anthropic models with Data Retention, and these models must always be separately enabled even where other Anthropic models are on by default.

## Manage Anthropic's Claude model settings in the Microsoft 365 admin center

Microsoft is making Anthropic models available by default in certain regions. In Microsoft Copilot \(web, desktop, and mobile\), UI indicators show when Claude models are in use. In Copilot Studio, creators must select the model during agent creation. In capabilities such as Edit with Copilot in Microsoft 365 apps or Researcher, users can select **Claude**.

## Opt-in regions and exclusions

In some regions, Anthropic's models aren't available by default. For these regions, the **AI providers operating as Microsoft subprocessors** setting for Anthropic models appears but the default is set to **No users**. These regions include the European Union \(EU\), the European Free Trade Association \(EFTA\), and the United Kingdom \(UK\).

Note

On April 3, 2026, Microsoft introduced a new Microsoft 365 admin center setting **Copilot in Microsoft 365 apps with Anthropic models** in EU/EFTA and UK to enable Anthropic as the default model for Copilot in Microsoft 365 apps. For more information, see [Copilot in Microsoft 365 apps with Anthropic models](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-anthropic-apps).

As of July 22, 2026, a new setting is available in the Microsoft 365 admin center that allows non-federal customers in Government Community Cloud \(GCC\) to use Anthropic models. For more information, see [Anthropic operated models for non-federal customers in GCC](https://learn.microsoft.com/en-us/microsoft-365/copilot/anthropic-non-federal-gcc).

Anthropic models aren't available for federal customers in GCC or for any customers in GCC High and Department of Defense \(DoD\) environments. They're also not available in other sovereign clouds. The option to use Anthropic models doesn't appear in the Microsoft 365 admin center for these government and sovereign cloud customers.

## Opt-in to use Anthropic's models

If your organization is in a region that has Anthropic as a subprocessor set to **Off** by default, you can choose to opt in so Anthropic's models are available for your organization. You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

1. Go to the Microsoft 365 admin center and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **Anthropic**, and **Save**.
4. Under **Choose who can access Anthropic models for Copilot and generative AI experiences**, select your users or groups and **Save**.

![Screenshot of the choice in the Microsoft 365 admin center UI to use Anthropic models](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/anthropic-subproc-admin-center-ui.png)

Note

You can restrict user access to AI provider subprocessors by assigning permissions to specific users or Microsoft Entra ID security groups in the Microsoft 365 admin center. These assignments are applied at the provider level and enforced across Microsoft Copilot and Copilot Studio experiences. When access is limited by user or group membership, only the assigned users can use Copilot features or agents that rely on that AI provider. Review existing user or group assignments and update policies or configurations as needed. For more information on user and security group access, see [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access). For more information on creating security groups, see [Create a security group](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

If your organization is in the European Union \(EU\), the European Free Trade Association \(EFTA\), or the United Kingdom and you previously opted in to use Anthropic models under Anthropic's separate commercial terms and data processing agreement, you need to opt in again. The toggle is set to **Off** by default.

Some features are only available when Anthropic models are enabled. If you turn off Anthropic as a subprocessor, certain features may no longer be accessible.

## Anthropic Fable-class models

Certain Anthropic models, such as Fable 5.0 and Fable 5.1, may be made available to your organization with different or additional terms \(“Fable-class models”\).

Depending on your organization’s eligibility, some Fable-class models may be available to your organization with Anthropic acting as a subprocessor. For example, for certain organizations, Fable 5.1 is available with Anthropic acting as a subprocessor and Microsoft's Product Terms and Data Protection Addendum \(DPA\) apply. For these organizations, no additional terms apply, and Anthropic doesn't retain customer content \(including prompts and responses\). As long as your organization has enabled Anthropic models under the **AI providers operating as Microsoft subprocessors** setting in the Microsoft 365 admin center, no other opt-in is required. Contact your account team if you have questions about your organization’s eligibility.

Other Fable-class models may be provided as “Anthropic models with Data Retention” and require your organization to agree to Anthropic’s terms as described in the next section.

## Opt-in to allow use of Anthropic models with Data Retention

Anthropic models with Data Retention are advanced models \(such as [Claude Fable 5 and Claude Mythos 5](https://support.claude.com/articles/15425996-data-retention-practices-for-mythos-class-models)\) that require data retention by Anthropic. This means data is stored by Anthropic and not subject to your Microsoft Customer Agreement including commitments in the Product Terms and DPA. Anthropic models with Data Retention \(such as Fable 5.0\) have additional controls in the Microsoft 365 admin center and are off by default for all scenarios, including in regions when different Anthropic models are on by default in commercial cloud and for which Anthropic is a Microsoft subprocessor. No users will have access to these models until the tenant admin explicitly opts in to enable use of Anthropic models with Data Retention. In this scenario, Anthropic acts as an independent processor and use of Anthropic models with Data Retention is subject to acceptance of Anthropic's [Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms) and Anthropic's [Data Protection Addendum](https://www.anthropic.com/legal/data-processing-addendum). The tenant admin must also choose which users \(all or specific users or groups\) can access and use these models.

When users within your organization are granted access to Anthropic models with Data Retention, users will also be able to identify in the product experience that these models require data retention by Anthropic.

When you enable use of Anthropic models with Data Retention, Anthropic retains data as explained in Anthropic's commercial data retention policy: [Data retention for Mythos-class models](https://support.claude.com/en/articles/15425996-data-retention-practices-for-mythos-class-models) This means that Anthropic \(not Microsoft\) stores most inputs and outputs for up to 30 days before deleting them. If Anthropic's trust and safety classifiers identify potential violations of Anthropic's Usage Policy, Anthropic may retain content \(inputs and outputs\) for up to two years and trust and safety classification scores for up to seven years. Anthropic doesn't use retained data for model training without your express permission. For more information, see [API and data retention - Claude API Docs](https://platform.claude.com/docs/en/manage-claude/api-and-data-retention).

## Additional controls for Copilot Studio and Power Platform in the Power Platform Admin Center

Once enabled in the Microsoft 365 admin center, additional admin controls are available in the Microsoft Power Platform admin center \(PPAC\) to allow Anthropic to be used in Copilot Studio and Power Platform. For more information, see [Allow external large language models \(LLMs\) for generative responses](https://learn.microsoft.com/en-us/power-platform/admin/allow-llm-generative-responses).

## Disable connection to Anthropic's models

If your organization is in a region that has Anthropic as a subprocessor set to **On** by default, you can opt-out to restrict Anthropic models in the Microsoft 365 admin center. You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

1. Go to the Microsoft 365 admin center and select **Copilot** > **Settings**.
2. On the **User access** page, select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **Disable Anthropic as a Microsoft subprocessor**.

Once you disable Anthropic as an AI subprocessor, users won't have the option to use Anthropic's AI models. You can choose to enable Anthropic models at a later date if desired.

## Allow the use of Preview models

Preview models are the latest models that may, from time to time, be available for exploration and testing but aren't recommended for production use. [Review the limitations of preview models.](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-preview-ai-models)

## Related articles

- [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Overview of AI subprocessors in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-subprocessor-overview)
- [Supplier Security & Privacy Assurance](https://www.microsoft.com/procurement/sspa?msockid=344e0e6ad66c6b3e19441848d7416abd)
