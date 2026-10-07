<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/add-google-domain?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-08-29 -->

# Add your Google Workspace domain to Microsoft 365

## Watch: Add Google Workspace domain

Watch this video and find more on the [Microsoft 365 small business YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198105).

<iframe src="https://learn-video.azurefd.net/vod/player?id=0ede3d98-5bb2-4f48-81d8-3d5634125446" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Add your Google Workspace domain to Microsoft 365 for business so you can keep using your business email address.

1. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the Microsoft 365 admin center, in the left nav, select **Show all** > **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
3. Choose **Add domain**, enter your domain name, and then select **Use this domain**.
4. Choose **Add a TXT record to the domain's DNS records**, select **Continue**, and copy the TXT value.
5. Identify the DNS hosting provider used by your domain's authoritative nameservers, and sign in to that provider.

   If your Google Domains registration migrated to Squarespace, use the [Squarespace Domains dashboard](https://domains.squarespace.com) to check the nameservers. With custom nameservers, add the record at that DNS provider, not in Squarespace's DNS records. See [Squarespace nameserver guidance](https://support.squarespace.com/hc/en-us/articles/4404183898125-Change-or-reset-your-domain-s-nameservers). Don't change nameservers or transfer the domain just to verify ownership.
6. At the authoritative DNS host, add the **TXT** record using the name and value supplied by Microsoft 365, and then save it. The update usually takes effect within a few minutes but might take up to 48 hours.
7. Return to the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), select **Verify**, and then **Close**. Adding the TXT record verifies domain ownership. It doesn't transfer domain registration or DNS hosting, and it doesn't redirect email to Microsoft 365.

## Update users' email addresses

Use the verified business domain when [preparing new email migration accounts](https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/migrate-email?view=o365-worldwide#prepare-mail-user-accounts).

For existing users who need a username and primary-email change:

1. In the left nav, select **Users** > [**Active users**](https://go.microsoft.com/fwlink/p/?linkid=834822).
2. Choose a user, select **Manage username and email**, **Edit**, select your domain from the dropdown, then select **Done** and **Save changes**.
3. Repeat for the other users who need the change.

Next, [prepare and migrate email](https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/migrate-email?view=o365-worldwide). Change the production MX records after completing the migration batches, as described in [Connect your domain](https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/connect-domain-tom365?view=o365-worldwide).
