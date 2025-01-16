# URL Shortener

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
- Think about the structure of the application a bit before we begin generating
- Practice generating code with Cursor
- Practice explaining unfamiliar code and getting answers to questions

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

Open a browser tab and go to [http://localhost:5000/]. You will see the example index page.


## Interfacing

