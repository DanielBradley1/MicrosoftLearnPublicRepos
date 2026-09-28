<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/moveto-microsoft-365/connect-domain-tom365?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-03-16 -->

# Connect your domain to Microsoft 365 for business

Check out all of our small business content on [Small business help & learning](https://go.microsoft.com/fwlink/?linkid=2224585).

Check out [Microsoft 365 small business help](https://go.microsoft.com/fwlink/?linkid=2197659) on YouTube.

## Watch: Connect your domain to Microsoft 365

Check out this video and others on our [YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198216).

<iframe src="https://learn-video.azurefd.net/vod/player?id=b9007f8d-dd2b-4ceb-bf40-6529c45ad321" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Once you've set up Microsoft 365 and moved your email data from Google Workspace, you can connect your domain to Microsoft 365.

First you will need to delete existing DNS records from Google, and then we can add new DNS records from Microsoft 365.

1. Sign into your Google Workspace admin console at [admin.google.com](https://admin.google.com).
2. Select **Domains**, **Manage domains**, **View details**, **Manage domain**, then **DNS** in the left nav.
3. Scroll down to **Synthetic records**, open **Google Workspace**, select **Delete**, then **Delete** again.
4. Scroll down to **Custom resource records** and delete any existing DNS records that appear, including any you may have created previously for Microsoft 365.
5. Go to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
6. In the left nav, choose, **Show all** > **Settings** > [**Domains**](https://go.microsoft.com/fwlink/p/?linkid=834818).
7. Then choose your default domain.
8. Select **Continue setup**, then, to connect your domain, choose **Continue**.
9. Scroll down to view the DNS records that need to be copied to Google.
10. Open **MX Records**, and under **Points to address or value**, copy the record.
11. Return to Google, and in the **Custom resource records** section, open the record type dropdown and select **MX**.
12. In the **Data** field, paste the record you copied.
13. Then select **Add**.
14. Repeat the process for CNAME and TXT records and add the values in the Google DNS management page.
15. Return to the Microsoft 365 admin center and select **Continue**.

    Your domain setup is complete.
