# Retrieval Augmented Generation: TutorBot

## Overview

This will be our third project, but we're going to mostly build it in class.

The goal: create a Retrieval Augmented Generation application that functions as a tutor for a text of your choice. Here, "text" refers to some written artifact that you can use as the basis for your generations.

Goals for phase 1:

- Select a text that you want to use as the basis for your project. It should be decently long, so that it's not reasonable to simply put the entire document into every prompt that you execute. This is a good opportunity to do some liberal arts and incorporate your non-programming interests.

- Come up with a starting question that you want the user to answer about the text.

- Get the text chunked and inserted into a Pinecone database using the setup strategy from the last lab.

- Develop the basic interactive query application with the starting question as the initial prompt. Again, use the last lab as a startintg point. You should pull the relevant information chunks from the database to go along with the prompt. Think about the prompt: you probably want to pass the question, the user's answer, and some instructions about how to respond.

- Design a system prompt that guides the interaction of the user with the application. Think about what an effective tutoring interaction would be like. Remember that it's okay to have the system prompt be long with detailed instructions (check out the [Claude system prompts](https://docs.anthropic.com/en/release-notes/system-prompts) for examples).

## Phase 2

Once you have the basic tutoring interaction working for one question, add a second question.

Here's the challenge: When is it okay to move to the second question? You want to set up an interaction that evaluates the user's response and decides if it's sufficient to move to the second question. Think about this as a state-based model:

- Read the user's response to question 1

- Do a check that evaluates the response to determine if it's correct enough to move on to question 2.

- If the answer isn't correct yet, send it to the model to generate the tutoring response
```
 ------------             -------------------------------     Yes     ------------
| Question 1 |---------->| Evaluate if answer is correct |---------->| Question 2 |
 ------------             -------------------------------             ------------
      ^                                  |
      |                                  | Not yet
      |                                  v
      |                     ----------------------------
       <-------------------| Generate tutoring response |
                            ----------------------------
```
You can then have a similar flow for Question 2. Check if it's correct, and if so, end the session. If not, generate a tutoring response.

Use a variable to keep track of where in the process you are.

