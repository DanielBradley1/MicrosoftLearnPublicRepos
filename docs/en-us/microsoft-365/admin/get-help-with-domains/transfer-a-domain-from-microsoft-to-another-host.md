<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Transfer a domain from Microsoft to another host

You can't transfer a Microsoft 365 domain to another registrar for 60 days after you purchase the domain from Microsoft.

Note

A *Whois* query shows a Microsoft purchased domain registrar as **Wild West Domains LLC**. However, only Microsoft should be contacted about your Microsoft 365 purchased domain.

Sign in with an account with appropriate permissions, follow these steps to get a code at Microsoft 365, and then go to the other domain registrar website to transfer your domain name to the new registrar.

Important

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. For more information, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Transfer a domain

1. In the admin center, go to **Settings** > **Domains**.
2. On the **Domains** page, select the Microsoft 365 domain that you want to transfer to another domain registrar, and then select **Check health**.
3. At the top of the page, select **Transfer domain**.
4. On the **Choose where to transfer your domain** page, select **A different registrar**, and then select **Next**.
5. On the **Unlock domain transfer** page, select **Unlock transfer for *<your domain>***, and then select **Next**.
6. Check your domain transfer contact information, and then select **Next**.
7. Copy the authorization code and wait about 30 minutes for your domain transfer status to change to **Unlocked for transfer** on the **Registration** tab before you continue with next steps.
8. Go to the website of the domain registrar you want to manage your domain name going forward. Follow directions for transferring a domain. If you need assistance, search for help on their website. Transferring a domain usually means paying transfer fees and giving the Authcode to the new registrar so they can start the transfer. Microsoft emails you to confirm the transfer request is received. The domain then transfers within five days.

   You can find the authorization code on the **Registration** tab on the **Domains** page in Microsoft 365.

   Tip

   `.uk` domains require a different procedure. Select an IPS tag from the drop-down menu of UK domain registrars to update your **IPS Tags** to match the registrar you want to manage your domain going forward. Once the tag changes, the domain immediately transfers to the new registrar. To complete the transfer, work with the new registrar. This process most likely involves paying transfer fees and adding the transferred domain to your account with your new registrar.
9. After the transfer is complete, you'll renew your domain at the new domain registrar.
10. To finish the process, go back to the **Domains** page in the admin center, and then select **Complete domain transfer**. This action marks the domain not purchased from Microsoft 365 and disables the domain subscription. It doesn't remove the domain from the tenant and doesn't affect existing users and mailboxes on the domain.

Note

Microsoft 365 purchased domains aren't eligible for nameserver changes or transferring the domain between Microsoft 365 organizations. If either of these procedures are required, the domain registration must be transferred to another registrar.

## Support

Tip

Some configuration tasks might be complex to perform. For technical support, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. At the bottom right, select **Help & Support**.
3. In the **Support Assistant** pane that opens, enter your question.
4. Review the results. If you still have questions, select **Contact support**.

To learn about your options for contacting support, see [Get support for Microsoft 365 for business](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-support).
