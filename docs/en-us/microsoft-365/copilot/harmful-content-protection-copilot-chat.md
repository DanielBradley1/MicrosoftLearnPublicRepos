<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/harmful-content-protection-copilot-chat -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Manage harmful content protection settings for Microsoft Copilot Chat

Microsoft Copilot uses content filtering to protect users from harmful content in user prompts and generated responses \(see [How does Copilot block harmful content?](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#how-does-copilot-block-harmful-content)\). However, in certain use cases, such as in investigation, law enforcement, legal review, or social work scenarios, it's important to adjust responsible harmful content protections appropriately. For these special use cases, your organization's Microsoft 365 Apps administrator can enable a specific group of users to adjust harmful content protection settings in their Copilot Chat experiences. This configuration allows Copilot Chat to respond to queries about harmful content.

Important

Core responsible AI protections, such as prompt injection defense, copyright safeguards, biosecurity, and image protections are always enforced and can't be disabled.

When you configure an `Adjust responsible AI protections for Microsoft 365 Copilot` policy, your policy doesn't affect images or agents. Default content filters remain in place for images and agents, even when users disable harmful content protection in a Copilot Chat conversation. Disabling harmful content protection applies only to text responses.

## How harmful content protection settings work

When you apply a policy to adjust AI protections, the users included in the policy can use a toggle to enable or disable harmful content protection in Copilot Chat. Their menu includes a **Harmful content protection** setting, as shown in the following screenshot:

[![Screenshot showing the More menu in Microsoft Copilot Chat.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/copilot-chat-more-menu.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/copilot-chat-more-menu.png#lightbox)

By default, the **Harmful content protection** setting is enabled at the beginning of each conversation. If necessary, the user can set the toggle to off to disable harmful content protection for the duration of the conversation.

- When this setting is *enabled*, harmful content is blocked in Copilot Chat.
- When this setting is *disabled*, the user can query on harmful content within the context of that conversation. In this case, the user might see sensitive or potentially offensive content related to their queries.

Once a user disables harmful content protection in a conversation in Copilot Chat, they can't re-enable it until a new conversation is started.

Only users who are included in the `Adjust responsible AI protections for Microsoft 365 Copilot` policy have the option to disable harmful content protection. All other users don't see the toggle.

Note

Regardless of whether harmful content protection is enabled or disabled, [Responsible AI governance](https://www.microsoft.com/en-us/ai/principles-and-approach), including prompt injection defense, copyright safeguards, and image protection, continues to be enforced.

## How to configure harmful content protection settings

Caution

When you turn off harmful content protection, Copilot Chat responses can include sensitive or potentially offensive content that violates the [Microsoft Generative AI Services Code of Conduct](https://learn.microsoft.com/en-us/legal/ai-code-of-conduct).

1. Set up or identify a security group in Microsoft Entra ID. The group should include only those users who need to temporarily disable harmful content protection for certain scenarios, such as investigation, law enforcement, legal review, or similar use cases.

   To get help with your security group, see [Learn about group types, membership types, and access management](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups).
2. As an Office Apps Administrator \(or Global Administrator\), sign in to the [Microsoft 365 Apps admin center](https://config.office.com). \(Note that the Microsoft 365 Apps admin center isn't the Microsoft 365 admin center.\)

   Important

   Use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that you should limit to emergency scenarios when you can't use an existing role. [Learn more about administrator roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).
3. In the navigation pane, select **Customization**.

   [![Screenshot showing the Customization section in the Microsoft 365 App admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/microsoft-365-apps-admin-center-customization.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/microsoft-365-apps-admin-center-customization.png#lightbox)
4. Create or edit a policy configuration for **Adjust responsible AI protections for Microsoft Copilot**.

   [![Screenshot showing the Adjust responsible AI protections flyout pane.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/adjust-responsible-ai-protections.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/adjust-responsible-ai-protections.png#lightbox)
5. In the flyout pane, specify your configuration settings as follows:

   [![Screenshot showing configuration options for the Adjust responsible AI protections policy.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/adjust-responsible-ai-protections-options.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/harmful-content-protection-copilot-chat/adjust-responsible-ai-protections-options.png#lightbox)

   1. Under **Configuration setting**, select **Enabled**.
   2. Under **Options**, select an option, such as **Provide users with the option to adjust harmful content protection**.
   3. Select **Apply**.

6. Apply your policy to the security group you created in Step 1 and save your changes.

When the policy takes effect, the users who are included in the policy have the **Harmful content protection** toggle in their Copilot Chat experience. [Learn more about the user experience](https://support.microsoft.com/en-us/topic/605db862-b859-4ec3-9327-d405cc164690).

Note

Harmful content protection settings apply only to text responses. Default content filters remain in place for images and agents, even if harmful content protection is disabled in a Copilot Chat conversation.

## Best practices and important points

- Use a security group in Microsoft Entra ID for your harmful content protection policies. Only include users who need this feature, such as those doing investigative work in law enforcement, legal, or social work scenarios. Not everyone in your organization needs to turn off harmful content protection.
- Let users know how the feature works and when to use it. For more information about the user experience, see [Using the harmful content protection toggle in Microsoft Copilot Chat](https://support.microsoft.com/en-us/topic/605db862-b859-4ec3-9327-d405cc164690).

## Related articles

- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/security-microsoft-365-copilot)
- [Application card: Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-application-card)
