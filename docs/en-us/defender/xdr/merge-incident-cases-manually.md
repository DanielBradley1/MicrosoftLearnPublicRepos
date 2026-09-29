<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/merge-incident-cases-manually -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Merge incident cases manually in the Microsoft Defender portal \(preview\)

Incident cases are automatically created and correlated in the Microsoft Defender portal when suspicious activity is detected. Sometimes, related incident cases aren't merged automatically, or you might decide that multiple incident cases should be investigated as a single case.

Use manual merge to combine related incident cases. When incident cases are merged, one case ID is retained, case data is consolidated into the retained case, and the other case IDs are removed.

Note

Incident cases are in preview and are the recommended experience for managing incidents in the Microsoft Defender portal. The legacy incident experience remains available during this preview.

Note

Incident cases with a resolved status can't be merged.

## Prerequisites

Before you begin, make sure that:

- Your tenant is onboarded to the Microsoft Defender portal.
- You have access to incident cases in the Defender portal.
- You have the **Security Data Manage** Microsoft Defender unified RBAC permission.
- You have access to all incident cases you want to merge.

Incident case permissions and scoping follow the same permissions model as the legacy incident experience. You can merge only incident cases included in your assigned data sources and scopes.

For more information, see [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## Merge incident cases from the Cases page

To merge incident cases from the **Cases** page:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the incident cases you want to merge.
5. Select **Merge cases**.

   ![Screenshot showing multiple incident cases selected on the Cases page with the Manage case and Merge cases actions available in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/merge-incident-cases-manually/merge-incident-cases-manually-select-cases.png)
6. In the **Merge cases** pane, review the selected cases.
7. In **Comment**, enter a comment that explains why you're merging the cases.
8. Under **The reasons for this merge are**, select one or more reasons for the merge.

   Reasons can include:

   - Same threat source
   - Similar TTPs or behavior
   - Same actor
   - Same campaign
   - Shared indicators
   - Same asset
   - Network proximity
   - Event causal sequence
   - Temporal proximity
   - Lateral movement path

9. Select **Merge cases**.

## Merge an incident case from the case page

To merge incident cases from an open incident case:

To merge from the incident case page:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Open the incident case you want to merge.
5. Select the three-dot menu.
6. Select **Merge cases**.
7. In the **Merge cases** pane, search for the case you want to merge with.
8. Select the case.
9. In **Comment**, enter a comment that explains why you're merging the cases.
10. Under **The reasons for this merge are**, select one or more reasons for the merge.

    Reasons can include:

    - Same threat source
    - Similar TTPs or behavior
    - Same actor
    - Same campaign
    - Shared indicators
    - Same asset
    - Network proximity
    - Event causal sequence
    - Temporal proximity
    - Lateral movement path

11. Select **Merge cases**.

## Related content

- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Investigate incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases)
- [Merge and split incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-case-merging)
- [Move alerts from one incident case to another in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case)
