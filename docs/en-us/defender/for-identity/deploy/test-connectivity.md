<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/test-connectivity -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Test Microsoft Defender for Identity connectivity

The Defender for Identity sensor requires network connectivity to the Defender for Identity service. Depending on which version of the sensor you deployed, see [Sensor v2.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2) or [Sensor v3.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3).

Test connectivity before deployment to verify that the sensor server can reach the Defender for Identity cloud service. Use the [browser connectivity test](#test-connectivity-using-a-browser) or [PowerShell connectivity test](#test-service-connectivity-using-powershell). You can also use these tests to troubleshoot connectivity after deployment.

For more information, see [v2.x required ports](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2#required-ports).

Note

To get the name and other important details about your Defender for Identity workspace, see the [About page](https://learn.microsoft.com/en-us/defender-for-identity/settings-about) in the [Microsoft Defender XDR](https://security.microsoft.com/) portal.

## Test connectivity using a browser

Use this procedure to test v2.x sensor connectivity from a browser:

1. Open a browser. If you're using a proxy, make sure that your browser uses the same proxy settings being used by the sensor.

   For example, if the proxy settings are defined for **Local System**, you'll need to use PSExec to open a session as **Local System** and open the browser from that session.
2. Browse to the following URL: `https://<your_workspace_name>sensorapi.atp.azure.com/tri/sensor/api/ping`. Replace `<your_workspace_name>` with the name of your Defender for Identity workspace.

   Important

   You must specify `HTTPS`, not `HTTP`, to properly test connectivity.

   **Expected result**: The response shows the latest sensor version number, confirming that the server can reach the Defender for Identity HTTPS endpoint.

   For some older workspaces, the message returned could be *Error 503 The service is unavailable*. This is a temporary state that still indicates success. For example:

   ![Screenshot of an HTTP 200 status code \(OK\).](https://learn.microsoft.com/en-us/defender-for-identity/media/configure-proxy/test-proxy.png)

   Other results might include the following scenarios:

   - If you don't get *Ok* message, then you may have a problem with your proxy configuration. Check your network and proxy settings.
   - If you get a certificate error, ensure that you have the required trusted root certificates installed before continuing. For more information, see [Proxy authentication problem presents as a connection error](https://learn.microsoft.com/en-us/defender-for-identity/troubleshooting-known-issues#proxy-authentication-problem-presents-as-a-connection-error). The certificate details should look like this:

     ![Screenshot of the required certificate path.](https://learn.microsoft.com/en-us/defender-for-identity/media/configure-proxy/certificate.png)

## Test service connectivity using PowerShell

These commands test v2.x connectivity to the workspace sensor API.

**Prerequisites**: Before running Defender for Identity PowerShell commands, make sure that you downloaded the [Defender for Identity PowerShell module](https://www.powershellgallery.com/packages/DefenderForIdentity/).

Sign in to your server and run one of the following commands:

- To use the current server's settings, run:

  ```powershell
  Test-MDISensorApiConnection
  ```

- To test settings that you're planning on using, but aren't currently configured on the server, run the command using the following syntax:

  ```powershell
  Test-MDISensorApiConnection -BypassConfiguration -SensorApiUrl 'https://contososensorapi.atp.azure.com' -ProxyUrl 'https://myproxy.contoso.com:8080' -ProxyCredential $credential
  ```


  Where:


  - `https://contososensorapi.atp.azure.com` is an example of your sensor URL, where *contoso* is the name of your workspace.
  - `https://myproxy.contoso.com:8080` is an example of your proxy URL

For more information, see the [MDI PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/defenderforidentity/test-mdisensorapiconnection).

## Check v3.x connectivity requirements

The v3.x sensor uses Microsoft Defender for Endpoint service endpoints. Follow the [v3.x network requirements](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#network-requirements) for the applicable Defender for Endpoint connectivity guidance.

## Next steps

[Download and install the Microsoft Defender for Identity sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor)
