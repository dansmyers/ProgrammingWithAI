# URL Shortener

<img src="https://camo.githubusercontent.com/f6acc4ef19cb8772b4e0ca1f82af8d1478dc3d1bcd19a8937985c64003102fc6/68747470733a2f2f6d656469612e7069746368666f726b2e636f6d2f70686f746f732f3563333737373038313765656663353130663162333536352f31363a392f775f313238302c635f6c696d69742f44617669642d426f7769652e6a7067" width="400px" />

David Bowie using a computer, ca. 1994

## Overview

Let's get started by building a URL shortening application. In addition to letting us play with Cursor, this will introduce (or review) some important concepts from web application programming that will be beneficial for future projects.

Our basic application will do the following:

- The user will load a web page with a field where they can enter a URL
- When the user submits the page, the long URL is sent to the server
- The server reads the URL, produces a shortened version, and stores the mapping in an internal data structure
- The server sends back the shortened URL that's displayed on the original page for the user

When the user submits a shortened URL, a different function on the server will retrieve the associated long URL from the data store, then redirect to that page.

Our goals are:

- Learn about basic web apps and routes using Python's Flask framework
- Learn about the interaction of client and server sides of a web application
- Think about the structure of the application before we begin generating
- Practice generating code with Cursor
- Practice explaining unfamiliar code and getting answers to questions
- Debug AI-generated code

## Prelude

Open Cursor.

The first thing you'll need to do is open a working directory. Create a new directory on your local computer called `Programming_with_AI` (wherever you would keep your class files). Open that directory with Cursor.

You should see a terminal at the bottom of the application showing your `Programming_with_AI` as the current working directory.

Create a subdirectory for this project and then `cd` into it.
```
mkdir URL_Shortener

cd URL_Shortener
```

## Virtual Environments

Next, we're going to set up a **virtual environment** for installing Python packages. The virtual environment is like an isolated version of Python. Packages that you install into it are only used locally, without affecting the global system-wide Python installation or other virtual environments. The reasons why this is beneficial:

- It allows you to avoid conflicts between different package versions for different projects and the global Python installation
- It allows you to customize the package versions used by different applications (e.g., Project A needs Flask 1.0 while Project B needs Flask 2.0)
- It's possible to create a special `requirements.txt` file that lists all of the dependencies for a project and their versions, which can then be automatically installed

Once you're in `URL_Shortener`, create a virtual environment by running the following in the terminal
```
python3 -m venv env 
```
You'll see a directory named `env` appear in the file browser. You can then activate the virtual environment using
```
source env/bin/activate
```
If you're using a Windows computer, use:
```
.\env\Scripts\activate
```
The terminal prompt will change to something similar to
```
(env) dmyers@daniels-mbp URL_Shortener % 
```

From here, you'll use the terminal as normal, but any Python packages you install will only exist within the virtual environment.

