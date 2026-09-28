<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/manage-microsoft-365-education-ai-features -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Manage Microsoft 365 for Education AI Features

Microsoft 365 for Education customers have access to many generative AI features included in their licensing. All generative AI features follow [Microsoft’s Responsible AI principles](https://www.microsoft.com/ai/responsible-ai), and access to generative AI features can be controlled by IT administrators.

## Teach in the Microsoft Copilot App

**Teach** in the Microsoft Copilot App is a home where educators can easily access AI-powered teaching tools to create lesson plans, draft materials like quizzes and rubrics, and quickly make modifications to language, reading level, length, difficulty, alignment to relevant standards, and more.

Teach is available to users with the following SKUs assigned and Microsoft Copilot Chat enabled:

- Microsoft 365 A1/A3/A5 for Faculty/Staff
- Office 365 A1/A1 Plus/A3/A5 for Faculty/Staff

Teach isn't available to students, enterprise or business customers, or consumer/personal accounts.

Teach is enabled by default and can be accessed in the Microsoft Copilot app on web, Windows, and Mac. Teach can be [accessed directly here.](https://copilot.cloud.microsoft/teach)

To disable Teach for select or all users, remove access Microsoft Copilot Chat following the instructions in step 2 at [Remove access to Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage#remove-access-to--chat).

**Learn more:**

- [Teach in the Microsoft Copilot App](https://aka.ms/teach/support) \(end users\)
- [Get started with the Microsoft Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-app-overview) \(IT admins\)

## Learning Activities

Learning Activities are a Microsoft Education experience designed to help educators and students transform passive content into active learning. With just a few selections, educators and students can now create engaging practice activities like flashcards directly from existing learning content or topics of their choice.

Learning Activities are available to users with the following SKUs:

- Microsoft or Office 365 A1/A3/A5 for Faculty/Staff
- Microsoft or Office 365 A1/A3/A5 for Students
- Microsoft 365 Business Basic/Business Standard/Business Premium
- Microsoft 365 E3/E5
- Microsoft 365 F1/F3
- Office 365 E1/E1 Plus/E3/E5
- Office 365 F3

Note

Availability for students is limited to students aged 13+. To help ensure appropriate access, admins must take additional steps to manage deployment: [Microsoft Copilot Chat for Students 13+ \| Microsoft Community Hub](https://techcommunity.microsoft.com/blog/EducationBlog/microsoft-365-copilot-chat-for-students-13/4412957).

Learning Activities aren't available for consumer or personal Microsoft 365 accounts.

Learning Activities are enabled by default, and available in the following places:

- The Learning Activities web app for educators and students
- Teach in the Microsoft Copilot app for educators
- Teams for Education Classwork and Assignments for educators and students
- Study Guide in Copilot Notebooks for educators and students
- The Study and Learn agent for educators and students
- Acivities can be access directly at [https://learningactivities.edu.cloud.microsoft/](https://learningactivities.edu.cloud.microsoft/)

Learning Activities Availability:

- Activity generation is available by default for eligible enterprise users, faculty and staff, and students aged 18 and older.
- Practice of activities shared by an educator is available by default for eligible students, including students under age 18.
- Activity generation is not available by default for students aged 13 to 17. To enable generation, admins must configure the student's Microsoft Entra ageGroup property as NotAdult. For instructions, see [Microsoft Copilot Chat for Students 13+](https://techcommunity.microsoft.com/blog/EducationBlog/microsoft-365-copilot-chat-for-students-13/4412957).
- Activity generation is not available for students under age 13.

**To disable Learning Activities:**

- Educators and students can access Learning Activities independent of Copilot chat. Generation remains off by default for students under 18.
- Admins can disable access for all users in PowerShell. In PowerShell \(only for Tenant Admins to disable Learning Activities for users in their tenant\):

  - Run the following PowerShell script:

    ```PowerShell
    Install-Module Microsoft.Graph.Authentication
    Connect-MgGraph -Scopes "Application.ReadWrite.All"
    $ServicePrincipal = Invoke-MgGraphRequest -Uri "/v1.0/servicePrincipals?`$filter=AppId eq '22d27567-b3f0-4dc2-9ec2-46ed368ba538'"
    Invoke-MgGraphRequest -Uri "/v1.0/servicePrincipals/$($ServicePrincipal.value.id)" -Method PATCH -Body @{ 'accountEnabled' = $false }
    ```

**To enable or disable Learning Activities in an Enterprise tenant \(admin\):**

Note

- You must be a Global admin or Office Apps admin to manage this setting.
- This setting applies to your entire organization. You can’t enable or disable Learning Activities for specific users or groups.

1. In the Microsoft 365 admin center \([https://admin.microsoft.com](https://admin.microsoft.com)\), go to **Settings > Org settings**.
2. In the **Services** tab, select **Learning Activities**.  [![Screenshot of org settings.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/learning-activities-org-settings.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/learning-activities-org-settings.png#lightbox)
3. In the **Learning Activities** panel, check or uncheck **Turn on Learning Activities**.

   - **Checked**: Learning Activities is available to users in your organization.
   - **Unchecked**: Learning Activities is disabled for all users in your organization.

4. Select **Save**.  [![Screenshot of saving learning activities org settings.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/learning-activities-org-settings-save.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/learning-activities-org-settings-save.png#lightbox)

A confirmation banner \(Changes saved.\) appears at the top of the panel to confirm your change.

Note

Changes may take up to 24 hours to take effect across your organization.

When Learning Activities is turned off, users who try to access Learning Activities see a sign-in error indicating that Learning Activities is disabled. This is expected behavior. Users won’t be able to access Learning Activities until an admin turns the feature back on.

## Generative AI in Teams for Education

Teams for Education enables educators to create collaborative classrooms, connect in professional learning communities, and communicate with students and guardians. Included in Teams for Education are generative AI features for educators to enhance the Assignments, Classwork, Reading Progress, and Insights apps.

Generative AI in Teams for Education is available to users with the following SKUs:

- Microsoft 365 A1/A3/A5 for Faculty/Staff
- Office 365 A1/A1 Plus/A3/A5 for Faculty/Staff

Generative AI features in Teams for Education are enabled by default. To disable these features, follow the instructions at [set up AI content recommendations in an institution](https://learn.microsoft.com/en-us/microsoftteams/institution-settings#enable-ai-for-educators).

Learn More:

- [Microsoft AI in Teams for Education \(end users\)](https://support.microsoft.com/topic/microsoft-ai-in-teams-for-education-8f0b37fa-dacd-412d-a170-c7bdcccbecc3)

## Transparency documentation and responsible AI FAQs

An AI system includes not only the technology, but also the people who use it, the people affected by it, and the environment in which it's deployed. Transparency documentation and FAQs are intended to help you understand:

- How AI technology works
- The choices system owners and users can make that influence system performance and behavior
- The importance of thinking about the whole system, including the technology, the people, and the environment

You can use transparency documentation and FAQs to better understand specific AI systems and features that Microsoft develops.

Transparency documentation and FAQs are a part of a broader effort to put our AI principles into practice. To find out more, see [Microsoft AI principles](https://www.microsoft.com/ai/responsible-ai).

Learn more about the capabilities and impacts of specific features:

- [AI Feedback Suggestions: Responsible AI FAQ](https://support.microsoft.com/topic/ai-feedback-suggestions-responsible-ai-faq-b67b6c78-a2fb-4f99-8ba5-0475150e4c89)
- [Rubric Generation: Responsible AI FAQ](https://support.microsoft.com/topic/rubric-generation-responsible-ai-faq-5d74dd6f-7a9c-4053-a3e1-0af50e94218b)
- [Instructions Generation: Responsible AI FAQ](https://support.microsoft.com/topic/instructions-generation-responsible-ai-faq-f44f9d1e-152e-4456-a3f8-b1bb0595eda8)
- [Lesson Plan - Transparency Document](https://support.microsoft.com/topic/lesson-plan-transparency-document-749b6a92-1013-48c0-8c76-b9c50de57bea)
- [Flashcards Transparency Document](https://support.microsoft.com/topic/flashcards-transparency-document-6704c843-36e9-43b3-ac4a-5138950bee30)
