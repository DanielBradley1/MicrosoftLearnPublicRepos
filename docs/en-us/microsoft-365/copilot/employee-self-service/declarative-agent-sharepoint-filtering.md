<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-sharepoint-filtering -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Use SharePoint advanced filtering with the Employee Self-Service declarative agent

Note

This article applies to the Employee Self-Service declarative agent. For the Employee Self-Service custom engine agent, see [SharePoint advanced filtering](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/sharepoint-filtering).

When employees ask questions like "What is my holiday policy?", the Employee Self-Service agent sometimes shows policies for multiple countries/regions \(for example, US, India, France\) instead of just the one that applies to the employee. This situation happens because Employee Self-Service retrieves all matching SharePoint documents but doesn't apply user-specific filters \(like country/region or company code\) during the search.

We can personalize results by telling the Employee Self-Service agent to only return SharePoint documents that match the employee's profile, such as their location or company code.

This personalization works in two parts:

1. The Employee Self-Service agent collects user information, like location, and stores it as a variable.
2. SharePoint knowledge sources are updated to use that variable when searching, so results are filtered to what's relevant.

## Step-by-step configuration

### Prerequisites

1. Decide the attributes to filter on \(some examples include Company\_Code, Country/Region, Location, Department\).
2. Verify SharePoint metadata exists on the target content \(site columns filled on pages/docs\).
3. Find the managed property that maps to that column: **SharePoint Admin Center** > **More features** > **Search** > Manage Search Schema.

   1. Confirm the property you want to use \(such as RefinableString100\) is Searchable/Queryable/Refinable.
   2. If you just changed mappings, Reindex the library or site and allow time for crawl.

4. Identify where you intend to source your user attribute at runtime, like Workday, SuccessFactors, Graph, or a custom API.

### Capture the user context in the agent \(Copilot Studio\)

1. In your Employee Self-Service agent solution, open **Admin** > **User Context** > **Setup**.
2. Make sure this topic runs before any retrieval topics \(keep/enable the redirect pattern\).
3. Fetch attributes and set global variables, such as:

   1. Global.ESS\_UserContext\_Company\_Code
   2. Global.ESS\_UserContext\_Country
   3. Global.ESS\_UserContext\_Location

      Note

      Use your connector/action to get these values. For a quick smoke test, you can temporarily hardcode a value.

4. Save and publish.

### Add KQL filters to SharePoint knowledge sources

For **each** SharePoint knowledge source that must respect filtering:

1. Open the **Knowledge source** > **Advanced settings**.
2. In **Additional search** terms, add KQL that references your **managed property** and **global variable**.

   **Examples**

   - **Company code**


   ```text
   additionalSearchTerms: (NOT HIDEFROMSEARCH:1)
   AND (RefinableString100:All OR RefinableString100:{Global.ESS_UserContext_Company_Code})
   ```


   - **Country/Region**


   ```text
   additionalSearchTerms: (NOT HIDEFROMSEARCH:1)
   AND (RefinableString101:{Global.ESS_UserContext_Country})
   ```


   - **Location**


   ```text
   additionalSearchTerms: (NOT HIDEFROMSEARCH:1)  
   AND (RefinableString102:{Global.ESS_UserContext_Location})
   ```


   - **Multiple attributes \(AND\)**


   ```text
   additionalSearchTerms: (NOT HIDEFROMSEARCH:1)
   AND (RefinableString100:{Global.ESS_UserContext_Company_Code})
   AND (RefinableString101:{Global.ESS_UserContext_Country})
   ```


   Tip


   All is a useful fallback value when content is intentionally global or applicable to everyone.

3. Save and publish.
