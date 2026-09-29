<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/prioritize-vulnerabilities -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Prioritize and remediate vulnerabilities in Microsoft Defender for IoT

With vulnerability management, Microsoft Defender for IoT in the Defender portal provides extended coverage for operational technology \(OT\) networks, gathers OT device data into one place, and displays the data with the other devices on your network.

In this article, you learn how to investigate vulnerabilities and take recommended remediation actions. Learn more about how Defender for IoT discovers vulnerabilities in the [vulnerability discovery overview](https://learn.microsoft.com/en-us/defender-for-iot/discover-vulnerabilities-overview).

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Investigate vulnerabilities

To investigate vulnerabilities and review recommended remediation actions, follow these steps:

1. In the Defender portal, select **Endpoints > Vulnerability management > Weaknesses**.
2. Set the filter settings as needed. If device groups are created for your sites, you can use them filter the weaknesses page.

   1. Select **Filter by device groups**.
   2. Select a device group.
   3. Select **Apply**.

3. Select a Common Vulnerabilities and Exposures \(CVE\) ID.

   A side panel opens with the CVE ID as the title, and the **Vulnerability details** tab visible. You can also select the **Exposed devices** and **Affected software** tabs.
4. Select **Go to related security recommendation**.

   The **Security recommendations** page opens, filtered to show the CVE you're investigating.
5. Select a recommendation. A side panel opens. Do one of the following:

   - Select **Request remediation** and follow the [Request remediation instructions](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-remediation#request-remediation). This sends a request to the relevant team to perform the remediation.
   - Select **Exception options** and fill in the details. For more information, see [justification for an exception](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation#explore-security-recommendation-options). To complete, select **Submit**.

## Next steps

- [Investigate and remediate incidents and alerts](https://learn.microsoft.com/en-us/defender-for-iot/investigate-threats)
