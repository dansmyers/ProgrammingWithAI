# Instagram Ripoff

> "Good artists copy, great artists steal."
>
> Dan S. Myers

## Overview


In this activity, you're going to build an Instagram-style photo blog. Your page will display a collection of uploaded photos in a grid, with a title and date for each one. You'll also create a basic admin page where the site owner (you) can upload new photos.

This project will allow us to practice the web programming techniques we've talked about this week, plus the additional feature of a backend database to store metainformation about the photos. It will also allow you to practice creating a **functional specification**, working with an AI coach to plan out how the application should work from the user's perspective before you begin coding.


## Scope

The overall goal of the project is to build an Instagram-style photoblog. We'll keep things deliberately simple for now:

- There's going to be one `index.html` page that displays the uploaded photos to the user.

- There will be an `admin.html` page with a form to upload new images.

- We won't use any security or login features for now. This wouldn't be acceptable for a real app, but it's fine for an in-class demo project.

- Use vanilla HTML, CSS and JS for the frontend, Python Flask for the backend, and SQLite for the database.


## Functional Specs

The **functional specification** is a document that describes what the software should do *from the user's perspective*. What operations does it support? What are the intended workflows or processes? What is the look and feel?

Creating a functional spec typically precedes creating a detailed design document that actually specifies the internal architectural details of the software, like the choice of languages, frameworks, API endpoints, data formats, and so forth.

Start with your favorite chat application and ask it to help you develop a function spec for this project:

>I want to build a demo photo blog app. I know that I want to use vanilla HTML and JS for the front-end, Python flask for the backend, and an SQLite database.*
>
>I'm thinking about something like Instagram, where photos appear in a grid with a caption and date for each title.
>
>This is primarily a demo, so I don't want to worry about managing log-ins, etc. for multiple users, so let's assume that there will be one user. I will be the only adminstrator.
>
>Act as my coach and walk me through a discussion to build a functional specification for this application. You can assume that I'm the user, so I'm able to answer all questions about what the app should or shouldn't do.
