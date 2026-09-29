<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-security-copilot-query-assistant -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Microsoft Security Copilot advanced hunting query assistant

[Microsoft Security Copilot in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-in-microsoft-365-defender) includes a query assistant feature for advanced hunting.

Threat hunters or security analysts who aren't familiar with or haven't learned Kusto query language \(KQL\) can make a request or ask a question in natural language \(for example, *Get all alerts involving user admin123*\). Security Copilot then generates a KQL query that matches the request by using the advanced hunting data schema.

The query assistant feature reduces the time it takes to write a hunting query from scratch, so threat hunters and security analysts can focus on hunting and investigating threats.

Users with access to Security Copilot can use the query assistant feature in advanced hunting.

Note

The advanced hunting capability is also available in the Security Copilot standalone experience through the Microsoft Defender XDR plugin. Know more about [preinstalled plugins in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/manage-plugins#preinstalled-plugins).

## Try your first request

To start using the Query assistant, follow these steps:

Note

Make sure that the Query assistant mode is active. [Get access to Security Copilot in advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-security-copilot#get-access)

1. Open the **Advanced hunting** page from the navigation bar in Microsoft Defender portal. The Security Copilot side pane for advanced hunting appears at the right hand side.

   [![Screenshot of the Copilot pane in advanced hunting.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-pane-big.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-pane-big.png#lightbox)

   You can also reopen Copilot by selecting **Copilot** at the top of the query editor.
2. In the Copilot prompt bar, ask any threat hunting query that you want to run and press ![](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/send.png) or **Enter**.

   [![Screenshot that shows prompt bar in the Security Copilot for advanced hunting.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-query-big.png)](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-query-big.png#lightbox)
3. Copilot generates a KQL query from your text instruction or question. While Copilot is generating, you can cancel the query generation by selecting **Stop generating**.

   ![Screenshot of Security Copilot in advanced hunting showing generated query results with Add and run and Add to editor options.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-generate.png)

4. Review the generated query. To check how Copilot came up with the query, you can select **See the logic behind the query** below the query text to expand the explanation behind the query. Select **See the logic behind the query** again to minimize the explanation.

   ![Screenshot of Security Copilot option to see the logic behind the query.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-see-logic.png)


   You can then choose to run the query by selecting **Run query**.


   ![Screenshot of Security Copilot showing the Run query option.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-run-query.png)


   The generated query appears as the last query in the query editor and runs automatically.


   If you need to make further tweaks, select **Add to editor**.


   ![Screenshot of Security Copilot in advanced hunting showing the Add to editor option.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-add-editor.png)


   The generated query appears in the query editor as the last query, where you can edit it before running using the regular **Run query** above the query editor.

5. You can provide feedback about the generated response by selecting the feedback icon ![Screenshot of Security Copilot feedback option in advanced hunting.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-feedback-icon.png) and choosing **Looks right**, **Needs improvement**, or **Inappropriate**.

Tip

Providing feedback is an important way to let the Security Copilot team know how well the query assistant was able to help in generating a useful KQL query. Feel free to articulate what could make the query better, what adjustments you had to make before running the generated KQL query, or share the KQL query that you eventually used.

## Run or add the generated query

When the Threat Hunting Assistant generates a KQL query, select **Run query** to run it in advanced hunting.

To review or edit the query before running it, select the arrow next to **Run query**, then select **Add to editor**. The query is added to the query editor without running.

![Screenshot of the Run query split button in the Security Copilot side pane, showing the Add to editor option.](https://learn.microsoft.com/en-us/defender-xdr/media/advanced-hunting-security-copilot/advanced-hunting-security-copilot-settings.png)

To see how the query was constructed, select **See the logic behind the query**.
