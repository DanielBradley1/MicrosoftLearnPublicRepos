<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/set-up-saml-sso-figma-microsoft-entra-id -->
<!-- Sitemap-Last-Modified: 2026-02-10 -->

# Set up SAML SSO for Figma with Microsoft Entra ID

Note

You can only complete this step after your Figma for Education rep has enabled you as your organization's administrator.

Organizations that manage users with Microsoft Entra ID can configure SAML SSO in Figma. Figma supports both identity \(Microsoft Entra ID\) and service \(Figma\) initiated configurations.

We recommend having both Figma and Microsoft Entra ID open in separate tabs so that you can switch between them throughout the setup process.

Note

When configuring SAML in an active organization:

- Microsoft recommends testing SAML configurations in a sandbox environment. However, there isn't a way to create a sandbox or test environment in Figma. We recommend testing the Figma application with a test user, such as yourself, or a small group of users first.
- To make sure existing users can still access Figma during the set up process, [set the login and authentication method](https://help.figma.com/hc/en-us/articles/360052497994) to **Members may log in with any method, including email and password** \(default\).
- After everything is up and running, you can update this setting to Members must log in with SAML SSO. Learn more in Microsoft's tutorial: [Microsoft Entra ID SSO Integration with Figma](https://learn.microsoft.com/en-us/entra/identity/saas-apps/figma-tutorial).

## Confirm your Figma administrator account

1. Visit [figma.com](https://www.figma.com/).
2. Select **Log In**.
3. Sign in with your account \(previously created\) using your administrator district email address.
4. Confirm you are on your organization's account by checking the left toolbar for:

   - The name of your school or district
   - An admin settings tab

5. If you don't see the name of your organization and an admin settings tab, you might be viewing external teams.

   - Select the dropdown next to **External teams.**
   - Select the name of your district or school in the dropdown.

[![Picture showing location of external teams drop-down menu.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/account-set-to-external-teams.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/account-set-to-external-teams.png#lightbox)

[![Picture showing location org name and admin settings.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/account-set-to-organization.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/account-set-to-organization.png#lightbox)

## Set up SAML SSO

Next, use [these Figma instructions](https://help.figma.com/hc/en-us/articles/360040532413-SAML-SSO-with-Microsoft-Entra-ID) to set up SAML SSO in Figma. Remember to return to this page after you finish!

## User view at login

Depending on how you configured your setup, students and educators are shown one of two ways to log in to Figma.

### SP-initiated login

Students login using single sign-on.

1. Visit figma.com
2. Select **Log In**.
3. Select **Use** **single-sign on**.
4. Enter school email address \(no password necessary\).
5. Select **Log** **in**.

   [![Picture showing the dialog box to sign in to Figma.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sign-in-figma.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sign-in-figma.png#lightbox)

### IdP\(Identity Provider\) Initiated login

Students log in from Microsoft 365 and are redirected to Figma.

[![Picture showing how to log in to Figma using IdP.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sign-in-idp.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/sign-in-idp.png#lightbox)

[Next: Configure your Figma organization>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/configure-figma-organization)
