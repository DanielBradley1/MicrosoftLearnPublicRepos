<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-sharepoint-knowledge -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Configure SharePoint as a knowledge source for the Employee Self-Service declarative agent

Note

This article applies to the Employee Self-Service declarative agent. For the Employee Self-Service custom engine agent, see [Configure SharePoint as a knowledge source](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/customize#configure-sharepoint-as-a-knowledge-source).

To add SharePoint content as a knowledge source for the Employee Self-Service agent:

1. Open the **Employee Self-Service** agent in Copilot Studio and select the **Configure** tab.
2. Go to the **Knowledge** section. Under **Add files, meetings, chats, emails, and websites**, select the **SharePoint** icon.

   [![Screenshot of the Knowledge section on the Configure tab in Copilot Studio, showing the SharePoint, Teams, Outlook, and website icons.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-section.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-section.png#lightbox)
3. In the **Enter a name, URL, or email address** box, add the SharePoint sites or files that contain your HR or IT content. Use either of these methods:

   - **Search and select:** Type part of a site or file name to filter the results. Select the **Sites** tab to show only sites, or the **Files** tab to show only files. Then select an item from the list.

     [![Screenshot of the Knowledge section in Copilot Studio with a partial site name typed in the box, the Sites tab selected, and a matching SharePoint site in the results.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-search-sites.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-search-sites.png#lightbox)
   - **Paste a URL:** Paste the URL of a SharePoint site into the box, and then select the suggested site.

     [![Screenshot of the Knowledge section in Copilot Studio with a SharePoint site URL pasted in the box and the site listed under Suggested.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-paste-url.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-paste-url.png#lightbox)

4. Repeat the previous step for each site or file that you want to add.
5. The sites and files you add appear under **SharePoint** in the **Knowledge** section. You don't need to save.

   [![Screenshot of the Knowledge section in Copilot Studio with a SharePoint site, a file, and a page listed under SharePoint.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-added.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/da-sharepoint-knowledge-added.png#lightbox)
6. Republish the agent so that employees get responses grounded in the new sources.

Important

Add a SharePoint **site** rather than a single page when you want the agent to use all of the site's content. A common mistake is adding a page URL. You can add one, but the agent then uses only that page, not the rest of the site.

- Site URL \(uses all content in the site\): `https://contoso.sharepoint.com/sites/HR`
- Page URL \(uses only that page\): `https://contoso.sharepoint.com/sites/HR/SitePages/Benefits.aspx`

Tip

Add only the SharePoint sites and files that contain authoritative HR and IT content. Narrow, well-maintained sources produce more accurate answers. For guidance, see [Optimize SharePoint knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-optimize-sharepoint).

## SharePoint knowledge filtering

For information on SharePoint knowledge filtering, see [SharePoint advanced filtering](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-sharepoint-filtering).

## Related content

- [Configure knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-knowledge-sources)
- [Optimize SharePoint knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-optimize-sharepoint)
- [SharePoint advanced filtering](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-sharepoint-filtering)
