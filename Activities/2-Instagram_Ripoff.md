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

>I want to build a demo photo blog app. I know that I want to use vanilla HTML and JS for the front-end, Python flask for the backend, and an SQLite database.
>
>I'm thinking about something like Instagram, where photos appear in a grid with a caption and date for each title.
>
>This is primarily a demo, so I don't want to worry about managing log-ins, etc. for multiple users, so let's assume that there will be one user. I will be the only adminstrator.
>
>Act as my coach and walk me through a discussion to build a functional specification for this application. You can assume that I'm the user, so I'm able to answer all questions about what the app should or shouldn't do.

Have a discussion with the chat coach, keeping in mind the project scope above. Your goal is to move to a description of the important features of the app and an understanding how the user will interact with it.

### Stopping point

It's hard to give exact guidance about what you should produce, since it depends on the specific conversation you have with the chat partner. Here's an example of what I had after chatting with Claude.

```
Core Functionality

Public Photo Grid (index.html)

Display Requirements:

  Responsive grid layout showing 12 photos initially

  Each photo display includes:
    - The image itself
    - Caption below the image
    - Upload date in a human-readable format

  Photos ordered newest to oldest

  Infinite scroll: Load next 12 photos when user reaches bottom of page

  Simple, clean design with focus on the images


Admin Interface (admin.html)

Upload Form:

  File upload field that accepts only PNG, GIF, JPG, and JPEG formats
  Caption text field
  Upload date automatically captured on submission
  Preview of selected image before upload
  Clear success/error messages after upload attempt
```

```
Backend API Specification

GET /api/photos

Parameters:

page: integer (default=1)
per_page: integer (fixed at 12)


Returns JSON:
jsonCopy{
  "photos": [
    {
      "id": "unique_id",
      "url": "path_to_photo",
      "caption": "user provided caption",
      "upload_date": "ISO timestamp",
    }
  ],
  "has_more": boolean
}



POST /api/photos

Request: multipart/form-data

photo: file (PNG, GIF, JPG, or JPEG only)
caption: string


Returns JSON:
jsonCopy{
  "success": boolean,
  "message": "success/error message",
  "photo": {
    "id": "unique_id",
    "url": "path_to_photo",
    "caption": "user provided caption",
    "upload_date": "ISO timestamp"
  }
}


Data Storage

Photos stored in filesystem under static/photos directory

Metadata stored in SQLite database with schema:
sqlCopyCREATE TABLE photos (
  id TEXT PRIMARY KEY,
  filename TEXT NOT NULL,
  caption TEXT,
  upload_date TIMESTAMP NOT NULL
)
```

Notice that my application defines two routes:

- `GET /api/photos` to retrieve the list of all photos currently in the database
- `POST /api/photos` to upload a new photo

Recall that `GET` is typically used to fetch information from the server and `POST` is typically used when uploading something that will be stored server-side. This solution uses the same URL endpoint but controls its behavior with the HTTP method.

### DB

This application also uses a database that stores information about each photo. The schema contains:

- A unique identifier constructed at upload time
- The filename
- Caption text
- Upload date

We're going to use SQLite via its Python library to create and query the database. SQLite is one of the most popular lightweight database modules, so it's a good choice for a project like this one that doesn't need a complex setup or high-performance access to large amounts of data.

## Design

Once you have a general sense of the application, continue with the design.

I recommend starting by having a conversation about the frontend or backend to sketch out the countours of the solution before you generate any code.

Think about the complexity of your application. I did this project twice: the first version split the app functionality across several files and subdirectories, which turned out to be hard to reason about. I kept the second version more focused and it had only a main `app.py` file and a small `config.py` that defined some of the parameters.

Also be aware that the AI might want to generate more complex features that you don't really need yet. For example, you don't need to implement any logins for the admin page in the first version.

I recommend keeping your HTML files to individual `index.html` and `admin.html` that contain their own CSS and JS. You don't need to break out separate style and script files at this point.





