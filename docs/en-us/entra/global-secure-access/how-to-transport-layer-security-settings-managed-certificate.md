<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings-managed-certificate -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Configure TLS inspection with a Microsoft-managed certificate \(preview\)

Transport Layer Security \(TLS\) inspection in Microsoft Entra Internet Access requires a certificate authority \(CA\) that client devices trust. With a Microsoft-managed certificate, Microsoft generates and operates a tenant-specific root CA for your organization. You don't need to provide your own public key infrastructure \(PKI\) or CA for TLS inspection.

Note

Microsoft-managed certificates for TLS inspection are currently in preview. This information relates to a prerelease product that might be substantially modified before release. Microsoft makes no warranties, expressed or implied, with respect to the information provided here. For more information, see the [Microsoft Entra preview terms](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

This article explains how to create a Microsoft-managed certificate, deploy the root CA certificate to client devices, and enable the certificate for TLS inspection. The private key is protected in Microsoft's secure key infrastructure and isn't exposed.

If your organization must use its own PKI, see [Configure TLS inspection with your own certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings).

## Prerequisites

To complete the steps in this article, you need:

- A trial license for Microsoft Entra Internet Access.
- [Global Secure Access prerequisites](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering).
- The [Global Secure Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-secure-access-administrator) role.

## Create a Microsoft-managed certificate

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as a Global Secure Access Administrator.
2. Browse to **Global Secure Access** > **Secure** > **TLS inspection policies**.
3. Select the **TLS inspection settings** tab.
4. Select **Create certificate**, and then select **Microsoft-managed**.

   [![Screenshot that shows the Microsoft-managed option on the Create certificate menu.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/create-microsoft-managed-certificate-menu.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/create-microsoft-managed-certificate-menu.png#lightbox)
5. In the **Create Microsoft-managed certificate** pane, review the certificate details and lifecycle. Microsoft automatically configures the tenant-specific certificate authority. No certificate information is required.

   [![Screenshot that shows the details and lifecycle of a Microsoft-managed certificate.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/create-microsoft-managed-certificate-pane.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/create-microsoft-managed-certificate-pane.png#lightbox)

   Note

   The default root CA validity period is 10 years. You can use the API to configure a shorter validity period if your organization requires one.
6. Select **Create**.
7. Confirm that the certificate appears in the list with **Managed** in the **Type** column and **Disabled** in the **Status** column.

## Download and deploy the root CA certificate

Client devices must trust the managed root CA before you enable TLS inspection. If you apply a TLS inspection policy before distributing the root CA certificate, users can encounter certificate errors.

1. On the **TLS inspection settings** tab, find the managed certificate.
2. Select the actions menu \(**...**\), and then select **Download root certificate**.

   [![Screenshot that shows the Download root certificate action for a Microsoft-managed certificate.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/download-root-certificate.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/how-to-transport-layer-security-settings-managed-certificate/download-root-certificate.png#lightbox)
3. Save the `.cer` file.
4. Use your MDM solution to deploy the root CA certificate to client devices. For Microsoft Intune, see [Trusted root certificate profiles for Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/certificates-trusted-root).
5. On a test device, confirm that the certificate is installed in the **Trusted Root Certification Authorities** store.

The downloaded file contains the public root CA certificate. It doesn't contain the private key.

## Enable the managed certificate

After you deploy the root CA certificate to your client devices:

1. On the **TLS inspection settings** tab, find the managed certificate.
2. Select the actions menu \(**...**\), and then select **Enable**.
3. Confirm that the certificate status changes to **Active**.

You can now [create and assign a TLS inspection policy](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security).

## Manage the certificate

Use the actions menu \(**...**\) on the **TLS inspection settings** tab to manage a Microsoft-managed certificate:

- **Disable**: Temporarily stop using the certificate for TLS inspection.
- **Enable**: Enable a disabled certificate.
- **Delete**: Remove a certificate that you no longer need.

### Rotate a Microsoft-managed certificate

Rotate a certificate before it expires:

1. Create a new Microsoft-managed certificate.
2. Download the new root CA certificate.
3. Deploy the new root CA certificate to client devices.
4. Enable the new certificate.
5. Validate TLS inspection with the new certificate.
6. After validation succeeds, delete the old disabled certificate.

Don't remove the old root CA certificate from client devices until you validate the new certificate and complete the transition.

## Related content

- [Configure TLS inspection with your own certificate](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security-settings)
- [Configure Transport Layer Security inspection policies](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security)
- [What is Transport Layer Security inspection?](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-transport-layer-security)
- [Transport Layer Security inspection frequently asked questions](https://learn.microsoft.com/en-us/entra/global-secure-access/faq-transport-layer-security)
- [Troubleshoot Transport Layer Security inspection issues](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-transport-layer-security)
