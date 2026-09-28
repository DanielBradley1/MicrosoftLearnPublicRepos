<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Configure Transport Layer Security inspection policies

Transport Layer Security \(TLS\) inspection in Microsoft Entra Internet Access lets you decrypt and inspect encrypted traffic at service edge locations. This feature lets Global Secure Access apply advanced security controls like threat detection, content filtering, and granular access policies. These access policies help protect against threats that might be hidden in encrypted communications. This article explains how to create a context-aware Transport Layer Security inspection policy and assign it to users in your organization.

## Prerequisites

To complete the steps in this process, you must have the following prerequisites in place:

- An active, enabled certificate authority. Configure either a [Microsoft-managed certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings-managed-certificate) or [your own certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings).
- Test devices or virtual machines running Windows that are either Microsoft Entra joined or hybrid joined to your organization's Microsoft Entra ID.
- A trial license for Microsoft Entra Internet Access.
- [Global Secure Access prerequisites](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering)

## Create a context-aware TLS inspection policy

To create a context-aware Transport Layer Security inspection policy and assign it to users in your organization, complete the following steps:

### Step 1: Global Secure Access admin: create a TLS inspection policy

To create a TLS inspection policy:

1. In the Microsoft Entra admin center, go to **Secure** > **TLS inspection policies** > **Create policy**.  ![Screenshot of the Create a TLS inspection policy screen open to the Basics tab.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/create-tls-inspection-policy.png) The **Default action** specifies what to do if no rules match. The default setting is **Inspect**.
2. Select **Next** > **Add rule**. On the **Rules** page, you can define a custom rule by specifying an **FQDN** or selecting a **Web category**.  ![Screenshot of the Create a TLS inspection policy screen open to the Rules tab.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/add-rule.png)
3. To complete the policy configuration, go to **Save** > **Next** > **Submit**. Note a system rule has been auto created to exclude destinations that do not work with TLS inspection. An editable recommended bypass rule is automatically created to exclude Education, Finance, Government, and Health & Medicine categories.
4. To review rules, including the auto-created rules, select a policy and then go to **Edit** > **Rules**.  ![Screenshot of the Edit a TLS inspection policy screen open to the Rules tab.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/edit-policy-rules.png)

### Step 2: Global Secure Access admin: link the TLS inspection policy to a security profile

Link the TLS inspection policy to a security profile.

Before you enable TLS inspection on user traffic, make sure your organization has established and communicated TLS policy to end users. This step helps maintain transparency and supports compliance with privacy and consent requirements.

You can link the TLS policy to a security profile in two ways:

#### Option 1: Link the TLS policy to the baseline profile for all users

With this method, the baseline profile policy is evaluated last and applies to all user traffic.

1. In the Microsoft Entra admin center, navigate to **Secure** > **Security profiles**.
2. Switch to the **Baseline profile** tab.
3. Select **Edit profile**.
4. In the **Link policies** view, select **+ Link a policy** > **Existing TLS inspection policy**.
5. In the Link a TLS inspection policy view, choose a TLS policy and assign it a priority.
6. Select **Add**.  
   ![Screenshot of the Edit Baseline profile screen showing a list of policy names and their priorities.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/security-profile-baseline.png)

#### Option 2: Link the TLS policy to a security profile for specific users or groups

Alternatively, add a TLS policy to a security profile and link it to a [Conditional Access policy](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering#create-and-link-conditional-access-policy) for a specific user or group.  ![Screenshot of the new Conditional Access policy form with all fields completed with sample information.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/conditional-access-group-assignment.png)

### Step 4: Test the configuration

Ensure your devices trust the root certificate used to break and inspect TLS traffic. You can use Intune to [deploy the trusted certificate](https://learn.microsoft.com/en-us/intune/intune-service/protect/certificates-trusted-root#to-create-a-trusted-certificate-profile) to your managed Windows devices.

To test the configuration:

1. Make sure the end user device has the root certificate installed in the Trusted Root Certification Authorities folder.  ![Screenshot of the Trusted Root Certification Authorities folder.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/trusted-store.png)
2. Set up the Global Secure Access client:

   - Disable secure DNS and built-in DNS.
   - Block QUIC traffic from your device. QUIC isn't supported in Microsoft Entra Internet Access. Most websites support fallback to TCP when QUIC can't be established. For an improved user experience, deploy a Windows Firewall rule that blocks outbound UDP 443: `New-NetFirewallRule -DisplayName "Block QUIC" -Direction Outbound -Action Block -Protocol UDP -RemotePort 443`.
   - Make sure Internet Access Traffic Forwarding is enabled.

3. Open a browser on a client device and test various websites. Inspect the certificate information and confirm the Global Secure Access certificate.  ![Screenshot of the Certificate Viewer with the Global Secure Access certificate highlighted.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security/certificate-viewer.png)

## Disable TLS inspection

To disable TLS inspection:

1. Remove the policy link from the security profile:

   1. Browse to **Global Secure Access** > **Secure** > **Security profiles**.
   2. Switch to the **Baseline profile** tab.
   3. Select **Edit profile**.
   4. Select the **Link policies** view.
   5. Select the **Delete** icon for the policy you're disabling.
   6. Select **Delete** to confirm.

2. Remove the TLS inspection policy:

   1. Browse to **Global Secure Access** > **Secure** > **TLS inspection policies**.
   2. Select **Actions**.
   3. Select **Delete**.

3. Remove the TLS inspection policy certificate:

   1. Switch to the **TLS inspection settings** tab.
   2. Select **Actions**.
   3. Select **Delete**.

## Related content

- [Configure TLS inspection with a Microsoft-managed certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings-managed-certificate)
- [Configure TLS inspection with your own certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings)

- [Create a TLS certificates using ADCS](https://learn.microsoft.com/en-us/entra/global-secure-access/scripts/powershell-active-directory-certificate-service)
- [Create a TLS certificate using OpenSSL](https://learn.microsoft.com/en-us/entra/global-secure-access/scripts/powershell-open-secure-sockets-layer)
- [What is Transport Layer Security inspection?](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-transport-layer-security)
- [Frequently asked questions for Transport Layer Security inspection](https://learn.microsoft.com/en-us/entra/global-secure-access/faq-transport-layer-security)
- [Troubleshoot Transport Layer Security inspection issues](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-transport-layer-security)
