# Zipf's Law and *The Whale*

<img src="http://www.harkavagrant.com/history/moby.png" width="400px" />

Kate Beaton, *Hark! A Vagrant* [66](http://www.harkavagrant.com/index.php?id=66)

## Overview

Zipf’s Law is a result from linguistics that describes the distribution of word frequencies in many texts. It states that the Nth most frequent word occurs about 1/N times as often as the most frequent. That is, the second most frequent word occurs about 1/2 as often as the most frequent word, the third most frequent about 1/3 as often, and so forth. The law is named for George Zipf, who first described it based on empirical observations in the 1930s.

Let’s vibe out a program that can analyze a text — we're going to use *Moby Dick*, of course — and make a plot demonstrating if it follows Zipf’s Law. 

## Data

I've posted the text of *Moby Dick* to Canvas, or [you can download it](https://www.gutenberg.org/ebooks/2701) from Project Gutenberg in plain text format.

Once you have the data, drag it from your computer's Downloads folder into the `1-Generation` directory on Codespaces.

## Start by chatting

We might be able to get a usable solution by just asking directly for “a program that can analyze a text and see if obeys Zipf’s Law”, or something similar. It’s a better idea, though, to start by having a conversation about the requirements, which will give you an opportunity to clarify what the program needs to do.

Go to Claude and try the following prompt:

> I would like to write a Python program that can count the frequencies of words in a text file and plot them to examine if the text obeys Zipf's Law. I want the output to be a plot saved as a PNG file. Act as my co-programmer and discuss this program with me. Help the clarify requirements and understand the overall design. Assume that I have very little programming experience. Don't generate any code yourself yet, just help me create a plan for this project.

Don’t worry about making the best possible prompt! Modern models don’t need tricky prompt engineering. Instead, just start with your work in progress and have a conversation about what to do next.

Claude comes back with a few clarifying questions:

> - What kind of text files are you planning to analyze? (novels, articles, social media posts, etc.)
> - Do you want to analyze just one file at a time, or compare multiple files?
> - What should the program output - just a plot, or also save the word frequency data?

And some questions for what the program should do:

>- How should we handle punctuation and capitalization? (e.g., should "The" and "the" be counted as the same word?)
>- Should we exclude common words like "the", "and", "of"? (called "stop words")
>- What scale should we use for the plot? (Zipf's Law often shows up best on a log-log plot)

This is exactly what we wanted! AIs are generally good at providing this sort of clarifying feedback. **Always start your program by having a chat about the goals and requirements before you jump into generating code**.

I went back in and answered Claude’s questions:

>I want to analyze the text of one novel. I'm currently using Moby Dick as my example. I don't need to analyze multiple files right now. I have the text in a .txt file. I would like to produce a plot showing the word frequency data and comparing it what would be expected by Zipf's Law. We should ignore capitalization and punctuation and treat all occurrences of the same word as identical.

Your output to the first step, and hence your response, might be slightly different from mine, but notice that we’re just having a conversation about what we want the code to do.

## Get the plan

Once you've answered the questions, Claude will produce a project specification. If it doesn't, ask for it directly:

> Generate a specifications document for this project in Markdown format.

Note: Markdown is a standard way of writing structured text files that can be formatted to appear on the web. GitHub uses Markdown for all of the documents that it stores, including this one. Markdown is also very friendly for AI models. Unless you have a good reason, ask models to generate their output in Markdown text rather than PDFs or other formats.

Once you have the plan document, review it to make sure that it looks reasonable.

## Generate

Now ask Claude to generate the code.

`cd` into your `1-Generation` directory, then make a new file:
```
touch zipf.py
```
Copy your solution from Claude into `zipf.py`.

Run the program using
```
python3 zipf.py
```
It may prompt you to install some required libraries. If so, use the `pip install` commnd. For example, if you need to install `matplotlib`, use
```
pip install matplotlib
```
This is a pretty normal part of the Python workfolw. "pip" is the *Package Installer for Python*; it has the ability to pull libraries that aren't installed on your system and install them so you can use the functions they contain. **If you get a popup about virtual environments, just close it. We don't need those right now**.

## Check the output

Your program should run and produce a PNG file as its output. Take a look at the image and see if it makes sense. Make sure that the output obeys some qualities of good graphing:

- Title
- Axis labels
- Lines distinguished by style with a legend to explain which line is which. Use line style (e.g., solid vs. dotted vs. dashed) when you have a small number of curves to distinguish rather than colors.

If you need to make any edits to the figure, prompt Claude to update the code, then re-copy and re-run the updated version until you get a good looking plot.

## Variations

If you have time, try prompting in a few changes to the code:

- Add an annotation on the plot to show where the word “whale” appears in the data
- Remove the most common English words (the, and, a, of, etc.) that tend to dominate the top of the distribution and re-run the analysis

