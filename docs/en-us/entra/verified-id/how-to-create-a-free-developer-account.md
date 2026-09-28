<!-- Source: https://learn.microsoft.com/en-us/entra/verified-id/how-to-create-a-free-developer-account -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# Microsoft Entra Verified ID developer information

## Overview

Note

The requirement of a Microsoft Entra ID P2 license was removed in early May 2021. The Microsoft Entra ID Free tier is now supported.

## Create a Microsoft Entra tenant for development

You can create a Microsoft Entra tenant for development and testing in either of the following ways:

- **Microsoft 365 Developer Program** — Join the [Microsoft 365 Developer Program](https://aka.ms/o365devprogram) to get a sandbox tenant with E5 licenses, configured users, groups, and mailboxes. A qualifying subscription or program membership is required — see [who qualifies](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-) for details.
- **Free Microsoft Entra tenant** — [Create a new tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant) with an [Azure free account](https://azure.microsoft.com/pricing/purchase-options/azure-account). This gives you Microsoft Entra ID Free tier. You can then [activate a free trial of Microsoft Entra ID P1 or P2](https://learn.microsoft.com/en-us/entra/fundamentals/get-started-premium) if needed for testing.

Important

The Microsoft 365 Developer Program requires a qualifying subscription or program membership. Eligible members include Visual Studio Enterprise or Professional subscribers, ISV Success Program or Microsoft AI Cloud Partner Program participants, and Premier or Unified Support customers. For more information, see the [Microsoft 365 Developer Program eligibility update](https://devblogs.microsoft.com/microsoft365dev/stay-ahead-of-the-game-with-the-latest-updates-to-the-microsoft-365-developer-program/) and [Who qualifies for a Microsoft 365 E5 developer subscription?](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). If you don't qualify, use the free tenant option instead.

### Sign up for the Microsoft 365 Developer Program

If you have a qualifying subscription or program membership and decide to sign up for the Microsoft 365 Developer Program, follow these steps:

1. On the [Microsoft 365 Developer Program](https://aka.ms/o365devprogram) page, select **Join now**.
2. Sign in with a new Microsoft account or use an existing \(work\) account.
3. On the sign-up page, select your region, enter a company name, and accept the terms and conditions of the program.
4. Select **Next**.
5. Select **Set up subscription**. Specify the region where you want to create your new tenant, create a username and domain, and enter a password. This step creates a new tenant and the first administrator of the tenant.
6. Enter the security information needed to protect the administrator account of your new tenant. This step sets up multifactor authentication for the account.

At this point, you've created a tenant with 25 E5 user licenses. The E5 licenses include Microsoft Entra ID P2 licenses. Optionally, you can add sample data packs with users, groups, mail, and SharePoint to help you test in your development environment. For the verifiable credential issuing service, these data packs aren't required.

## Next steps

Now that you have a developer account, try the [first tutorial](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant) to learn more about verifiable credentials.
