<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage -->
<!-- Sitemap-Last-Modified: 2025-11-19 -->

# Building a host page

To instantiate Microsoft 365 for the web applications, a host must create an HTML page that contains an `iframe` element within it that's pointing to a particular [WOPI action URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-actions). A host page provides benefits, including:

1. Since the Microsoft 365 for the web application is hosted within a host page, the host page can communicate with the frame easily using [PostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage). This supports a richer integration between the host and Microsoft 365 for the web.
2. URLs displayed in the user’s browser are host URLs. So, from a user’s perspective, they're interacting with the host, not Microsoft 365 for the web. This also ensures that URLs copied and pasted by users are host URLs, not Microsoft 365 for the web URLs.

The host page must meet the following requirements:

- Use a `form` element and [POST](https://tools.ietf.org/html/rfc7231#section-4.3.3) the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) and [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) values to the Microsoft 365 for the web iframe [for security purposes](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage#passing-access-tokens-securely). Also, it's recommended to post `user_id` and `owner_id` values to the iframe. It's a requirement to post `user_id` and `owner_id` values for CSPP Plus scenarios.
- Include any JavaScript needed to interact with the Microsoft 365 for the web iframe using [PostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage).
- Manage [wd\* query string parameters](#pass-additional-query-string-parameters).
- Apply some specific CSS styles to the `body` element and Microsoft 365 for the web iframe to avoid visual bugs.
- Declare a `viewport` meta tag to avoid visual and functional problems in mobile browsers.

## Host page example

The [GitHub repository](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation) contains a [minimal example host page](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleHostPage.html).

Note

The example host page doesn't illustrate managing [**wd query string parameters**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage#pass-additional-query-string-parameters) or [**using PostMessage to interact with the Microsoft 365 for the web application iframe**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage). The following sections refer to these considerations in more detail.

## Passing access tokens securely

For security purposes, it's important that access tokens not be passed to the Microsoft 365 for the web iframe as a query string parameter. Doing so would greatly increase the likelihood of token leakage. To avoid this problem, hosts must pass the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) and [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) values to the Microsoft 365 for the web iframe using a form [POST](https://tools.ietf.org/html/rfc7231#section-4.3.3). This technique is illustrated, along with [dynamic iframe creation](#work-around-browser-iframe-behaviors), in code sample one.

## Enable clipboard permissions for the iframe

To enable the modern [Async Clipboard API](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard) inside Microsoft 365 for the web \(Word, Excel, PowerPoint, etc.\) when hosted in your page, you must explicitly grant clipboard permissions \(`clipboard-read` and `clipboard-write`\) to the iframe that loads the app.

Refer to the existing [SampleHostPage.html](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleHostPage.html) \(Code sample 1\) and add \(or confirm\) the appropriate permission policy.

### Why this matters

Enabling the Async Clipboard API improves copy/paste fidelity and usability and provides the following benefits:

- Users can paste using the ribbon or the right-click context menu in Chromium-based browsers \(not just keyboard shortcuts\).
- Cross-surface copy \(for example, Excel desktop → Excel for the web\) preserves formulas, conditional formatting, data validation, and other rich content previously lost.
- Programmatic clipboard operations become more predictable and future‑proof as legacy APIs are deprecated.

### What you need to do

1. Add the `allow` attribute to the iframe so the embedded Microsoft 365 app can request clipboard access:

   ```html
   <iframe
     id="office_frame"
     name="office_frame"
     allow="clipboard-read 'src'; clipboard-write 'src'"
     <!--
     other
     attributes
     --
   >
     ></iframe
   >
   ```

2. Ensure you aren't stripping or overwriting the iframe’s `allow` attribute during dynamic creation \(see Code sample 1\).

### Notes and cautions

- Browsers still require a user gesture for most clipboard reads and writes; granting permission does not bypass gesture requirements.
- If you omit these permissions, rich paste scenarios may silently fall back to html or plain text or fail.
- Legacy fallbacks \(for example, `document.execCommand('copy')`\) are deprecated; rely on the Async Clipboard API going forward.

### Dynamic creation excerpt \(showing clipboard permission\)

```javascript
var office_frame = document.createElement("iframe");
office_frame.id = "office_frame";
office_frame.name = "office_frame";
office_frame.title = "Office Frame"; // Accessibility
office_frame.setAttribute("allowfullscreen", "true");
office_frame.setAttribute(
  "sandbox",
  "allow-scripts allow-same-origin allow-forms allow-popups allow-top-navigation allow-popups-to-escape-sandbox"
);
// Grant clipboard permissions
office_frame.setAttribute(
  "allow",
  "clipboard-read 'src'; clipboard-write 'src'"
);
```

## Work around browser iframe behaviors

Some browsers exhibit unexpected handling of iframes when using bookmarks or the browser forward and back buttons.

In some cases, the Microsoft 365 for the web iframe is loaded twice in a single navigation, which can cause *file locked* or *access token expired* errors for users.

Also, occasionally the iframe isn't recreated at all, which causes the Microsoft 365 for the web application to load with the previous session’s state. This might cause a session to fail for a variety of reasons, including an expired token.

In order to avoid this result, hosts must dynamically create the Microsoft 365 for the web iframe using JavaScript, then dynamically submit it. This technique is shown in the sample host page:

***Code sample 1*** - *Markup from [SampleHostPage.html](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleHostPage.html) illustrating how to dynamically create the Microsoft 365 for the web iframe and pass access tokens securely*

```html
<body>

    <form id="office_form" name="office_form" target="office_frame" action="<OFFICE_ACTION_URL>" method="post">
        <input name="access_token" value="<ACCESS_TOKEN_VALUE>" type="hidden" />
        <input name="access_token_ttl" value="<ACCESS_TOKEN_TTL_VALUE>" type="hidden" />
        <input name="user_id" value="<USER_ID_VALUE>" type="hidden" />
        <input name="owner_id" value="<OWNER_ID_VALUE>" type="hidden" />
    </form>

    <span id="frameholder"></span>

    <script type="text/javascript">
        var frameholder = document.getElementById('frameholder');
        var office_frame = document.createElement('iframe');
        office_frame.name = 'office_frame';
        office_frame.id = 'office_frame';

        // The title should be set for accessibility
        office_frame.title = 'Office Frame';

        // This attribute allows true fullscreen mode in slideshow view
        // when using PowerPoint's 'view' action.
        office_frame.setAttribute('allowfullscreen', 'true');

        // The sandbox attribute is needed to allow automatic redirection to the O365 sign-in page in the business user flow
        office_frame.setAttribute('sandbox', 'allow-scripts allow-same-origin allow-forms allow-popups allow-top-navigation allow-popups-to-escape-sandbox');

        // Grant clipboard permissions
        office_frame.setAttribute(
          "allow",
          "clipboard-read 'src'; clipboard-write 'src'"
        );

        frameholder.appendChild(office_frame);
```

In an actual implementation, the `<OFFICE_ONLINE_ACTION_URL>`, `<ACCESS_TOKEN_VALUE>`, and `<ACCESS_TOKEN_TTL_VALUE>` strings must be replaced with appropriate [action URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls), [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), and [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) values.

## Pass additional query string parameters

Microsoft 365 for the web sometimes passes additional query string parameters to your host page. These query string parameters are of the form `wd*`. When you receive these query string parameters on your host page URLs, you must pass them, unchanged, to the Microsoft 365 for the web iframe.

In addition, if the [replaceState](https://developer.mozilla.org/en-US/docs/Web/Guide/API/DOM/Manipulating_the_browser_history#The_replaceState\(\)_method) method from the HTML5 History API is available in the user’s browser, you should remove the following parameters from your host page URL after passing them to the Microsoft 365 for the web iframe:

- `wdPreviousSession`
- `wdPreviousCorrelation`

Other `wd*` parameters must not be removed from the host page URL.

## Host page headers

If the host page headers are not correctly set, some browsers might cache the response, which can result in the host page not properly reloading when the user navigates to it. This can result in errors if the user reloads a cached page after the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), or [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#the-access_token_ttl-property) have expired. One way this can happen is by reloading the page using the forward and back buttons. For more information about cache management, see [**RFC 7234**](https://tools.ietf.org/html/rfc7234.html).

To prevent host page headers not being set correctly, use the following headers on the host page.

- [Cache-Control](https://tools.ietf.org/html/rfc7234#section-5.2): no-cache, no-store
- [Expires](https://tools.ietf.org/html/rfc7234#section-5.3): -1
- [Pragma](https://tools.ietf.org/html/rfc7234#section-5.4): no-cache

Other headers, such as [Date](https://tools.ietf.org/html/rfc7231#section-7.1.1.2) and [Vary](https://tools.ietf.org/html/rfc7231#section-7.1.4) are useful as well.

## Apply appropriate CSS styles

To ensure that the Microsoft 365 for the web applications behave appropriately when displayed through the host page, the host page must do the following:

- Apply specific CSS styles to the Microsoft 365 for the web iframe \(lines 22-33\) and the `body` element \(lines 15-20\).
- Set a `viewport` meta tag for mobile browsers \(lines 11-12\).
- Set an appropriate favicon for the page using the [favicon URL provided in WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#favicon-urls).

The following requirements are shown in the [sample host page](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleHostPage.html):

***Code sample 2*** - *Markup from [SampleHostPage.html](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/blob/master/samples/SampleHostPage.html) illustrating appropriate styles and favicons in a host page*

```html
<head>
  <meta charset="utf-8" />

  <!-- Enable IE Standards mode -->
  <meta http-equiv="x-ua-compatible" content="ie=edge" />

  <title></title>
  <meta name="description" content="" />
  <meta
    name="viewport"
    content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no"
  />

  <link rel="shortcut icon" href="<OFFICE APPLICATION FAVICON URL>" />

  <style type="text/css">
    body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      -ms-content-zooming: none;
    }

    #office_frame {
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      margin: 0;
      border: none;
      display: block;
    }
  </style>
</head>
```
