<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/test-launch/auth-best-practices -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Best practices for authentication in the Microsoft 365 Document Collaboration Partner Program

The Microsoft 365 Document Collaboration Partner Program \(MDCPP\) enables your users to view and edit Excel, PowerPoint, and Word documents directly in your collaboration application. Consider the following authentication best practices as you develop and test your solution.

## Fewer sign-in prompts with single sign-on \(SSO\)

If you choose to implement SSO, we recommend that you use WebView2 hosting inside of desktop versions of Office applications \(i.e., on Windows and Mac\) so that you have the highest reliability for authentication.

In order for your users to have fewer sign-in prompts when SSO is implemented, be sure to set the [CoreWebView2EnvironmentOptions.AllowSingleSignOnUsingOSPrimaryAccount](https://learn.microsoft.com/en-us/dotnet/api/microsoft.web.webview2.core.corewebview2environmentoptions.allowsinglesignonusingosprimaryaccount) property in WebView2.

For the sign-in prompts that must be displayed, allow pop-up windows for `https://login.microsoftonline.com`.

- Windows: Handle the WebView2 [CoreWebView2.NewWindowRequested Event](https://learn.microsoft.com/en-us/dotnet/api/microsoft.web.webview2.core.corewebview2.newwindowrequested), allowing navigation to that domain.
- Mac: In the [WKWebView](https://developer.apple.com/documentation/webkit/wkwebview), filter pop-up windows based on URL by inspecting the `navigationAction.request.url` property inside the [WKUIDelegate.webView\(\_:createWebViewWith:for:windowFeatures:\)](https://developer.apple.com/documentation/webkit/wkuidelegate/webview\(_:createwebviewwith:for:windowfeatures:\)) method.

## IT Admin configuration of single sign-on \(SSO\) on Mac

If your solution implements SSO, be sure to share the following guidance with organizations deploying your solution so their IT admins can allow their users to use SSO on Mac.

- [Microsoft Enterprise SSO plug-in for Apple devices](https://learn.microsoft.com/en-us/entra/identity-platform/apple-sso-plugin)

## Continuous Access Evaluation \(CAE\) and how it may impact performance

The APIs implemented for the MDCPP use [Continuous Access Evaluation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation). Be sure to consider the following and related articles so that your authentication flows account for how CAE may impact performance of your solution.

- [Claims challenges, claims requests and client capabilities](https://learn.microsoft.com/en-us/entra/identity-platform/claims-challenge)
