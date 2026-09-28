<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/spacexai-subprocessor -->
<!-- Sitemap-Last-Modified: 2026-09-18 -->

# SpaceXAI as a subprocessor in Microsoft Online Services

Important

- The information in this article applies only to organizations that are enrolled in the [Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier). Because this is a preview service under the Frontier program, you’re responsible for assessing whether SpaceXAI operated models are appropriate for use in your organization.
- The information in this article doesn’t apply to the following customers, even if they’re enrolled in the Frontier program: in the European Union \(EU\), in the European Free Trade Association \(EFTA\), in the United Kingdom, using government clouds \(GCC, GCC High, or DoD\), or using sovereign clouds.

Microsoft is explanding model choice across Microsoft Online Services by making SpaceXAI models available in supported Microsoft Copilot experiences through SpaceXAI as a subprocessor. This gives organizations access to additional model options and new AI innovations. At initial availability, Grok models provided by SpaceXAI as a subprocessor are supported only in Microsoft Copilot in Word, Excel, and PowerPoint by using the model selector. SpaceXAI models in Copilot Studio continue to be available through [SpaceXAI as an independent processor](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-models).

Note

- SpaceXAI was added to the Microsoft Online Services Subprocessors List on September 10, 2026.
- SpaceXAI as a subprocessor is available for use to eligible customers as of September 18, 2026.

As a subprocessor, SpaceXAI operates with Microsoft oversight through contractual safeguards and appropriate technical and organizational measures. The [Microsoft Product Terms](https://www.microsoft.com/licensing/terms) and [Microsoft Data Protection Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA) apply to use of SpaceXAI models through Microsoft's enterprise Online Services, except as otherwise disclosed in the [Exclusions section](#exclusions) at the end of this article. Such use is also covered under our [Enterprise Data Protection](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). Microsoft’s [Customer Copyright Commitment](https://blogs.microsoft.com/on-the-issues/2023/09/07/copilot-copyright-commitment-ai-legal-concerns/) applies to SpaceXAI models used within products covered by that commitment, including Microsoft Copilot in Word, Excel, and PowerPoint.

Before new or updated models are introduced, they undergo extensive testing and safety validation, and are reviewed against Microsoft's Responsible AI requirements.

For more information about subprocessor data access, see [Microsoft Data Access](https://www.microsoft.com/trust-center/privacy/data-access). To see a list of Microsoft subprocessors, see the [Service Trust Portal](https://aka.ms/subprocessor).

## Manage SpaceXAI as a subprocessor in the Microsoft 365 admin center

Currently SpaceXAI operated models are disabled for all eligible customers. You [can choose to enable these models](#enable-the-use-of-spacexai-operated-models) in the Microsoft 365 admin center at any time based on your organization's preference.

Note

- This new subprocessor setting in the Microsoft 365 admin center is different than the SpaceXAI setting under **AI providers for other large language models**. For more information on that setting, see [Connect to SpaceXAI models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-models).
- If you previously used the SpaceXAI setting under **AI providers for other large language models** to provide your users with access to SpaceXAI models, and you now want to use SpaceXAI as a subprocessor, you need to enable the new subprocessor setting and assign the appropriate users or groups. Your previous settings aren’t automatically carried over to the new subprocessor setting.

## Enable the use of SpaceXAI operated models

You can choose to enable SpaceXAI operated models so that they're available for your organization.

You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To enable the use of SpaceXAI operated models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **SpaceXAI**.
4. Under **Choose which users can access SpaceXAI operated models**, select **All users**, or specify users and groups, and then select **Save**.

![Screenshot of the UI to configure the use of SpaceXAI models in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/spacexai-subproc-admin-center-ui.png)

You can restrict user access to AI provider subprocessors by assigning permissions to specific users or Microsoft Entra ID security groups in the Microsoft 365 admin center. These assignments are applied at the provider level and enforced across Microsoft Copilot experiences. When access is limited by user or group membership, only the assigned users can use Copilot features or agents that rely on that AI provider. Review existing user or group assignments and update policies or configurations as needed. For more information on user and security group access, see [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access). For more information on creating security groups, see [Create, edit, or delete a security group in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

Some features or models are only available when SpaceXAI operated models are enabled. If you disable SpaceXAI as a subprocessor, certain features or models may no longer be accessible.

## Disable the use of SpaceXAI operated models

You can disable the use of SpaceXAI operated models in the Microsoft 365 admin center.

You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To disable the use of SpaceXAI operated models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings** > **View all**.
2. Select **AI providers operating as Microsoft subprocessors**.
3. On the **AI providers operating as Microsoft subprocessors** page, under **Available subprocessors for your organization**, select **SpaceXAI**.
4. Under **Choose which users can access SpaceXAI operated models**, select **No users**, and then select **Save**.

After you disable SpaceXAI as a subprocessor, users won't have the option to use SpaceXAI operated models. You can choose to enable SpaceXAI operated models at a later date if desired.

## Exclusions

The following exclusions apply:

- Certifications for SpaceXAI operated models in Microsoft Online Services are maintained and managed by SpaceXAI. You should refer to [SpaceXAI's own certification landing page](https://trust.x.ai/) to understand the availability of their certifications, additional exclusions, and audit reports.
- SpaceXAI operated models available through Microsoft aren't FedRAMP High authorized. If your organization requires FedRAMP High prior to use, consult with your authorization official to determine whether use of SpaceXAI operated models is permitted within your environment.
- SpaceXAI operated models in Copilot experiences are currently excluded from in-country processing commitments when applicable.

## Related articles

- [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Overview of AI subprocessors in Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-subprocessor-overview)
- [Supplier Security & Privacy Assurance](https://www.microsoft.com/procurement/sspa)