When you need to leave the virtual environment (because you're done working on this project), type
```
deactivate
```
at the terminal and you'll go back to the standard prompt. You can re-enter the environment using the `source` command above.

## Starting the Project

Create a new file and open it:
```
touch url_shortener.py

code url_shortener.py
```
You'll see a new tab pop up at the top of the application with an empty file.

From here, we have a few options:

- Start coding manually
- Start coding, then use TAB autocompletes
- Use a prompt to generate some starting code

Here's our first important tip that I want you to internalize: **Always develop incrementally**.

AI tools can generate a *huge* amount of code very quickly.

- It's unwise to create more code in one step that you can realistically assess and evaluate
- The more code you try to generate, the more the model has to try to infer relevant details

Therefore, we should always think:

- What's the next step?
- What do I need to clarify or understand better before I move forward with creating more code?
- How will I know if any generated code is valid?

### Aside

In reality, we could probably one-shot a basic URL shortener. It's not *that* complicated. But I want you to practice thinking step-by-step, questioning yourself, and developing incrementally, even if it's not strictly necessary yet.

## Structure

Let's start by generating a simple Flask app. Once we verify that works, we'll work on shaping it into the complete URL shortener.

Click in the editor pane, then press CTRL + k (COMMAND + k on Mac) to open the chat interface. Type the following prompt:

>Generate a basic Flask app with a default route. When the user requests the default page, return an index.html file.

Press ENTER to submit. You'll get back code similar to this:
```
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

Briefly:

- `@app.route` defines a function associated with a particular URL. When the server receives a request for that URL, it runs the associated function code.

- In this case, `/` is the default route for the server's homepage. When a browser requests the default homepage, the server runs the `home` function, which returns `index.html`.

- In general, web applications work by defining functions that are mapped to different URL routes. For anything that we want the server to do, we'll assign a URL path to that action, the write the associated function, which might call other functions.

### Install Flask

Install Python packages with `pip`, the Package Installer for Python:
```
pip install flask
```

### Making the index page

By default, the base page for a website is called `index.html`. Let's create one to use for testing.

First, create a `templates` directory: Flask requires that static HTML pages be placed in a specific directory.
```
mkdir templates

touch templates/index.html

code templates/index.html
```

Use the same prompting technique to generate a basic index page.

> Generate a basic index page that I can use for testing.

Note that the AI might give you some code based on the URL shortener concept. That's okay for now, but we need to be very careful about assuming that any code we get from this prompt is going to be relevant to the final version of the app. We haven't thought about the interface between the frontend and server yet.


### Test

This is just a basic hello app, but we should go ahead and test what we have and make sure that we can at least serve the page.

**Big tip**: You have to save your code in Cursor for your changes to take effect. It doesn't automatically saved your changes when you run the program from the terminal!

Run the app in the terminal by typing:
```
python3 url_shortener.py
```
You should see text appearing telling you that the server is now running.

Open a browser tab and go to [http://127.0.0.1:5000/](http://127.0.0.1:5000). You will see the example index page.

**Use CTRL+c in the terminal to stop running the server**.


## Interfacing

Confession: When I first worked on this project, I got myself in trouble. Why? **I generated the front and back ends of the application without thinking carefully about how they were going to communicate**.

The result was an application in two parts that had different ideas about how to exchange data, so I had to do a lot of tedious rewriting to bring them into alignment.

Therefore, here's a key tip that you'll need to keep in mind all the time: **Think about your interfaces**!

To begin, go to your favorite chat (Claude, ChatGPT, etc.) and ask it to give you some tips on designing the communication between the front and back ends of the URL shortener app:

> I  want to build a URL shortening application. Give me some suggestions for handling the interface between the frontend and server. I'm using Python Flask for the server. You don't need to write any code yet, just give me concrete suggestions for how to structure an effective interface between the two parts of the application.

Remember that checking with an AI is basically what the Dungeons and Dragons folks would call a **free action**. It costs almost nothing to throw any nontrivial question into the chat to see what suggestions it has.

Read the response. To summarize, your basic strategy for communicating between the front and back ends of the site is to call a URL on the server that accepts data using the HTTP POST method. The data for the request will typically be encoded using JavaScript Object Notation (JSON), which is the standard way of passing data between the parts of a web application.

### Get a Prompt

It's also helpful to ask for help generating prompts.

> Generate a prompt that I can use in my AI-supported IDE to produce the server code. I only want the prompt. I want to follow your guidelines of creating a /api/shorten endpoint that accepts and returns JSON.

I got the following response:

> Create a Python Flask API endpoint at /api/shorten that accepts POST requests with JSON containing a "long_url" field. The endpoint should validate the URL format, generate a unique short ID using a combination of lowercase letters and numbers (6 characters), store the mapping between the short ID and original URL, and return a JSON response with fields for "short_url" (including the domain), "original_url", and "created_at" in ISO format. Include proper error handling for invalid URLs (400) and rate limiting (429). Use appropriate type hints and docstrings. The code should follow REST best practices and include logging. Return HTTP 201 for successful creation. Store the URLs in-memory for now using a dictionary. Include the main Flask app configuration with CORS enabled.

### Warning

**Look at the prompt**. AIs like to generate full-featured, complex code. Often, this will be more than what you want, at least for the initial stages of the app.

Here, for example, we're looking at using Cross-Object Resource Sharing (CORS), rate limiting, and returning some information on the creation time of the short URL. Do we need all those features right away? Maybe not!

I always recommend **developing incrementally**. If a feature seems more complex that what you need right now, seek clarification and decide if it can be ommitted until you really need it.

This is the advantage of small generations: You want to keep the magnitude of each change at a scale that you can understand and meaningfully evaluate.


### Server Implementation

Go back to the `url_shortener.py` file. Use the chat feature to implement this prompt.

Inspect the code that you get as a result. Make sure that it seems reasonable and you have a reasonable understanding of what each step does. You can get explanations for any lines by highlighting them, then using the chat feature to create a prompt.

### Generating the front-end

Go back to the front-end page. I suggest removing the code that's there so you can generate a fresh page.

Construct a prompt that will produce a page for the URL shortener.

- You can get suggestions from your other chat if you want.

- Another tip: when you're constructing the prompt you can use `@url_shortener.py` to include the server's code in the prompt. That's an easy way to provide more context to the generation.

- Make sure that the generated front-end code uses the same parameter names as the server-side code: `long_url`, `short_url`, etc.

## Test

**Save both files**, then re-run the flask app, reload the page, and try submitting a URL. Hopefully it will work.

If it doesn't, experiment with debugging using the AI interface. Open up a chat on the right side and paste any error message or bad behavior you get and ask for explanations and suggestions.

## Fetching

If you have time, try one more round of development to add a route `GET /{short_id}` that will match any generated shortened URL and perform a redirection to the corresponding real page saved in the dictionary of mappings.

Use the same strategy of prompting a general AI for suggestions, then prompting the server code to add the new feature.

Once you have this implemented, you have a general URL shortener app. To make it better, the next step would be to upgrade to a real backend database to store the mappings instead of a temporary in-memory dictionary.

## Lessons Learned

Developing with AI is powerful, but surprisingly tricky.

- TAB-based development is dangerous. Use it for true autocomplete, where you're generating something you would type anyway, but not for design decisions.

- Develop incrementally. Be carefuly about generating more code that you can meaningfully understand and assess in one step. Later, automated testing frameworks will help maange this problem.

- Think about interfaces. AI may be able to generate the internal parts of an application, but you need to make sure different components agree on how data is going to be exchanged and functions are going to be called.

- AI likes to generate complex code, maybe more complex than you really need at the current stage. Review your prompts and generations and simplify them if necessary.
