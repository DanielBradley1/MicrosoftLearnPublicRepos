<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/content-security-policy?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Configure Content Security Policy \(preview\)

\[This article is prerelease documentation and is subject to change.\]

[Content Security Policy](https://developer.mozilla.org/docs/Web/HTTP/CSP) \(CSP\) is a browser security standard that limits where an app can load scripts, styles, images, and other resources from, and which sites can frame it. A well-formed CSP is one of the strongest defenses against cross-site scripting \(XSS\), clickjacking, and data-injection attacks.

Microsoft Copilot Managed Runtime apps enforce a secure CSP by default. You don't have to author a policy to be protected - every app ships with a restrictive baseline. Read this article to understand:

- The default CSP policy
- How to tell when the default policy blocks something your app needs
- How to extend the default policy for legitimate external resources

## How CSP applies to Copilot Managed Runtime apps

Because the policy is environment-wide and security-sensitive, **an administrator owns CSP configuration**. As a developer, your job is to know the default policy, recognize when it blocks a resource your app legitimately needs, and request the specific directive change from your administrator.

Note

CSP changes are applied at the platform and can take several minutes to propagate. After a change, reload your app and recheck the browser console.

## The default policy

By default, apps enforce a restrictive policy. Each directive controls a category of resource: `'self'` means only this app's own origin, `'none'` means nothing is allowed, and `data:` allows inline content supplied through data URIs.

| Directive | Default value | Description |
| --- | --- | --- |
| [`default-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/default-src) | `'self'` | Only allow content \(scripts, images, and so on\) to load from the same origin. |
| [`style-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/style-src) | `'self' 'unsafe-inline'` | Allow styles from own domain and inline styles. |
| [`form-action`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/form-action) | `'none'` | Prevent all form submissions, including to self. |
| [`frame-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-src) | `'self'` | Only allow embedding frames from own domain. |
| [`child-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/child-src) | `'none'` | Disallow loading `<iframe>`, `<embed>`, or `<object>` children. |
| [`img-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/img-src) | `'self' data:` | Allow images from own domain and data. |
| [`media-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/media-src) | `'self' data:` | Allow audio/video from own domain and inline media via data URIs. |
| [`script-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/script-src) | `'self' <platform>` | Allow scripts from own domain. |
| [`worker-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/worker-src) | `'none'` | Disallow use of web workers or service workers. |
| [`object-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/object-src) | `'self' data:` | Allow `<object>` elements only from own domain and inline data. |
| [`connect-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/connect-src) | `'self'` | Allow network requests \(AJAX/fetch/WebSocket\) from own domain; no external connections. |
| [`font-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/font-src) | `'self'` | Allow fonts from own domain and inline font definitions. |
| [`base-uri`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/base-uri) | `'self'` | Only allow `<base>` to point to own domain. |
| [`manifest-src`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/manifest-src) | `'none'` | Disallow loading of web app manifests. |
| [`frame-ancestors`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) | `'self' <platform>` | Controls where the app itself can be embedded. |

A few consequences of this baseline are worth calling out:

- **`connect-src 'self'`** Your app can make network requests to its own origin, but external origins are blocked. Connector data access goes through the Microsoft Copilot Managed Runtime SDK and host, which route calls through the platform - so most apps never need to relax this. You adjust `connect-src` only for an external endpoint you call directly, such as an Azure Monitor Application Insights collection URL.
- **`script-src 'self' <platform>`** Scripts must come from your app's own origin. Inline scripts and third-party script CDNs are blocked unless explicitly allowed.
- **`frame-ancestors 'self' <platform>`** Other sites can't embed your app in an iframe unless their origin is added. See [Allow your app to be embedded](#allow-your-app-to-be-embedded).

## Customize directives for external resources

When your app legitimately needs a resource that the default policy blocks - such as a font from a CDN, an image host, or a telemetry endpoint - an administrator adds the source to the relevant directive for the environment.

Custom values **merge with** the default value of a directive. For example, allowing an extra script source produces:

```
script-src 'self' https://contoso.com
```

The one exception is a directive whose default is `'none'`: your custom values **replace** `'none'` rather than appending to it. For instance, if your app uses a web worker, an administrator sets `worker-src` to `'self'`, replacing the default `'none'`.

Important

Keep additions as narrow as possible. Add specific origins \(`https://contoso.com`\), never wildcards like `*` or `'unsafe-inline'` for scripts, which defeat the purpose of the policy.

## Allow your app to be embedded

By default, only your app and the platform can frame your app, because `frame-ancestors` is set to `'self' https://*.powerapps.com`. If you embed an app in another host - a custom website, a SharePoint page, or another app - the browser blocks the frame and logs a violation like:

```
Refused to frame '<your-app-url>' because it violates the following Content Security Policy directive: "frame-ancestors 'self' https://*.powerapps.com"
```

To allow the embedding, an administrator adds the host's origin to `frame-ancestors` for the environment - for example, `https://contoso.com`. Because custom values merge with the default, the effective directive becomes:

```
frame-ancestors 'self' https://*.powerapps.com https://contoso.com
```

## Identify a CSP violation

When something in your app silently fails to load, check whether CSP blocked it:

1. Open your app in the browser.
2. Open the browser developer tools \(F12, or Ctrl+Shift+I\).
3. Go to the **Console** tab and filter to **Errors**.
4. Look for messages such as *"Refused to connect to 'https://…' because it violates the following Content Security Policy directive: …"*. The message names both the blocked URL and the directive that blocked it.
5. Note the URL and directive. That's exactly the source and directive an administrator needs to allow.

After the policy is updated and has propagated, reload the app and confirm the console no longer shows the violation.

## Enforcement and report-only mode

CSP can run in two modes:

- **Enforced \(default\).** The browser blocks any resource that violates the policy.
- **Report-only.** The browser allows everything but reports what *would* have been blocked. Use this mode to roll out or tighten a policy without breaking a running app.

The recommended way to introduce or change a policy is to enforce it in a development or test environment first, run report-only in production to surface any real violations, and only then enforce it in production.

## Report CSP violations

An administrator can configure a **reporting endpoint** - a URL the browser sends a JSON report to whenever the policy is violated. The browser sends reports whether the policy is enforced or report-only. This endpoint is the primary tool for discovering what a stricter policy would break before you turn it on.

## Related articles

- [Connect an app to data \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/connect-to-data?view=o365-worldwide)
- [Copilot Managed Runtime architecture \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/architecture?view=o365-worldwide)
- [Content Security Policy reference \(MDN\)](https://developer.mozilla.org/docs/Web/HTTP/CSP)
