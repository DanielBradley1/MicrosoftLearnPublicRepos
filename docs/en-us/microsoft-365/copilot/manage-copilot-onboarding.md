<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-copilot-onboarding -->
<!-- Sitemap-Last-Modified: 2026-10-12 -->

# Manage Microsoft Copilot onboarding \(Frontier\)

Copilot onboarding is a guided, in-product experience that helps users build confidence with Microsoft Copilot. It includes short, personalized activities that help users discover the Copilot capabilities available to them based on their role and license, understand how those capabilities can support their work, and build skills through guided practice. Copilot onboarding is available to users with both starter and Premium licenses.

As an admin, you can configure Copilot onboarding in the Microsoft 365 admin center. Copilot onboarding gives your users a consistent starting point, lets you include your organization’s AI usage policy, and allows you to track completion.

## Setup at a glance

After your tenant joins the Frontier program and enables Frontier features, the Copilot onboarding settings become available in the Microsoft 365 admin center. You decide whether to set up and share the experience with users. To get started:

- **Confirm eligibility.** Check that your tenant and users meet the requirements in the next section.
- **Add your organization’s AI policy link.** This step is optional.
- **Share the experience.** Send users a link or a customizable email so they can start their personalized onboarding experience.
- **Monitor completion.** Check who's finished and follow up if you need to.

You'll find licensing, language support, privacy, and other details in the reference sections at the end of this article.

## Prerequisites

Review the following prerequisites before you configure Copilot onboarding. Some items are optional, depending on whether you want to include an AI policy or track completion.

