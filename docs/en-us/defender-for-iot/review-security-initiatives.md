<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/review-security-initiatives -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Review security initiatives in Microsoft Defender for IoT

[Security initiatives](https://learn.microsoft.com/en-us/security-exposure-management/exposure-insights-overview#security-initiatives) offer a focused, metric-driven way of tracking exposure in specific security areas using security initiatives.

Microsoft Defender for IoT in the Defender portal allows you to review Microsoft Security Exposure Management security initiatives dedicated to OT and enterprise IoT device protection.

In this article, you learn how to review security initiatives so that your security teams can prioritize, discover, and validate OT-related security findings across your sites.

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Review the OT Security initiative

The **OT Security** initiative improves your OT site security posture by monitoring and protecting OT environments in the organization, and employing network layer monitoring. The **OT Security** initiative identifies devices and ensures that systems are working correctly, and data is protected.

Your security teams can use the **OT Security** initiative to:

- Identify unprotected devices.
- Harden posture across sites through vulnerability assessments, with actionable guidance to help remediate at-risk devices.

## Review the Enterprise IoT Security initiative

The **Enterprise IoT Security** initiative allows you to identify unmanaged IoT devices and enhance your organization's security. With continuous monitoring, vulnerability assessments, and tailored recommendations specifically designed for enterprise IoT devices, you gain comprehensive visibility into the risks posed by these devices. The **Enterprise IoT Security** initiative not only helps you understand the potential threats but also strengthens your organization's resilience in mitigating them.

Review the full [security initiatives catalog](https://learn.microsoft.com/en-us/security-exposure-management/initiatives-list).

## Prerequisites

Before you review security initiatives, make sure you meet the following prerequisites:

- Review the Defender for IoT [prerequisites](https://learn.microsoft.com/en-us/defender-for-iot/prerequisites).
- Review the [prerequisites for the **OT Security** initiative](#prerequisites-for-ot-security-initiative).

### Prerequisites for OT Security initiative

When you view the **OT Security** initiative, if you haven't yet onboarded Defender for IoT and set up sites, the **More data is required to support the OT Security initiative** section is displayed.

![Screenshot showing the \*\*More data is required to support this initiative\*\* section in Microsoft Defender for IoT in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-iot/media/review-security-initiatives/more-data-required.png)

If the **More data is required to support this initiative** section is displayed:

1. Review the **Unprotected OT devices** metric to understand the impact on your network. For example, the **Unprotected OT devices** metric shows 24 affected assets.

   ![Screenshot showing the Unprotected OT devices metric \*\*Overview\*\* tab in Microsoft Defender for IoT in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-iot/media/review-security-initiatives/unprotected-ot-devices.png)
2. Select **Get started with Microsoft Defender for IoT** and follow the procedure to [onboard Defender for IoT in the Defender portal](https://learn.microsoft.com/en-us/defender-for-iot/get-started).
3. Select **create new sites** to [set up sites](https://learn.microsoft.com/en-us/defender-for-iot/set-up-sites).

## Review OT and Enterprise IoT security initiatives in the Defender portal

1. Follow the procedure to [open the Initiatives page and review an initiative](https://learn.microsoft.com/en-us/security-exposure-management/initiatives#view-initiatives-page).
2. For the **OT Security** initiative, if you haven't yet onboarded Defender for IoT and set up sites, the **More data is required to support the OT Security initiative** section is displayed. If this section is displayed, see the [prerequisites for the OT Security initiative](#prerequisites-for-ot-security-initiative).
3. Review the data in the initiative page, including the initiative score, top metrics, and more \(learn more about [security exposure management initiatives](https://learn.microsoft.com/en-us/security-exposure-management/exposure-insights-overview)\). For example, this **OT Security** initiative page shows an initiative score of 83%, and shows that 61.9% of the detected OT devices are protected.

   [![Screenshot showing the OT Security initiative in Microsoft Defender for IoT in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-iot/media/review-security-initiatives/ot-security-initiative.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/review-security-initiatives/ot-security-initiative.png#lightbox)
4. Select the metric from the **Top metrics** area in the initiative page or from the **Related metrics** area in the small overview.

   - Review the **Overview** tab to drill down into additional security data and recommendations, including the weight of the metrics, affected assets, and score impact. For example, the **Unprotected OT devices** metric shows 24 affected assets, and 3.81 score impact.
   - Review the recommendations in the **Security recommendations** tab. For example, for the **Site-linked devices using insecure protocols** metric, you're recommended to disable the Telnet administration protocol, and remove the SNMP V1 and SNMP V2 administration protocols.

     ![Screenshot showing the \*\*Security recommendations\*\* tab for a metric in Microsoft Defender for IoT in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-for-iot/media/review-security-initiatives/security-recommendations.png)


   Learn more about [working with metrics](https://learn.microsoft.com/en-us/security-exposure-management/exposure-insights-overview#working-with-metrics).

## Next steps

[Learn about vulnerabilities](https://learn.microsoft.com/en-us/defender-for-iot/discover-vulnerabilities-overview) or proceed to [investigate and remediate vulnerabilities](https://learn.microsoft.com/en-us/defender-for-iot/prioritize-vulnerabilities).
