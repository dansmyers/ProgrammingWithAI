# Practice Code Generation

<img src="https://media.pitchfork.com/photos/5c37770817eefc510f1b3565/16:9/w_1280,c_limit/David-Bowie.jpg" width="500px" />

*David Bowie using a computer, ca. 1994*

## Overview

This activity will let you practice the basic rhythm of prompting an AI to generate some code, then running it in our Codespaces environment.

## BTC to USD

Write a program that can read a number of bitcoins from the user and output the corresponding number of US dollars. Use $94,416.44 per 1 BTC as the conversion rate.

To start, open up a new session in Claude. Try the following prompt:
> Generate a Python program that reads a number of bitcoins from the user and calculates the corresponding number of US dollars. Use $95,416.44 per 1 BTC as the conversion rate.

Claude will consider your request and produce a .py file. Once you have the result, copy it using the button in the upper-right corner of the display window. There may be some things in the code that you don't understand yet. That's okay for now.

Go to Codespaces and create a new file by typing in the terminal:
```
touch btc_to_usd.py
```
The `.py` extension is normal for Python scripts. Open the file by clicking on it in the left hand file browser window, or by typing
```
code btc_to_usd.py
```
in the terminal.

Copy your solution into the file. Then run the program using
```
python3 btc_to_usd.py
```

### Testing
Back in the Cold War era, they had a saying about U.S.-Soviet relations: *Trust, but verify*. You need to adopt the same attitude towards AI-generated code: It may appear reasonable, *but you have to actually test it* to make sure the program works.

Let's think about some useful test cases:

- If we input 1 BTC, we should get $95,416.44 as the output
- If we input 2, 10, 100, etc. BTC we should get multiples of the conversion rate
- If we input 0, we should get 0 as the output

Test a few different inputs and verify that the output seems reasonable.

What about error cases?

- What happens if you enter words instead of a number, like `twenty` instead of 20?
- What happens if you enter `1 BTC`?
- What happens if you enter a negative number? Is this an error?

Error cases aren't necessarily a problem, as long as we understand what kinds of inputs cause errors and agree on how they should be handled.

### Explanations

It's easy to check if the program works, but it's a bit of a black box. Look at the code and see if you can make out the general flow of program statements as they execute:

- You'll have a function named `main`; this is the main logic for the program
- There is an `input` statement and `print` statement
- You'll also see a calculation for the result

But the specific syntax of these statements may be difficult to understand.

Here's a major tip: ***You can ask the AI to help you understand the code***. This should be your #1 priority when working with a new program. You don't have to understand the individual details of the statements, but you *absolutely do* need to understand the choices the AI made so you can determine if they match your goals.

Go back to your Claude window and ask it to update the program (in the same chat window):
> Add comments explaining each line to help me understand what the program does.

Look at the result. Are there still things that are unclear? If so, prompt the AI to explain them. For example,
> Tell me more about the `float` function. Why is that required?

## Kilos

One kilogram is equal to 2.20462 pounds.

Use Claude to generate a program that reads a number of pounds from the terminal and outputs the corresponding number of kilograms. Use the previous example as a model. Add descriptive comments so you can understand what the program does. Then test your program on a number of error cases to see how it behaves.

The largest cocaine bust in American history occurred in [2019 at the Philadelphia Packer Marine Terminal](https://en.wikipedia.org/wiki/2019_Philadelphia_Packer_Marine_Terminal_cocaine_seizure). Customs officials seized 39,525 pounds of cocaine with an estimated street value of more than $1.3 billion. Use your program to calculate the number of kilograms.

## Smoots

<img src="https://assets.mitmuseum.mit.edu/iiifimg3/66927613/full/800,/0/default.jpg" width="300px" />

Oliver R. Smoot is an MIT graduate and former head of the American National Standards Institute (ANSI) and the International Organization for Standards (ISO).

In 1958, as part of his initiation into ΛXA, Smoot and his brothers measured the entire length of Harvard Bridge over the Charles River in Cambridge, MA, using Smoot’s body as the ruler. He was at the time 170 cm tall (5 feet, 7 inches), and the bridge was declared to be 364.4 Smoots, "plus or minus one ear" (about 2035 feet or 650.7 meters). Since that time, the measurement of Harvard Bridge has always been denominated in Smoots, with the markings repainted each year by the incoming ΛXA pledge class at MIT. The Cambridge police use the Smoot markings to identify the location of accidents on the bridge.

Generate a conversion program for Smoots.

