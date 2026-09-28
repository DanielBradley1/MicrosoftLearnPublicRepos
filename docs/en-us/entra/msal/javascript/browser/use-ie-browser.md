<!-- Source: https://learn.microsoft.com/en-us/entra/msal/javascript/browser/use-ie-browser -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# Known issues on Internet Explorer browsers \(MSAL.js\)

For better compatibility with Internet Explorer, we generate the Microsoft Authentication Library for JavaScript \(MSAL.js\) for [JavaScript ES5](https://262.ecma-international.org/5.1/), but there are other things to consider as you develop your application.

## Run an app in Internet Explorer

Internet Explorer lacks native support for JavaScript Promises, required by MSAL.js.

To support JavaScript Promises in an Internet Explorer app, reference a Promise polyfill before you reference MSAL.js.

```html
<script
  src="https://cdnjs.cloudflare.com/ajax/libs/bluebird/3.3.4/bluebird.min.js"
  class="pre"
></script>
```

## Debugging an application running in Internet Explorer

### Running in production

Deploying your application to production \(for instance in Azure Web apps\) normally works fine, provided the end user has accepted popups. We tested it with Internet Explorer 11.

### Running locally

To debug your application locally, temporarily disable Internet Explorer's *Protected Mode* during your debugging session.

1. In Internet Explorer, select **Tools** > **Internet Options** > **Security** tab > **Internet** zone.
2. Clear the **Enable Protected Mode \(requires restarting Internet Explorer\)** checkbox.
3. Select **OK** to restart Internet Explorer.

When you're done debugging, follow the previous steps and select \(instead of clear\) the **Enable Protected Mode \(requires restarting Internet Explorer\)** checkbox.

## Next steps

Learn more about [Known issues when using MSAL.js in Internet Explorer](https://learn.microsoft.com/en-us/entra/msal/javascript/browser/known-issues-ie-edge-browsers).
