<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Move alerts from one incident case to another in the Microsoft Defender portal \(preview\)

Incident cases use alert correlation to group related alerts into a single incident case. If an alert is correlated to the wrong incident case, you can move the alert to another incident case so that analysts investigate and respond with the correct context.

When you move an alert, you must add a comment that explains the change. You can also submit feedback to Microsoft about the incorrect correlation type or irrelevant entities to help improve alert correlation.

Note

Incident cases are in preview and are the recommended experience for managing incidents in the Microsoft Defender portal. The legacy incident experience remains available during this preview.

## Prerequisites

Before you begin, make sure that:

- Your tenant is onboarded to the Microsoft Defender portal.
- You have access to incident cases in the Defender portal.
- You have the **Security Data Manage** Microsoft Defender unified RBAC permission.
- You have access to the alert you want to move and both the current and destination incident cases.

Incident case permissions and scoping follow the same permissions model as the legacy incident experience. You can move alerts only between incident cases included in your assigned data sources and scopes.

For more information, see [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## Move an alert to another incident case

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Open the incident case that contains the alert you want to move.
5. Under **Artifacts**, select **Alerts**.
6. Select the alert you want to move.
7. Select **Move alert to another incident**.

   ![Screenshot showing a selected alert and the Move alerts to another incident action in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/move-alert-to-another-incident-case/move-alert-to-another-incident-case-select-alert.png)
8. Search for and select the incident case that you want to move the alert to.

   ![Screenshot showing the Move alert to another incident pane in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/move-alert-to-another-incident-case/move-alert-to-another-incident-case-pane.png)
9. In **Comment**, enter a comment that explains why you're moving the alert.
10. Under **Submit feedback to Microsoft for this correlation change**, provide feedback about the correlation change.

    You can select:

    - The correlation types that are incorrect.
    - The entities that are irrelevant to the current correlation.

11. Select **Save**.

The alert is moved to the selected incident case. The alert is removed from the original incident case and becomes part of the destination incident case investigation context.

## Related content

- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Investigate incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases)
- [Alert correlation and incident merging in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/alerts-incidents-correlation)
- [Merge incident cases manually in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/merge-incident-cases-manually)
