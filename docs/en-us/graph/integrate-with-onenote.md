<!-- Source: https://learn.microsoft.com/en-us/graph/integrate-with-onenote -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# OneNote API overview

OneNote is a digital notebook that lets customers track ideas and notes for home, school, or work, by typing, sketching, or voice, on the web, phone, tablet, or desktop. They can freely organize notes, switch devices and pick up where they left off, and collaborate on notes with others in real time.

By integrating your apps with OneNote, you can create empowering experiences across multiple platforms that reach millions of users worldwide. You can use Microsoft Graph to access notebooks, sections, and pages in OneNote to create solutions that help your users plan and organize ideas and information.

Note

The Microsoft Graph OneNote API will no longer support app-only authentication effective March 31, 2025. We recommend that you update your solutions to use [delegated authentication](https://learn.microsoft.com/en-us/graph/auth-v2-user).

<iframe src="https://www.youtube-nocookie.com/embed/VXd4OeQU1ek" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Why integrate with OneNote?

### Collect and organize notes and ideas

Use OneNote as a canvas where users can add and arrange their content. Microsoft Graph makes it easy to write apps that enable students to take notes and do research, families to share plans and ideas, or shoppers to share pictures. Your app can grab the information people want, send it to OneNote, and then help them organize it.

### Capture information in many formats

Capture HTML, embed images \(sourced locally or at a public URL\), video, audio, email messages, and other common file types. OneNote can even render webpages and PDF files as snapshots. Microsoft Graph supports a set of standard HTML and CSS for OneNote page layout, so you can use tables, inline images, and basic formatting to get the look you want.

### Use the OneNote ecosystem to enhance your core scenarios

Tap into other powerful OneNote features. The OneNote APIs in Microsoft Graph run OCR on images, support full-text search, auto-syncs clients, process images, and extract business card captures and online product and recipe listings. Use OneNote as your digital memory store in the cloud for notes and lightweight media, or as a data feed for domain-specific data.

### Reach millions of OneNote users on all major platforms

Use OneNote to increase your app usage. OneNote is preinstalled on new Windows devices, and is available for most platforms, online, and as part of Microsoft 365. When you publish apps that use the feature-rich OneNote environment, you have access to broad cross-platform market potential.

## What can I do with OneNote APIs in Microsoft Graph?

The following are some of the most popular requests for working with OneNote resources.

| Operation | URL |
| :--- | :--- |
| GET my notebooks | [https://graph.microsoft.com/v1.0/me/onenote/notebooks](https://developer.microsoft.com/graph/graph-explorer?request=me/onenote/notebooks&version=v1.0) |
| GET my sections | [https://graph.microsoft.com/v1.0/me/onenote/sections](https://developer.microsoft.com/graph/graph-explorer?request=me/onenote/sections&version=v1.0) |
| GET my pages | [https://graph.microsoft.com/v1.0/me/onenote/pages](https://developer.microsoft.com/graph/graph-explorer?request=me/onenote/pages&version=v1.0) |

## Learn more about OneNote APIs

Take an in-depth look at Microsoft Graph APIs to learn about the OneNote content updating capabilities. The topics in the following list show you how to create new OneNote pages and update existing pages with new content. You'll also learn about best practices in using Microsoft Graph to update OneNote notebooks.

### Work with OneNote

- [Use the OneNote REST API](https://learn.microsoft.com/en-us/graph/api/resources/onenote-api-overview)
- [Best practices](https://learn.microsoft.com/en-us/graph/onenote-best-practices)
- [Open the OneNote client](https://learn.microsoft.com/en-us/graph/open-onenote-client)
- [Use note tags in OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-note-tags)
- [Error codes for OneNote APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/onenote-error-codes)

### Work with OneNote pages

- [Input and output HTML in OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-input-output-html)
- [Get OneNote content and structure with Microsoft Graph](https://learn.microsoft.com/en-us/graph/onenote-get-content)
- [Create OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-create-page)
- [Update OneNote page content](https://learn.microsoft.com/en-us/graph/onenote-update-page)

### Work with OneNote page content

- [Create absolute positioned elements in OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-abs-pos)
- [Add images, videos, and files to OneNote pages](https://learn.microsoft.com/en-us/graph/onenote-images-files)
- [Use OneNote API div tags to extract data from captures](https://learn.microsoft.com/en-us/graph/onenote-extract-data)

## API reference

Looking for the API reference for this service?

- [OneNote API in Microsoft Graph v1.0](https://learn.microsoft.com/en-us/graph/api/resources/onenote-api-overview?view=graph-rest-1.0&preserve-view=true)
- [OneNote API in Microsoft Graph beta](https://learn.microsoft.com/en-us/graph/api/resources/onenote-api-overview?view=graph-rest-beta&preserve-view=true)

## Next step

- Use the [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) to try out the OneNote APIs with your own OneNote notebooks.
