<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-models -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Connect to SpaceXAI models \(as an independent processor\)

You can now use SpaceXAI models within your Microsoft products. These models are hosted by SpaceXAI outside of Microsoft. You can elect to use SpaceXAI models with Copilot Studio and with Copilot Cowork in Microsoft 365.

SpaceXAI models can help people in your organization with some of the following:

- Summarize complex information
- Answer questions using source material
- Synthesize across multiple sources
- Idea generation, drafting and editing

When your organization chooses to use a SpaceXAI model, your organization is choosing to share your data with SpaceXAI to power Copilot Studio and Copilot Cowork features. This data is processed outside all Microsoft managed environments and audit controls, therefore Microsoft's customer agreements, including the [Product Terms](https://www.microsoft.com/licensing/terms?msockid=344e0e6ad66c6b3e19441848d7416abd) and [Data Processing Addendum](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA?lang=18&msockid=344e0e6ad66c6b3e19441848d7416abd) don't apply. In addition, Microsoft's data residency commitments, audit and compliance requirements, service level agreements, and Customer Copyright Commitment don't apply to your use of SpaceXAI services. Instead, use of SpaceXAI services is governed by the [xAI Enterprise Terms of Service](https://x.ai/legal/terms-of-service-enterprise) and the [xAI Data Processing Addendum](https://x.ai/legal/data-processing-addendum#xai-data-processing-addendum).

## Before you begin

Before users in your organization can use SpaceXAI, they need to be assigned a [Microsoft Copilot license](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users).

## Connect to SpaceXAI in the Microsoft 365 admin center

Before your organization can connect to SpaceXAI models, you must allow access in the Microsoft 365 admin center.

You have to be a member of the Global administrator role to perform this task. For more information, see [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Copilot settings** page, select **View all**.
3. Select **AI providers for other large language models**.
4. Under **Available models for your organization**, choose **SpaceXAI**.
5. Review the **Legal terms**, and if they're acceptable, then select the **I have read and agree to the Terms and Conditions** checkbox.
6. Under **Choose which users can access SpaceXAI models**, select the users or groups that you want to have access, and then choose **Save**.

Note

You can restrict user access to AI independent providers by assigning permissions to specific users or Microsoft Entra ID security groups in the Microsoft 365 admin center. These assignments are applied at the provider level and enforced across Microsoft Copilot and Copilot Studio experiences. When access is limited by user or group membership, only the assigned users can use Copilot features or agents that rely on that AI provider. Review existing user or group assignments and update policies or configurations as needed. For more information on user and security group access, see [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access). For more information on creating security groups, see [Create a security group](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group).

After you connect, it may take a few hours for the connection to complete.

## Controls for Copilot Studio in the Microsoft Power Platform Admin Center

Once enabled in the Microsoft 365 admin center, additional administrator controls are available in the Microsoft Power Platform admin center to allow SpaceXAI to be used in Copilot Studio. For more information, see [Allow external large language models \(LLMs\) for generative responses](https://learn.microsoft.com/en-us/power-platform/admin/allow-llm-generative-responses).

## Disable connection to SpaceXAI

Your organization may decide that it no longer wants users to be able to connect to SpaceXAI models. You can disable connection to SpaceXAI models by doing the following steps:

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/) and select **Copilot** > **Settings**.
2. On the **Settings** page, select **View all**.
3. Select **AI providers for other large language models**.
4. Under **Available models for your organization**, choose **SpaceXAI**.
5. Under **Choose which users can access SpaceXAI models**, select **No users**, and then choose **Save**.

Once you disconnect SpaceXAI, users can't use SpaceXAI models. After completing the steps to disable SpaceXAI in Microsoft 365, it may take several hours for the service to be fully disabled for your users.
