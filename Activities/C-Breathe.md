# Breathe

## Overview

Let's practice using the specs-driven development approach we discussed in class to make a web-based breathwork app.

- The app will run as a single front-end web page using HTML, CSS, and JavaScript
- It will have some controls to allow the user to select a breathing pattern and a visual and timer to help count each step

## Build the spec

The first step is to chat about the project with Claude to build a specifications document. Go to the regular Claude chat - I find it better for this step than using the terminal app. Prompt:
> I want to create a breathwork app. It should run as a single front-end web page. I want to be able to select a breathing pattern and have a visual and a counter that helps with the counting of each step. Please chat with me and help me produce a specification in Markdown format for this project that I can give to me AI coding agent. You don't need to write any code, just help me produce the spec.

After this, Claude will ask you some questions. Chat about them. The key to this step is **having opinions and ideas** that can drive the specification. If you don't understand a questions, ask Claude to explain it to you. This is a great learning tool.

After you've worked through the discussion, ask Claude to output a spec document in Markdown format. Markdown is a way of representing structured documents in plain text. It's a preferred way of giving information to models because it's easy for them to understand, compared to more complex formats like PDFs and Word docs.

## Read the spec

Take a moment to actually read through the spec document. Double-check the choices it contains. If you have any questions, you can ask about them (again, this is a great way to learn about design). If you find something you want to change, just ask Claude to update the document.

## Get the plan

Go to your Codespaces workspace. Start by `cd`ing into your `4-Web` directory:
```
cd 4-Web
```
Then make a new file for the spec document:
```
touch breathwork_spec.md
```
Open that file, then copy the output from the chat into it.

Next, start `claude`. Then enter planning mode by typing `/plan` at the prompt.

Ask Claude to read `breathwork_spec.md` and develop a phased implementation plan to build the app.
> Read the specifcation given in breathwork_spec.md and develop a phased implementation plan to build the project it describes.

Work through the plan, then give Claude the go-ahead to build the app.

## Test and iterate

Once the build is complete, Claude can run the app for you. Try it out. Does it do what you want? How does it look and feel?

Identify a few changes you want to make. Even if you like the app as it is, think of something that could be changed. Then, **update the spec** to describe the change you want. This is important - the spec is the ground truth for the app, so you want to always make sure changes are reflected in it. If the project gets out of synch with the spec, the model has no reference to use to guide its code generation.

You can do the update by prompting Claude to change the spec, or by editing it yourself.

Then, prompt Claude to rebuild the app using the updated specification document. This step illustrates a key idea for working with agents: **code is cheap**. The overhead of generating something multiple times is low, so it's often more efficient to update the spec and rebuild the project, rather than trying to make changes to the already-existing code.

## More specs

Once you've finished that project, play around with designing and implementing another web-based application of your choice. For example, you could make a simple game like tic-tac-toe or Wordle. Use the same approach of chatting about the project to build the spec document, then using `/plan` mode in the terminal to get a phased implementation that Claude can build.
