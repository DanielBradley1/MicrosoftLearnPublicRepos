<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-domains -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Step 1: Create your Office 365 tenant account

Tip

Some of the URLs in this article will take you to another document set. If you would like to maintain your place in this document set's table of contents, right-click the URLs to open them in a new window.

## Create your tenant

Follow these steps to set up an Office 365 Education verified tenant if you don't already have one.

1. [Verify academic eligibility for Microsoft Education subscriptions.](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/verify-academic-eligibility)
2. Navigate to the [Office 365 Education Plans page.](https://products.office.com/academic/compare-office-365-education-plans)
3. Select the blue **Get Started** button.

   ![Screenshot showing get started page for education tenant.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/get-started-edu-sign-up.png)
4. Add your verified e-mail and sign up.

   ![Screenshot showing sign-up page for education tenant.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/get-started-school-email.png)
5. Select **Sign up**.

Note

For education scenarios:

- Setup of your organization tenant is needed to start your tenant successfully.

## Add domains

After you created your tenant, add each of the domains for your organization using [these instructions for each domain you want to add.](https://support.office.com/article/Add-a-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611) You don't need to create a tenant account for each domain. You can have a single tenant account with multiple domains.

Note

For education scenarios:

- You cannot use the same root domain in another tenant
- Child/sub domains can be added
- Exchange MX records can point outside to other services

**Recommendation** – If possible, add a small number of domains. For education, enabling a single domain for teachers and a single domain for students works well. Each domain added is intended to be associated to the UserPrincipalName and Email Address of the users in your directory. If you have domains from an on-premises Active Directory that aren't being used, you don't need to add them to your Office 365 tenant.

[![Screenshot showing Domains for organization.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/setup-domains.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/setup-domains-lg.png#lightbox)

## Next steps

Next, let's configure the admin settings in the Security Center.

[Next: Configure the admin settings](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-admin-settings)
