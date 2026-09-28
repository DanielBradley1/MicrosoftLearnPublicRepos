<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-mistral-ai-models -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Connect to Mistral AI models

You can now use Mistral AI models within Copilot Studio. These models are hosted by Mistral outside of Microsoft. You can elect to use Mistral models with Microsoft 365 apps and features.

Mistral models can help people in your organization with some of the following:

- Summarize complex information
- Answer questions using source material
- Synthesize across multiple sources
- Idea generation, drafting and editing

When your organization chooses to use a Mistral model, your organization is choosing to share your data with Mistral to power Copilot Studio features. This data is processed outside all Microsoft managed environments and audit controls, therefore Microsoft's customer agreements, including the [Product Terms](https://www.microsoft.com/licensing/terms?msockid=344e0e6ad66c6b3e19441848d7416abd) and [Data Processing Addendum \(DPA\)](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA?lang=18&msockid=344e0e6ad66c6b3e19441848d7416abd) don't apply. In addition, Microsoft's data residency commitments, audit and compliance requirements, service level agreements, and Customer Copyright Commitment don't apply to your use of Mistral's services. Instead, use of Mistral’s services is governed by [Mistral Terms of Use for Microsoft](https://legal.mistral.ai/terms/terms-of-service-dpa-microsoft).

Important

Some Mistral services may be offered under preview terms. Mistral Medium 3.5 is offered in public preview. For more information, see [Remote agents in Vibe](https://mistral.ai/news/vibe-remote-agents-mistral-medium-3-5/). Mistral AI models offered in Copilot Studio are currently limited to Mistral Medium 3.5.

## Before you begin

Before users in your organization can use Mistral, they need to be assigned a [Microsoft 365 Copilot license](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users).

## Connect to Mistral in the Microsoft 365 admin center

Before your organization can connect to Mistral AI models, you must allow access in the Microsoft 365 admin center.

You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To enable connection to Mistral AI models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Copilot settings** page, select **View all**.
3. Select **AI providers for other large language models**.
4. Under **Available models for your organization**, choose **Mistral AI**.
5. Review the **Legal terms**, and if they're acceptable, then select the **I have read and agree to the Terms and Conditions** checkbox.
6. Under **Choose which users can access Mistral AI models**, select the users or groups that you want to have access, and then choose **Save**.

   ![Screenshot of the UI to configure the use of Mistral AI models in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/mistral-ui-admin-center.png)

After you connect, it may take a few hours for the connection to complete.

Note

You can restrict user access to AI subprocessors by assigning permissions to specific users or Microsoft Entra ID security groups in the Microsoft 365 admin center. These assignments are applied at the provider level and enforced across Microsoft Copilot and Copilot Studio experiences. When access is limited by user or group membership, only the assigned users can use Copilot features or agents that rely on that AI provider. Review existing user or group assignments and update policies or configurations as needed. For more information on user and security group access, see [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access). For more information on creating security groups, see [Create a security group](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

## Controls for Copilot Studio in the Microsoft Power Platform admin center

Once enabled in the Microsoft 365 admin center, additional administrator controls are available in the Microsoft Power Platform admin center to allow Mistral to be used in Copilot Studio. For more information, see [Allow external large language models for generative responses](https://learn.microsoft.com/en-us/power-platform/admin/allow-llm-generative-responses).

## Disable connection to Mistral in the Microsoft 365 admin center

Your organization may decide that it no longer wants users to be able to connect to Mistral AI models.

You must be a member of the [AI Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#ai-administrator) or [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to perform this task. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

To disable connection to Mistral AI models:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Settings** page, select **View all**.
3. Select **AI providers for other large language models**.
4. Under **Available models for your organization**, choose **Mistral AI**.
5. Under **Choose which users can access Mistral AI models**, select **No users**, and then choose **Save**.

Once you disconnect Mistral, users can't use Mistral AI models. After completing the steps to disable Mistral AI in Microsoft 365, it may take several hours for the service to be fully disabled for your users.
