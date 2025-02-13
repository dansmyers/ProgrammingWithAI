# Search Engine

<img src="https://preview.redd.it/gooby-extension-for-chrome-and-opera-v0-5zpyl95ck2jd1.png?auto=webp&s=9d554952ab292f320ab3453d7438d84e6829bf0a" width="600px" />

[Does the name "Gooby" ring a bell?](https://www.youtube.com/watch?v=ZvkGDqlRCvY)

## Due

## You can work with other students to complete this project

## Overview

In a previous lab we looked at creating a proxy server for the `gemini://` protocol space. Now, you're going to build on that to create a working **search engine** for Geminispace.

This project is intentionally open-ended and, frankly, ambitious. I'm excited to see what you're able to come up with.

The project has three components:

1. A *web crawler* that explores the network of `gemini://` pages and saves them for processing in the next step.

2. A program to build the *search index*. This program needs to extract search terms from the pages found by the crawler, then build and save a mapping from each search term to the list of pages that contain it.

3. The actual search engine interface, similar to Google: the frontend is a text entry for the search term, the backend looks up relevant pages and returns them in a list.

For each phase, I'm expecting you to have conversations with your AI collaborator to work through the design options and make reasonable choices. The sections below will give you some tips for each phase, but ultimately you get to choose the vision that you want to implement.

**Don't worry about going too hard with features right away**. For the first version, you don't need to worry about any advanced search features or ranking search results. If you get a working version you can think about adding some more features.

## Web Crawler

The crawler is the first phase of the search engine. Its purpose is to collect the *corpus* of documents that will be used to build the search engine index.

The basic crawling procedure is a breadth-first search:

- Retrieve the starting page
- Extract all links it contains and put them in a queue
- While the queue is not empty, retieve the next page, extract its links, and put them in the queue

Therefore, given enough time, the crawler will eventually explore every page reachable from its starting location.

Practical crawlers will run in parallel from multiple starting locations to reach disconnected parts of the web graph. They also try to crawl in an intelligent way by prioritizing pages that are likely to be high value.

Major search engine crawlers look for a file called `robots.txt` at the root of the site, which site owners can use to supply instructions for how to crawl the site effectively, or indiciate that some pages shouldn't be indexed.

For this part, you need to design and implement a crawler for the `gemini://` space. Here are some tips:

- Only crawl pages beginning with `gemini://` and having the `text/gemini` return type. You don't need to crawl plain text, HTML, or other file formats.

- Only follow links to other `gemini://` pages. Ignore `http://` links.

- Respect `robots.txt`. Most sites will not have one, but check if it's present. If so, respect instructions to not crawl the page.

- Add a small randomized delay in between page accesses so that you aren't crawling a site too aggressively, which can look like a malicious scan or denial-of-service attack.

- Save the pages you retrieve to local storage so you can process them later.

- Implement some logging so that you can see what pages are being requested, which ones are returned, and which requests fail. This may be important for debugging.

- **Set a cap on the number of pages**. Make this very low initially, like 10-20, while you work out the basic crawler. You can increase it once you have a working system, but it's okay to keep it in the <100 range for this project. We don't need to crawl thousands of pages.

FYI: My first AI generations did not quite work correctly. I had to do some debugging and even (*quelle horreur!*) write some code by hand.

## 
