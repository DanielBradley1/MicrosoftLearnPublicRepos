<!-- Source: https://learn.microsoft.com/en-us/intune/user-help/troubleshooting/troubleshoot-device-access-windows -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Troubleshoot Windows device access

**Applies to**

- Windows

This article describes how to resolve access issues for an enrolled Windows device.

## Check Wi-Fi connection

A connection to Wi-Fi is required to access work or school resources. Verify that you're connected to Wi-Fi and then try accessing the resources again.

## Add work or school account in Settings app

If your account isn't appearing in the **Settings** app, go through the setup steps in the Settings app again.

1. Open the **Settings** app.
2. Select **Accounts**.
3. Identify the version of Windows you're using, and then select **Access work or school**.
4. Check for your account. If it's not listed, select **Connect** to add it.
5. Sign in with your work or school account, and then follow the onscreen prompts to finish connecting.

When complete, your account appears as a connection, and you have access to any resources your organization makes available.

## Contact IT support for access problems

If you see your work or school account listed in the Settings app, then your device and account are already connected. Contact your IT support person for further help. They may have put restrictions or requirements in place that prevent you from accessing certain resources. Sign in the Company Portal app or [website](https://go.microsoft.com/fwlink/?linkid=2010980) for your organization's helpdesk details.

## Error messages

### We couldn't auto-discover a management endpoint matching the username entered. Please check your username and try again. If you know the URL to your management endpoint, please enter it.

**Cause**: Your account couldn't be verified alongside the provided URL \(also referred to as the management endpoint\).

#### Resolution

1. Re-enter your username and password.
2. If it still doesn't work, contact your IT support person to get the correct URL \(example: `www.yourcompany.onmicrosoft.com`\).
3. When prompted to, enter the provided URL.

### It looks like you're not connected. Make sure you're connected to the network.

**Cause**: Your device isn't connected to Wi-Fi and a connection is required to add a work or school account.

#### Resolution

Connect to a Wi-Fi network and then try adding your account again.

### Your device is already being managed by an organization.

**Cause**: Your device has already been enrolled in Intune or another mobile device management \(MDM\) provider.

#### Resolution

Contact your IT support person to find out how they want you to proceed.
