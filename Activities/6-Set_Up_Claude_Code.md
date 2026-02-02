# Set up Claude Code

<img src="https://substackcdn.com/image/fetch/$s_!PAxG!,w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fa137509b-3774-4b96-8727-66f4cf7ae376_1920x1080.png" width="600px" />

*Retro-futurism is when the AI runs in the terminal. Via [The Discourse](https://thediscourse.co/p/claude-code).*


## Instructions

I'll lead you through these steps in class.

1. Open your Codespace

2. Copy following command into your terminal and press ENTER to install the Claude Code application:
```
curl -fsSL https://claude.ai/install.sh | bash
```

3. Type `claude` in the terminal to start the program

4. It will ask you a few questions about your preferred display style. You can use the up and down arrow keys to select the style you want, or just press ENTER to accept the defaults.

5. You will have to authenticate your account. When it pops up the list of authentication options, choose option #1 to connect your Claude subscription account.
  
6. This will pop up a box asking if you want to load the Anthropic website in a new tab. Select ***Cancel*** to close the box. Because of how Codespaces works, you can't load the required site directly from it.

7. Claude will print a long link in the terminal window. *Copy it* and paste it into tab on your browser. That page will load and prompt you to log in to your Anthropic account.

8. After you authorize Claude Code, you'll get a long key string. Copy it, then paste it back into the browser window and press ENTER.
  
9. Finish answering any setup questions. The defaults should be fine.

At the end, you should see a prompt in your terminal waiting for you to input a command for the agent.

## Terminal commands

First, notice that you're in *the Claude Code application*, not the regular terminal.

Let's get into a folder where we can work on this activity. I recommend *exiting Claude Code* to run your terminal commands. **Press CTRL+c *twice* to exit Claude Code**. You're now back in the regular terminal.

Start by making a directory for this unit by running `mkdir`:
```
mkdir 2-Claude_Code_Intro
```
Then `cd` into it, again using the `!`:
```
cd 2-Claude_Code_Intro
```

You can now re-start Claude Code by typing `claude` in the terminal.

## Generate a program

Let's start by creating a simple conversion program. Put the following prompt into the Claude Code prompt:
> Generate a simple Python program that prompts the user to enter a number of pounds and calculates the corresponding number of kilograms. Print the           
  result to two decimal places. Include descriptive comments to help me understand the code.

Claude will think for a second, then pop up a window showing you the code it wants to write. The standard code editing view shows the existing code in the left pane - we're creating a new file, so this is currently empty. The right pane shows the new code.

The terminal pops up some options for you to accept this change. Notice that you have the option to default accept all changes Claude decides to make during this session. This option is useful for longer generations, but can be risky since you're giving the model the freedom to make changes without you checking each one. For now, choose option (1) to approve this change.

A good rule of thumb is to *read the code* and see if it looks reasonable. In this case, it's pretty to easy to understand what the program does: it prompts the user to input a value, does a calculation, then prints the result. That seems fine. For right now, you don't need to understand the exact syntax of each line, but **you should have a general sense of what the program is trying to do before you accept it**. If the code looks too complicated, or seems to be doing something different from what you want, you should reject the suggestion and reprompt with more specific instructions.

### Run the program

You can ask Claude to run the program for you by typing
> python pounds_to_kg.py
Or just tell it to run the program:
> run the program

This will prompt Claude to test the program for you. It will prompt you to accept an example input value (probably 10), then run the program and check the output.

Notice that this is running the program *within Claude*. This is kind of cool if you need to test a complex program. However, you probably want to test the program yourself without burning inference tokens. Press CTRL+c twice to exit Claude, then test the program several times by running it yourself:
```
python3 pounds_to_kg.py
```

Once you're satisfied that the code is good, re-start the `claude` command.

### Explanation

Prompt Claude to tell you how the program works:
> Explain how the program works.

It will print an explanation of each step of the program. **Look at the code** while you read the explanation and verify that it makes sense. If anything is unclear, prompt for additional information. For example,
> What does float mean?

## Basic work flow for a new session

1. Open your Codespace.

2. `cd` into the directory where you want to work.

3. Run `claude` in the terminal to start Claude Code.

4. Prompt Claude to generate some code. Later, we'll talk about other strategies for driving the generation process, but for now all of our programs can be generated by simple prompts. Make sure to specify the inputs and outputs. Tell Claude to include descriptive comments for each line to help you understand what the code is doing.

5. Claude will prompt you to accept changes it makes. *Look at each one* and verify that it seems reasonable and is in line with what you want. If it seems like Claude is doing something different from what you want, reject the changes and reprompt.

6. Run the program. If you only need to run it once, you can prompt Claude to run it for you. If you need to test it multiple times with different inputs, I recommend exiting Claude, testing the program, then re-starting `claude`.

7. Prompt Claude to explain the program to you and read its explanation while you look at the code. You'll be tempted to skip this step, but it's important for helping you learn. Don't be lazy!

## Practice problems

### McChocolate Potatoes

<img src="https://cdn.vox-cdn.com/thumbor/WMJG04bu5nCmDiQ5mh0_chXelTY=/247x0:787x405/1820x1213/filters:focal(247x0:787x405):format(webp)/cdn.vox-cdn.com/uploads/chorus_image/image/48592139/McDonald_s_Chocolate_Fries.0.0.jpg" width="300px" />

I'm a sucker for regional fast food items. It turns out that you ~can~ could get **chocolate fries** at [McDonald's in Japan](https://www.eater.com/2016/1/19/10790586/mcdonalds-chocolate-fries-japan) (they are officially known as "McChocolate Potatoes"). Are they any good? Maybe not, but they cost only 330 yen as a side item.

Generate a program that can read in a number of Japanese yen and print the corresponding number of patriotic American dollars. 1 JPY is currently worth about .0064 USD.

Tips:

- Include the conversion factor as information in your prompt, so Claude doesn't try to look it up from the Internet
- When it's time to test the program, exit Claude, run it to check the results, then re-start Claude
- Follow the guidelines above of looking at the code before you accept any changes; also prompt for a walk-through of the code


### Beard-seconds

<img src="https://upload.wikimedia.org/wikipedia/commons/8/81/Hans_Langseth.jpg" width="300px" />

The beard-second is an incredibly scientific unit of length defined as the distance an average beard grows in 1 second. Google defines the beard-second as 5 nanometers and will perform conversions between beard-seconds and other lengths (try typing “1 foot in beard-seconds” into Google). Using this definition, it would take an average beard 58.8 days to grow 1 inch.

The longest beard in the world is 17 feet long and is housed in the Smithsonian institution. In life, it belonged to Hans Langseth, who immigrated to the U.S. from Norway in 1864; he died in North Dakota in 1927. He would wrap his beard around a corncob and carry it in his pocket.

Generate and test a program to read a number of inches as input and convert it to units of beard-seconds. Print the result to two decimal places.

### Fake Internet Meme Money

<img src="https://external-preview.redd.it/3_iVT6i7dReTdMXS-bNiIS0U9p2QTsfq6BUDC57b8tc.jpg?auto=webp&s=5943d7cf04be56a4de8cf045667e41631c02a90e" width="35%" />

Dogecoins, the favored cryptocurrency of shiba inus everywhere, currently trades for about .10 USD per DOGE.

Write a program that reads a number of DOGE as input, then prints the corresponding amount of USD to two decimal places. Again, test your program and prompt for a walk-through of the code. 

### Fibonacci

Recall the famous Fibonacci sequence, where each number is the sum of the two previous numbers: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34,...

Prompt Claude to create a program that calculates and prints the first 25 Fibonacci numbers. Tell it to include descriptive comments explaining what each part does. After the program generates, run it, and verify that the output is reasonable, then get a walk-through of the steps.

### Guessing game

Prompt Claude to write a simple number guessing game. It should ask the user to guess a number between 1 and 1000 with a maximum of 10 tries. It should give hints if the user guesses too high or too low.

### Magic 8-Ball

Prompt Claude to create a program like a Magic 8-Ball that asks the user to enter a question, then prints out a randomly-selected answer from one of seven options.

Once you have the program generated, open up the code and look at the file. Experiment with editing the output messages **by hand** and re-running the program to observe that changes that you've made.