| Requirement | What you need |
| --- | --- |
| Tenant approval | Your tenant must be enrolled in the Frontier program with Frontier features enabled. Microsoft then makes the onboarding setting available, but an eligible admin must configure and share the experience. EDU and government cloud tenants aren’t included. |
| Organization license | An eligible Microsoft 365 tenant-level subscription. To learn more, see the [Licensing details](#licensing-details) section. |
| Admin role | Global Administrator or Knowledge Administrator can manage settings and view reporting. An AI Administrator can manage settings but can't view reporting. |
| User license | Access to Copilot Chat through a Copilot license or an eligible Microsoft 365 Enterprise or Business subscription. Business Basic, Dynamics, and Teams-only licenses aren't supported. |
| Copilot Chat access | Turn on Copilot Chat for every user you plan to onboard. To review or change access, select the **Copilot Chat** link in the Microsoft Copilot onboarding settings pane. This link takes you directly to the setting where you can manage access. |
| Learning Agent | Turn on Learning Agent for every user you plan to onboard. To review or change access, select the Learning Agent link in the Microsoft Copilot onboarding settings pane. This link takes you directly to the setting where you can manage access.  <br>You can also go to **Agents > All Agents > Learning** in the Microsoft 365 admin center. For more information, see [Test and deploy Microsoft 365 apps, agents, and add-ins](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps). |
| Web Search Grounding | Must be turned on for the tenant. |
| Viva Learning | Optional. You need Viva Learning only if you want to track onboarding completion. Before you use reporting, turn on Viva Learning and confirm that the **AI and Copilot Resources** provider is enabled. This provider is enabled by default. Viva Learning Basic is included with Office 365 E1, E3, and E5; Microsoft 365 Business Basic, Standard, and Premium; and Microsoft 365 Enterprise E3 and E5. For setup instructions, see [Set up Viva Learning](https://learn.microsoft.com/en-us/viva/learning/set-up-viva-learning) and [Manage providers](https://learn.microsoft.com/en-us/viva/learning/use-tabs). |
| AI policy URL | **Optional.** Add one if you want users to review your organization's AI usage policy during onboarding. |

## Manage Copilot onboarding for your users

### Step 1: Confirm eligibility

- Make sure your tenant and users meet the requirements in [Prerequisites](#prerequisites).
- Go to **Copilot > Settings > [Microsoft Copilot onboarding settings](https://admin.cloud.microsoft/?#/copilot/overview/:/CopilotSettings/AdminLedCopilotTraining)** in the Microsoft 365 admin center.
- Sign in with an eligible admin role if prompted.

### Step 2: Add your AI policy link \(optional\)

If your organization has an AI usage policy, you can add it to the onboarding experience so users can review your organization’s AI policy during their onboarding.

1. Under **AI Policy**, paste the URL for your organization's AI usage policy.
2. Select **Save**.
3. Confirm that the setting saved.

If you don’t add a policy link, Copilot onboarding skips the AI policy section for your users. You can continue setting up and sharing the rest of the experience.

### Step 3: Share the experience with users

You can share Copilot onboarding in two ways: copy a link or download an email template.

#### Option 1: Copy a link

Under **Copy link options**, choose where you want users to open Copilot onboarding:

- **Copilot app**
- **Copilot web**
- **Copilot in Teams**

Copy the link and share it through your organization's preferred channel. Each link opens onboarding in the Copilot destination you picked.

#### Option 2: Download the email template

1. Select **Download template**.
2. Customize the email with details for your organization, such as the user group's name and launch information.
3. Send the email to your users.

The button in the email template opens Copilot onboarding in the Copilot app.

Let users know that onboarding takes about 10 to 15 minutes and provides a personalized introduction to the Copilot capabilities available to them. If you added an AI usage policy, they'll also review it as part of the experience.

Consider sending follow-up reminders directly to users who haven't completed onboarding.

### Step 4: Monitor completion

If you turned on Viva Learning, you can track Copilot onboarding completion in Viva Learning reporting.

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), and then go to **Copilot > Settings > Microsoft 365 Copilot onboarding**.
2. Under **Step 3**, select **Go to Viva Learning reporting**. The link opens the report directly.
3. Search for Copilot onboarding and review users’ completion status.
4. Follow up with users who haven’t completed onboarding, if needed.

Reporting shows completion status only. To learn more, see [Privacy and onboarding data](#privacy-and-onboarding-data).

## What users experience

After you share the link, users open a personalized onboarding experience in the destination you chose: the Copilot app on Windows, Copilot on the web, or Copilot in Teams. The activities and guidance are tailored to help users discover the Copilot capabilities available to them. To learn more about the Copilot onboarding experience for users, see [Complete Microsoft Copilot onboarding](https://support.microsoft.com/microsoft-365-copilot/complete-microsoft-copilot-onboarding).

## Plan your rollout

Copilot onboarding is a lightweight way to help users get started with Copilot through a personalized experience that introduces relevant capabilities and guidance based on their available Copilot access. You don't need to build a large training program around it. If you're planning a broader Copilot launch, you can start with a smaller group, learn from their experience, and expand when you're ready.

### 1. Prepare your communications

Give users a little context before they open onboarding. Consider including:

- Why your organization is introducing Copilot onboarding.
- Who's included in the rollout.
- Where users can open the experience.
- How long onboarding takes.
- Where users can find your organization's AI usage policy.
- Where users can go for help.

The downloadable email template gives you a starting point that you can customize.

### 2. Keep stakeholders informed

Copilot onboarding isn't a mandatory approval gate, but some teams might still want advance notice, including Security and Compliance, Legal, Communications, Learning and Development, and Human Resources. These teams can help you align onboarding communications, AI guidance, and completion tracking with processes your organization already uses.

## Reference

### Licensing details

There's no separate license or extra cost for Copilot onboarding. It uses the Microsoft 365 and Copilot access your users already have.

Your organization needs one of these tenant-level subscriptions:

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 Business Basic
- Microsoft 365 Business Standard
- Microsoft 365 Business Premium

Users need access to Copilot Chat through a Copilot license or a standard Microsoft 365 Enterprise or Business subscription. Business Basic, Dynamics, and Teams-only user licenses aren't supported.

### Platform and language support

| Platform | Support |
| --- | --- |
| Windows | Supported. Users need the Microsoft Copilot desktop app. |
| macOS | Not supported. |
| Web | Supported. Users can use Edge, Chrome, Firefox, and Safari. |
| Mobile \(iOS and Android\) | Not supported. |

| Language | Support |
| --- | --- |
| English | Supported. |
| Additional languages | Not supported. |

### Privacy and onboarding data

All onboarding activity stays within your Microsoft 365 tenant, and the access controls and tenant policies you already use still apply.

- Users' answers to onboarding questions aren't saved.
- Reporting shows completion status only. Admins can't see or export users' answers.
- Viva Learning reporting isn't a formal system of record. If you need an auditable training record, keep using your existing human resources information system \(HRIS\), learning management system \(LMS\), or other approved system.

### Common questions

**How do I pause or turn off onboarding?**

If you decide not to offer Copilot onboarding, you can stop sharing the onboarding link. Because you initiate the experience, your users won’t see it unless you invite them to participate. To remove the onboarding option from your tenant entirely, you’ll need to disable Frontier features. Any existing completion data is retained.

**Can users skip onboarding?**

Yes. Users can dismiss it and come back later. Use your rollout communications to set expectations before you share the link.

**Why doesn't completion reporting update right away?**

Completion data can take some time to show up. Treat it as a general progress signal, not a real-time compliance record.

**What if the examples don't match a user's role or skill level?**

Share that feedback with Microsoft so it can improve the personalized guidance, activities, and content shown during onboarding.

## Related articles

- [License options for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing)
- [Roll out Microsoft Copilot to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-rollout)
- [Manage Microsoft Copilot scenarios in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-page)
