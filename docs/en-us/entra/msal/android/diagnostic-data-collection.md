<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/diagnostic-data-collection -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Set up MSAL logs collection

In order for us to be able to effectively debug your issues, please follow the steps below

### 1. Set up MSAL logs collection

Please follow the steps [here](https://github.com/AzureAD/microsoft-authentication-library-for-android/wiki/Logging) to hook up your logger. If possible, please print this to a separate file \(as opposed to printing to logcat\).

If you can reproducing the issue in-house, it would be ideal to turn on *VERBOSE* logging, by setting the log\_level property in your configuration file:

```
{
  "client_id" : [YOUR_CLIENT_ID],
  "authorization_user_agent" : "DEFAULT",
  "redirect_uri" : [YOUR_REDIRECT_URI],
  "authorities" : [YOUR_AUTHORITIES]
  "logging": {
    "log_level": "verbose"
  }
}
```

You can also do this by calling the following method ***AFTER*** initializing PublicClientApplication. It's critical that it happens after the initialization, or it will be overwritten by the configuration initialization.

```Java
Logger.getInstance().setLogLevel(LogLevel.VERBOSE);
```

### 2. Reproduce the issue

- If you can reproduce the issue,

  - If possible, uninstall everything, re-install everything, and reproduce the issue from scratch.
  - Reproduce the issue in one go.
  - Collect logs right away.

- If you cannot reproduce the issue in-house, please specify the \(estimated\) timestamp and/or correlation ID, so that we can pinpoint the issue.

### 3. Upload logs and the information regarding the issue.

1. Details about your scenario - what you're trying to achieve.
2. The steps to reproduce the issue.
3. Version of ADAL/MSAL you're currently using.
4. Your MSAL configuration file.
5. MSAL logs.
6. Company Portal AND Authenticator Logs \(if installed\).

   - This can be uploaded via the apps' ***Help/Support*** pages.
   - You will be provided a set of *correlation ID* after uploading the logs. Please forward those IDs to us.
   - [Create a PowerLift Incident in MS Authenticator and Company Portal?](https://stackoverflow.microsoft.com/questions/148465)
