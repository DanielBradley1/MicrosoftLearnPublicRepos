<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# Embedded native authentication web fallback overview

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

**Authentication approach:** Embedded native authentication.

An Embedded native authentication interaction can require behavior that your app can't complete natively. Browser fallback is a recovery path that starts a separate, configured browser sign-in. It doesn't resume the native transaction.

Important

The Native Authentication API V2 is in preview. The [Native Authentication API V1](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1) remains generally available. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to preview features.

## Service-required and client-initiated fallback

The API uses states, actions, and links to describe the next interaction. A client can present available actions or apply application flow logic to select an allowed operation.

The Native Authentication API can return the following response:

```json
{
    "state": "redirect"
}
```

This response can contain only `state`. It doesn't supply a continuation token or a browser handoff URL. Stop the native transaction instead of requiring `action`, `continuationToken`, or `_links` on this response.

At the OAuth boundary, browser-required handling can instead use `invalid_grant` with `web_redirect_required`. Handle that OAuth error separately from native JSON states.

A client can also reach a response it can't safely process: an unknown required action, a missing required field, an unsupported credential interaction, or malformed data. Offer a separately configured browser sign-in if your app has one, or show a clear failure without marking the user signed in.

Unknown optional properties or links are different. Ignore those additions while processing the required fields; their presence alone doesn't require a switch to the browser.

## Transaction and user-experience boundaries

A separate browser sign-in restarts authentication; it doesn't preserve native progress.

Native continuation tokens belong to the active transaction and current operation. They aren't general-purpose browser sign-in tokens. Don't add passwords, one-time passcodes \(OTPs\), native continuation tokens, or security tokens to browser URLs. Let the configured authorization flow handle its registered redirect. Keep authorization codes and other credentials out of logs and telemetry. Use the configured interactive authorization flow, not an arbitrary URL supplied by untrusted content.

The browser flow can have different interactions from the native flow. Don't mark the app signed in until its configured authentication integration reports success. If the user cancels or the browser flow fails, retain a clear signed-out or incomplete state.

## Browser integration

Use a supported browser-delegated integration to open the browser and handle its registered redirect. The [mobile quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?pivots=external) and [single-page app quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?pivots=external) describe those integration paths. Keep browser completion, cancellation, and error handling separate from native transaction processing.

For an application configured with Bring Your Own UX \(BYO UX\), normal browser authorization uses the configured self-hosted page. A native `redirect` response isn't a URL or parameter for bypassing that configuration to Microsoft-hosted pages. Use the configured browser authorization flow rather than a constructed bypass URL.

If your app doesn't have a supported browser path, explain that the interaction can't be completed. Don't automatically replay credentials or switch the active transaction to V1.

## V1 fallback

V1 clients need to support web fallback. The client declares its supported interactions through challenge types. For example, an email-with-password user flow requires both `oob` and `password`; omitting either can cause the service to require browser authentication. See [V1 challenge types](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1#v1-challenge-types-and-capabilities).

For existing SDK integrations, use the [SDK library references](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1#sdk-references) for fallback interfaces. V1 fallback starts a separate browser sign-in, not a resumable native-to-browser continuation.

## Related content

- [Embedded native authentication flow](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-flow).
- [The Native Authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication).
- [Migrate from Native Authentication API V1 to V2](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2).
