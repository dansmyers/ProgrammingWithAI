# Games

## Overview

This activity will practice using Claude Code to generate some simple single player games. Tips:

- Practice writing a good prompt. Think about what details you need to specify to get the behavior that you need from the game.

- Practice exiting Claude to test each program, then restarting Claude to make changes. Think about test cases for each program.


## Setup

`cd` into your `2-Claude_Code_Intro` directory:
```
cd 2-Claude_Code_Intro
```
Then start Claude:
```
claude
```

## The subtraction game

Here's a simple math game. There is a pile of 21 stones. On her turn, a player may take either 1, 2 or 3 stones. The player who takes the last stone *wins*. It was played as a challenge on *Survivor: Thailand* where they called in "Thai 21".

Prompt Claude to create a program to play the subtraction game against the computer. Describe the set up, legal moves, and winning condition. Remember to ask to include descriptive comments and take a look at the code before you accept it.

### Test

Once Claude generates the code, exit by pressing CTRL+c twice. Then run your program using:
```
python3 subtraction_game.py
```
**Your program might have a different file name**.

Play a few rounds and verify that the basic behavior is good. Then try testing it more aggressively:

- What happens if you enter a number that's not 1, 2 or 3?
- What if you try to remove more stones than remain?
- What if you enter a non-numeric input, like `two` instead of `2`?

If you find errors, re-run Claude by typing
```
claude
```
Then ask it to update `subtraction_game.py` to fix whatever problems you identified.

### Misère

Prompt Claude to change the program so that the player who takes the last stone *loses*. A game with this property is called a *misère* game. Again, test the program once it generates

## Fifteen

<img src="https://preview.redd.it/gustave-dor%C3%A9-the-night-mare-life-in-death-plays-dice-with-v0-mjuyk0eqiwkb1.jpg?auto=webp&s=3f727b48c0a49bff7cd70a01cb41160a5ccbfc4a" width="200px" />

*The Night-Mare Life-in-Death Plays Dice with Death for the Souls of the Crew*, woodcut by Gustave Doré for an edition of Samuel Taylor Coleridge's *Rime of the Ancient Mariner* (1875). [Linked from r/museum](https://www.reddit.com/r/museum/comments/163va3r/gustave_dor%C3%A9_the_nightmare_lifeindeath_plays_dice/).

**Fifteen** is a basic dice game, one of a family of accumulating games that involve rolling dice to get as close as possible to a target without going over.

Our version will use the following rules:

- Roll three six-sided dice and add their sum
- If the sum is equal to 15, the player wins immediately
- If the sum is greater than 15, the player loses immediately
- If the sum is less than 15 the player may choose to roll one more die and add it to the score
- Announce the player's score
- Print a message depending on whether the score was less than, equal to, or greater than 15

Prompt Claude to implement the Fifteen game to play against the computer. Again, make sure you describe the rules of the game in enough detail. Then test your implementation.


## Pick your own game

If you finish both of the previous problems, use Claude to implement a game of your choice. Think about what features you want it to have and how you want it to play, then describe those things in the prompt.
