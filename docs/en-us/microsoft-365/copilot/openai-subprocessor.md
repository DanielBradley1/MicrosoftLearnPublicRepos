<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/openai-subprocessor -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# OpenAI as a subprocessor in Microsoft Online Services

Important

The information in this article only applies to OpenAI models operated by OpenAI \(provided by OpenAI as a subprocessor\). The information doesn't apply to OpenAI models operated by Microsoft \(Azure OpenAI\).

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. There are no changes to security, compliance, and privacy for organizations.

Microsoft is expanding options for how OpenAI models can be delivered within Microsoft Online Services. In addition to OpenAI models that Microsoft operates \(Azure OpenAI\), Microsoft now provides OpenAI operated models through OpenAI as a subprocessor. This option gives your organization the foundation for more model flexibility, including quicker access to new AI model innovations, while maintaining enterprise-grade commitments and safeguards.

OpenAI was added to the Microsoft Online Services Subprocessors List on June 23, 2026. OpenAI as a subprocessor is available for use as of July 9, 2026. As a subprocessor, OpenAI operates with Microsoft oversight through contractual safeguards and appropriate technical and organizational measures. The [Microsoft Product Terms](https://www.microsoft.com/licensing/terms) and [Microsoft Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA) apply to use of OpenAI models through Microsoft's enterprise Online Services, except as otherwise disclosed in the [Exclusions section](#exclusions) at the end of this article. Such use is also covered under our [Enterprise Data Protection](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). Microsoft’s [Customer Copyright Commitment](https://blogs.microsoft.com/on-the-issues/2023/09/07/copilot-copyright-commitment-ai-legal-concerns/) applies to OpenAI models used within products covered by that commitment, including Microsoft Copilot and Copilot Studio.

For more information about subprocessor data access, see [Microsoft Data Access](https://www.microsoft.com/trust-center/privacy/data-access). To see a list of Microsoft subprocessors, see the [Service Trust Portal](https://aka.ms/subprocessor).

OpenAI operated models serve the same GPT-based Copilot experiences your users already have. In Copilot Studio, creators must select the model during agent creation. Consistent with the experience for OpenAI models operated by Microsoft \(Azure OpenAI\) in Copilot experiences, users can select a GPT model.

Note

- OpenAI models delivered through OpenAI as a subprocessor in Copilot experiences are currently excluded from in-country processing commitments when applicable.
- Access to OpenAI operated models isn't currently available for use in government clouds \(GCC, GCC High, DoD\) or sovereign clouds.
- OpenAI operated models are included in the EU Data Boundary, except as otherwise noted in the [EU Data Boundary documentation](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-ongoing-partial-transfers#approved-third-party-ai-subprocessors).

## Manage OpenAI as a subprocessor in the Microsoft 365 admin center

As of July 24, 2026, OpenAI operated models are enabled for all users for eligible commercial customers, unless you specifically [disable the use of OpenAI operated models](#disable-the-use-of-openai-operated-models) by selecting **No users** for the setting in the Microsoft 365 admin center.

## Enable the use of OpenAI operated models

You can choose to enable OpenAI operated models so that they're available for your organization. You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To enable the use of OpenAI operated models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **OpenAI**.
4. Under **Choose which users can access OpenAI operated models**, select **All users**, or specify users and groups, and then select **Save**.

![Screenshot of the UI to configure the use of OpenAI models in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/openai-subproc-admin-center-ui.png)

You can restrict user access to AI provider subprocessors by assigning permissions to specific users or Microsoft Entra ID security groups in the Microsoft 365 admin center. These assignments are applied at the provider level and enforced across Microsoft Copilot and Copilot Studio experiences. When access is limited by user or group membership, only the assigned users can use Copilot features or agents that rely on that AI provider. Review existing user or group assignments and update policies or configurations as needed. For more information on user and security group access, see [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access). For more information on creating security groups, see [Create, edit, or delete a security group in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

Some features or models are only available when OpenAI operated models are enabled. If you disable OpenAI as a subprocessor, certain features or models may no longer be accessible.

## Disable the use of OpenAI operated models

You can disable the use of OpenAI operated models in the Microsoft 365 admin center. You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To disable the use of OpenAI operated models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **OpenAI**.
4. Under **Choose which users can access OpenAI operated models**, select **No users**, and then select **Save**.

After you disable OpenAI as a subprocessor, users won't have the option to use OpenAI operated AI models. You can choose to enable OpenAI operated models at a later date if desired.

## Additional controls for Copilot Studio and Power Platform in the Power Platform admin center

After enabled in the Microsoft 365 admin center, additional admin controls are available in the Microsoft Power Platform admin center to allow OpenAI operated models to be used in Copilot Studio and Power Platform. For more information, see [Allow external large language models \(LLMs\) for generative responses](https://learn.microsoft.com/en-us/power-platform/admin/allow-llm-generative-responses).

## Exclusions

The following exclusions apply:

- Certifications for OpenAI operated models in Microsoft Online Services are maintained and managed by OpenAI. You should refer to [OpenAI’s own certification landing page](https://trust.openai.com/) to understand the availability of their certifications, additional exclusions, and audit reports.
- OpenAI operated models available through Microsoft aren't FedRAMP High authorized. If your organization requires FedRAMP High prior to use, consult with your authorization official to determine whether use of OpenAI operated models is permitted within your environment.
- Microsoft incorporates OpenAI's Responses API into certain Copilot experiences. OpenAI offers Zero Data Retention for the Responses API used by Microsoft, subject to the limitations and feature-specific data handling practices for Responses API described in OpenAI's [Data controls in the OpenAI platform](https://developers.openai.com/api/docs/guides/your-data) documentation.

## Related articles

- [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Overview of AI subprocessors in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-subprocessor-overview)
- [Supplier Security & Privacy Assurance](https://www.microsoft.com/procurement/sspa)
