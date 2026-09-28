<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-design -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 1: Design a Microsoft Exchange Online deployment in education environments

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft Exchange is a key component of the education offering for the Microsoft ecosystem. Microsoft Exchange Online is a hosted messaging solution that delivers email, calendar, contacts, and tasks from PCs, the web, and mobile devices. It integrates fully with Microsoft Entra ID, enabling administrators to use group policies, as well as other administration tools, to manage Exchange Online features across their environment.

This article is relevant to administrators of Exchange Online and describes requirements and best practices specific to deployment, implementation, and setup in educational environments.

## Roles and responsibilities

- IT Admin
- Identity Admin
- EXO Admin

## Methods to use

Alignment of Exchange Online to best-practice models is best accomplished through Desired State Configuration \(DSC\). DSC is a declarative PowerShell-driven capability that allows defining how a Microsoft 365 tenant should be configured, automates the deployment of that configuration, monitors, and detects configuration drift. Microsoft365DSC is open-source, GitHub-hosted, led by Microsoft engineers, and maintained by the community. Learn more in the [Microsoft365DSC documentation](https://microsoft365dsc.com). Adding [Azure DevOps](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/devops/manage-microsoft-365-tenant-configuration-microsoft365dsc-devops) in conjunction with Microsoft365DSC provides a complete Infrastructure as Code solution.

Also, the [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/exchange-online-powershell?view=exchange-ps&preserve-view=true) module can be used to enumerate configuration settings. Exchange Online PowerShell V3 \(EXO V3\) and later use REST API connections for all cmdlets. Microsoft Graph is another API that can manage Exchange Online and is the best alternative to Exchange Web Services \(EWS\), especially for managing at the object level \(mailboxes, contacts, calendars for example\). [Learn more about the retirement of EWS.](https://techcommunity.microsoft.com/t5/exchange-team-blog/retirement-of-exchange-web-services-in-exchange-online/ba-p/3924440)

## Exchange Online design decisions

- Microsoft 365 Tenant: Single tenant is recommended.
- Deployment Type: Exchange Online only \(hybrid with on-premises Exchange servers isn't recommended\).

### Protocols

- The default messaging protocol for the Outlook desktop is MAPI and is recommended.
- IMAP and POP protocols aren't recommended and can be disabled.
- The EWS protocol for programmatic access to mailboxes is being deprecated and replaced by Microsoft Graph.

### Authentication

Basic authentication \(ID and password only\) in Exchange Online is being [deprecated](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online) and Modern Authentication will be required.

### Outlook on the Web

- A3 and A5 licensees can disable access via Outlook on the Web. There's no requirement or recommendation to do so; enabling OWA doesn't present any additional security risks.
- A1 licensees can only use Outlook on the Web.

### Journaling

[Journaling](https://learn.microsoft.com/en-us/exchange/security-and-compliance/journaling/journaling) is the recording of email communications as part of an organization's retention policy. Journaling isn't recommended; retention policies and litigation hold, when necessary, should be used instead.

## Next steps

Now, you completed the Exchange Online design section and are ready to go to the Exchange Online setup section.

[Next: Set up Exchange Online>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-setup)
