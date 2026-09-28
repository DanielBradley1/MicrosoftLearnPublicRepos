<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-global-secure-access-mobile-client-advanced-diagnostics -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# Troubleshoot the Global Secure Access mobile client: Advanced diagnostics

This article explains how to troubleshoot the Global Secure Access mobile client for Android and iOS using the advanced diagnostics utility.

## Introduction

The Global Secure Access client runs in the background and routes relevant network traffic to Global Secure Access. It doesn't require user interaction. The advanced diagnostics tool makes the client's behavior visible to the administrator and helps with troubleshooting.

## Services section

The **Services** section shows the active services running in the traffic forwarding profiles.

![Screenshot of the Services section in the Global Secure Access mobile client.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/troubleshoot-global-secure-access-mobile-client-advanced-diagnostics/services-section.png)

## Troubleshooting section

The Troubleshooting section enables users to troubleshoot and share information with the administrator. To view the **Troubleshooting** section:

1. Open the Microsoft Defender app and select the **Global Secure Access client** tile.
2. Select the **Troubleshooting** section to open it.

In addition to **Get latest policy** and **Clear cached data**, users can also [collect and send logs](#collect-and-send-logs) and [run advanced diagnostics](#advanced-diagnostics).

### Collect and send logs

This troubleshooting function allows users to collect logs from the client and send the logs to Microsoft support for investigation. To access the **Collect and send logs** function:

1. Open the Microsoft Defender app and select the **Global Secure Access client** tile.
2. Expand the **Troubleshooting** section and select **Collect and send logs**.

The user can copy and share the Incident ID with Microsoft Support for their reference.

![Screenshot of a sample pop-up Incident ID message.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/troubleshoot-global-secure-access-mobile-client-advanced-diagnostics/incident-id.png)

### Advanced diagnostics

This troubleshooting function shows the client's health and lets users capture network and hostname traffic. To access the **Advanced diagnostics** function:

1. Open the Microsoft Defender app and select the **Global Secure Access client** tile.
2. Expand the **Troubleshooting** section and select **Advanced diagnostics**.

#### Health Check tests

The **Health Check** runs a series of device and policy tests to verify that the client and its components are working correctly. To run the health check:

1. Navigate to the **Advanced diagnostics** view.
2. Select **Health Check**.

To update the health check status, select **Refresh Health Check**.

![Screenshot of the Health Check view showing that the completed device and policy tests passed.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/troubleshoot-global-secure-access-mobile-client-advanced-diagnostics/refresh-health-check.png)

#### Network and hostname traffic

This function allows users to capture information about their network and hostname traffic. A good practice is to start the traffic capture, reproduce the issue, and then stop the capture. To capture network and hostname traffic:

1. Navigate to the **Advanced diagnostics** view.
2. Select **Network and hostname traffic**.
3. Select **START**.
4. Reproduce the issue.
5. Select **STOP** to stop capturing network and hostname traffic.

To review the captured traffic, go to the **NETWORK** and **HOSTNAME** tabs.

To download the captured traffic to share with Microsoft Support, select **DOWNLOAD**.

![Screenshot of Network and hostname traffic view showing a list of sample network traffic.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/troubleshoot-global-secure-access-mobile-client-advanced-diagnostics/network-host-name.png)

## Related content

- [Troubleshoot the Global Secure Access Client for Windows: Advanced Diagnostics](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-global-secure-access-client-advanced-diagnostics)
