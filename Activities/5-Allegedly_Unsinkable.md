# Allegedly Unsinkable

<img src="https://theonion.com/wp-content/uploads/2004/04/4deeab6c8613d651a6d9267ff31858dd.jpg?w=1024" width="400px" />

Front page of *The Onion*, April 16, 1912

## Overview

In the early hours of April 15, 1912, the "unsinkable" ship *RMS Titanic* sank when it struck an iceberg, killing more than half of the passengers and crew aboard. The `Titanic.csv` dataset contains demographic information for 889 of those passengers as well as a record of whether or not each passenger survived. 

The *Titanic* dataset is the `Hello, World` of data analytics. We'll continue the chain of tradition by practicing some more analysis using it.

The main goal of this activity is to practice the basic workflow one more time:

- Starting Codespaces
- Downloading a dataset and putting it into Codespaces
- Chatting with Claude about the question
- Clarifying the design
- Generating code
- Running the code in Codespaces to produce a plot


## Setup

Open your Codespace.

If you don't have a `1-Generation` directory, start by creating one. In the terminal, type:
```
mkdir 1-Generation
```
Recall that creating a subdirectory for each project or major unit of the course is a good way to keep things organized.

You can the change to working in the directory:
```
cd 1-Generation
```
You should see the terminal prompt change to indicate that you're now working in the directory.

Next, install the required data analytics libraries. You may have already done this for the previous projects. First install Pandas, the Python data analytics framework,
```
pip install pandas
```
**If you get a popup about virtual environments**, choose "Don't show this again" to close it. We don't need to worry about those in this class.  Then install `matplotlib` for plotting:
```
pip install matplotlib
```

## Data

The dataset is posted to Canvas as `Titanic.csv`. Download it from there, then move it from your Downloads folder into the `1-Generation` directory on Codespaces.

Once you have it in the correct folder, open the CSV file and take a look. The top row lists the fields. Observe that the dataset lists the class of each passenger as `Pclass`, which is 1, 2 or 3; sex as `Sex`, which is 'male' or 'female'; and `Survived`, which is 0 or 1.

## Question

Let's make a graph that will illustrate the difference in survival rates as a function of both passenger class and sex.

- Upload the `Titanic.csv` dataset to your Claude chat

- Then craft a prompt asking Claude to help you write code to analyze the impact of passenger class and sex on survival rate. You want the output to be a graph in PNG format.

- Tell Claude that it doesn't need to do the analysis or write any code right away, just help you understand the problem.

Work on crafting your own prompt, then answering the questions that Claude asks, then have it generate the Python code.

## Run

Copy the Python script from Claude.

In your terminal, create a new file:
```
touch survival.py
```
Then copy your program from Claude into the Python file.

Run the program:
```
python3 survival.py
```
Check the output graph. Does it look good? Does it seem reasonable? Prompt for any changes that you need.


## Do your own analysis

Now, think about some other question you'd like to ask about the *Titanic* data. Look at the fields of the CSV file for some ideas about what you might be able to analyze. Create a prompt to address that question, then generate a program and run it.

Use the `touch` command to make a new file in your Codespace, then have another chat with Claude to develop code to put into the new file. Again, save your output as a PNG image.
