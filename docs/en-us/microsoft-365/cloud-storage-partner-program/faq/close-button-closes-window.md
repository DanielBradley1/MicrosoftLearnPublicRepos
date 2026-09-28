<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/close-button-closes-window -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Why should I avoid using the CloseButtonClosesWindow property in Microsoft 365 for the web?

Browsers prevent JavaScript from closing windows that aren’t owned by the script that calls `window.close`, so in many cases [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) will not behave properly. In such cases an error may be logged on the browser developer console:

`Scripts may close only the windows that were opened by it.`

The calling script is not reliably given any information that the `close()` call failed, so Microsoft 365 for the web can’t detect when this happens and change behavior. Thus, hosts who wish to close the current window when the *Close* UI is activated should prefer to use [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage) and handle the `UI_Close` message for reliable close behavior.
