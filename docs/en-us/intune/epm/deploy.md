<!-- Source: https://learn.microsoft.com/en-us/intune/epm/deploy -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Deploy Endpoint Privilege Management with Microsoft Intune

To deploy Endpoint Privilege Management \(EPM\), start by enabling reporting, then use reports to create rules for elevation. This article describes some common deployment scenarios and outlines the recommended deployment phases for your organization.

- [Windows elevation settings policy](https://learn.microsoft.com/en-us/intune/epm/manage-elevation-settings).
- [Windows elevation rules policy](https://learn.microsoft.com/en-us/intune/epm/create-elevation-rules).
- [Reusable settings groups](https://learn.microsoft.com/en-us/intune/epm/create-elevation-rules#reusable-settings-groups), which are optional configurations for your elevation rules.

## Deployment overview

EPM can help control the elevation of applications in Intune and [Local Users and Groups](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection) can be used to control the local administrators group and transition users from administrators to standard users.

The common deployment phases are:

![The five phases to deploy EPM.](https://learn.microsoft.com/en-us/intune/epm/media/deploy/epm-deploy-phases.png)

- **Phase 1: Auditing** - Enable EPM client and enable reporting collection using an [elevation settings policy](https://learn.microsoft.com/en-us/intune/epm/manage-elevation-settings).
- **Phase 2: Persona identification** - Identity groups of users with common requirements.
- **Phase 3: Build rules** - Use [EPM reports](https://learn.microsoft.com/en-us/intune/epm/monitor-reports) to create [elevation rules](https://learn.microsoft.com/en-us/intune/epm/create-elevation-rules) for different personas.
- **Phase 4: Monitoring** - Iterate and refine rules, identify new scenarios.
- **Phase 5: Review user privileges** - Identify and optionally move users from administrator to standard user using [Local Users and Groups](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection#manage-local-groups-on-windows-devices). Consider enabling [support approved elevation](https://learn.microsoft.com/en-us/intune/epm/manage-support-approvals) so that users can request elevation for apps that aren't covered by rules.

Repeat phases 2 to 5 continuously to ensure your users have least privilege in line with [Zero Trust principles](https://learn.microsoft.com/en-us/intune/fundamentals/zero-trust).

The common deployment scenarios for EPM are:

| Scenario | Local User \(Before\) | Local User \(After\) | Example Role | Use Case |
| --- | --- | --- | --- | --- |
| 1 | Admin | Admin | IT Support Technicians | A certain subset of users required ongoing local admin – but you want to gain security improvements by using EPM. |
| 2 | Admin | Standard User | Information Workers | You want to move users with local admin rights to standard users, with minimal disruption. You want to allow them to request an app to run as admin on occasion.  <br>  <br>For step by step instructions on how to achieve this scenario with EPM, see [Using EPM to transition users from administrator to standard users](https://learn.microsoft.com/en-us/intune/epm/tutorial-admin-to-standard-user) |
| 2 | Standard User | Standard User | Developers | You want to allow specific users to 'elevate up' without granting local admin rights or using [LAPS](https://learn.microsoft.com/en-us/intune/device-security/laps/overview). |

---

## Next steps

[Next: Create an elevation settings policy >](https://learn.microsoft.com/en-us/intune/epm/manage-elevation-settings)
