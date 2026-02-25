# URL Shortener

## Overview

Let's work on building a basic URL shortener application. This will serve as a simple intro to full-stack web apps, with both a front-end web interface and a back-end that does some useful work.

The URL shortener will have a an input box and a button labeled "Shorten". When the user enters a website URL and clicks the button, the front-end will send a request to the back-end server. The back-end does three things:

- Calculate a shortned URL name
- Store the mapping from the shorter name to the full name in a lookup table
- Return the shortened name back to the user

Given a shortened URL name, there should also be a method that retrieves the full-length URL and then redirects the browser to it.

## Setup

Create a dedicated directory for this project:
```
mkdir 5-URL_Shortener
```
Then `cd` into it:
```
cd 5-URL_Shortener
```

You will need the Python Flask module for the back-end server. Install by typing the following command in the terminal:
```
pip install flask
```
Enter *Yes* if the program prompts you to accept the installation.

## Prompt

Use the specs-driven development approach.

Go to the regular Claude chat.
> I want to create a simple URL shortener application. I want to use Python Flask for the server back-end and basic HTML/CSS/JavaScript for the front-end. The application should have a text box on the front-end web page with a submit button. When the user submits a URL, the back-end should take it, determine a shortened version, then save a mapping from the short name to the full name in a lookup table. Return the shortened name to the user. It should also have the ability to take a shortened URL and go to its corresponding web page. Discuss this project with me and help me produce a Markdown specifications document for my AI coding agent. You don't need to write any code, just help me create the spec. I am learning about programming, so help me understand the reasoning behind the design choices we're discussing.

Work through the design process and generate the specs document. Take a look at it and make sure everything looks okay.

After you've done that, copy the spec output into a file named `specs.md` in your `5-URL_Shortener` directory.

You can then run `claude` and ask it to use the specs document to create a phased implementation plan with tests for each phase. Once the plan exists, approve it, and generate the code.

##
