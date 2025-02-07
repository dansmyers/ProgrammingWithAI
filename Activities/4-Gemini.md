# Gemini

## Overview

The Gemini protocol is a lightweight hypertext document system. That is, it's a way to define a collection of documents with links between them and make those documents accessible over the Internet.

If you think that sounds like the World Wide Web, you're right. Gemini is like a lightweight, low-featured, text-oriented, old-school version of the Web, where the primary unit is a basic text document with limited markup, some links, and not much else.

What's the point of this? Some people find it aesthetically appealing, or like the idea of a lower-featured Internet that is technically incapable of supporting things like tracking, ads, or embedded media.

All Gemini pages use URL identifiers starting with `gemini://`. For example, the main page of the Gemini project is `gemini://geminiproject.net`. To access a Gemini page,

1. The broswer sends a request to the Gemini server using an appropriate format (more on this below)
2. The browser responds with the requested page content, again in the format defined by the protocol

This is the same flow as a normal HTTP access, but the request and response formats defined by Gemini are not the same as regular HTTP, so a conventional browser can't retrieve data from a Gemini server.

## Gemini Viewer

The goal of this lab is to write a proxy viewer for Gemini pages. You're going to create an `index.html` page with an input field for a Gemini URL.

When the user inputs a `gemini://` URL, your page will send it to a backend Flask server using a `/api/gemini` route. Your backend will then do the behind-the-scenes work of creating a Gemini request, sending it to the target server, and receiving the response.

Once you have the response data, you'll send it back to the front-end and display it.

### Example

[Here is an example portal](https://portal.mozz.us/gemini/geminiprotocol.net/) you can use to browse Gemini pages through your regular web browser.

## Questions

Use the [offical FAQ](https://geminiprotocol.net/docs/faq.gmi) to answer these question.

- What are the design goals of Gemini?
- What is Gopher? How does Gemini relate to Gopher?
- How does Gemini relate to HTTP?

Use the [official Gemini tech overview](https://geminiprotocol.net/docs/tech-overview.gmi) to answer these questions.

- What is the basic format of the Gemini request?
- What is the basic format of the Gemini response?
- The section on response status codes contains the following.
>Status codes beginning with 2 are SUCCESS status codes, meaning:
>The request was handled successfully and a response body will follow the response header. The <META> line is a MIME media type which applies to the response body.
What does that mean? What is a MIME media type?

- What is the text/gemini media format? How does it compare to HTML?

## Implementation

Use your AI tools to implement the Gemini proxy page and backend server. I'm leaving this step deliberately vague so you have a chance to work through it on your own.

Think about the process we've used in previous projects and how the system should be organized.

### Testing

When you're ready to test, use `gemini://geminiprotocol.net/` as your test URL.

*Important note*: the closing `/` is required to retrieve the page correctly. 

## More features

If you get the basic proxy working you can add some more features:

- Rendering the text/gemini format into a page with headers and links
- Making links functional, so you can automatically browse to a linked Gemini page

