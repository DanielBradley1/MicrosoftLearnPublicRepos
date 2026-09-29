<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-permissions -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# How Microsoft Defender Experts permissions work

**Applies to:**

- [Microsoft Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview)
- [Microsoft Defender Experts for Servers](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-servers-overview)

For Microsoft Defender Experts incident investigations, when our experts need access to your tenants, we follow the just-in-time and least privilege principles to provide the right level of access at the right time. To deliver on these requirements, we built the Microsoft Defender Experts permissions platform using the following capabilities in Microsoft Entra ID:

- **Granular delegated admin privileges \(GDAP\)**: As part of onboarding, we provision the Microsoft Experts tenant as a service provider on your tenant to use the GDAP capability and get the right access level to our experts. The roles granted to our experts are configured using [cross-tenant role assignment](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/cross-tenant-access-overview) to ensure that they only have permissions that you have explicitly granted to them.
- **Microsoft Entra cross-tenant access policies**: To enforce restrictions on our experts' access to your tenant, we need to establish a cross-tenant trust between our experts and your tenant. To enable this trust, we configure a cross-tenant access policy in your tenant as part of onboarding. These cross-tenant access policies are created with read-only permissions to avoid any disruption.
- **Conditional access for external users**: We restrict our experts' access to your tenants from our secure environment by using compliant devices with strong multifactor authentication \(MFA\). To enforce the trust settings configured in cross-tenant access policy and block access otherwise, we configure these conditional access policies in your tenant.
- **Just-in-time \(JIT\) access**: Even after you have permitted our experts access to your environment, we limit their access based on JIT permissions for case investigation, with limited duration for each role. Our experts must first request access and get approval in our internal system to gain the appropriate role in your tenant. Our experts' access to your tenant is audited as part of Microsoft Entra sign-in logs for you to review

## Configuring permissions in customer tenants

Once you select the permissions you'd like to grant to our experts, we create the following policies in your tenant using the Security Administrator or higher role:

- **Configure Microsoft Experts as a service provider** – This setting lets our experts access the tenant environment as external collaborators without requiring you to create accounts for them.
- **Configure role assignments for our experts** – This setting controls the roles our experts are allowed in the tenant. You select the appropriate roles during the onboarding process
- **Configure cross-tenant access settings with MFA and compliant device as the trust settings** – This setting configures a trust relationship between customer and Microsoft Experts tenants based on MFA and device compliance in the Microsoft Experts tenant. This policy can be found under **Microsoft Entra ID** > **External Identities** > **Cross-tenant access Settings** with the name *Microsoft Experts*.
- **Configure conditional access policies** – These policies restrict our experts to only access your tenant from the Microsoft Experts secure workstations with MFA verification. Two policies are configured with the naming convention *Microsoft Security Experts-<policy name>-DO NOT DELETE*.

These policies are configured during the onboarding process and require the relevant administrator to stay signed in to complete the steps. Once the above policies are created and the permissions setup is considered complete, you'll see a notification that the setup is complete.

### See also

[Important considerations for Microsoft Defender Experts](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-considerations)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
