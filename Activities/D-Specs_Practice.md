# Practice with Specs-Driven Development

## Overview

Our goal for today is to practice the specs-driven development process we talked about last time. Briefly,

- Chat with the model (in the regular Claude chat) about what you want to build
- Produce a specs document in Markdown format describing the proejct
- Copy that into your workspace
- Ask Claude Code to read the document and produce a phased implementation plan
- Execute the plan
- Test the result
- Make revisions and updates to the spec as necessary

Work through the ideas below. Tell Claude to build each project as a **single front-end web page using HTML, CSS, and JavaScript**.

## Ideas

### Minesweeper

Build the classic Minesweeper game as a front-end web page. Think about what controls you should have for things like the size of the board and the density of mines.

### Stock visualizer

Return to the stock graphing that we did earlier. Build a web page that allows the user to input stock tickers, select a date range, and view a graph of the stock price over that time. Think about how you want to implement the range (free choice of interval, standard buttons like 1d/1m/3m/6m/1y?) and how you want to deal with viewing multiple tickers (create multiple plots? add multiple lines to each plot?).

### Nim

Nim is a classic mathematical strategy game, the extension of the 21 stone game we looked at earlier. There are *k* piles of stones, each containing *n* stones. On her turn, a player selects *one pile* and removes as many stones as she wants from it. The player who takes the last stone is the loser.

Write a visual Nim game as a single web page.

### Blackjack

Classic card game. Try writing three versions:

- The simple version where the player just plays against the dealer and wins, loses, or ties each hand
- A larger version where the player has a bankroll and bets on each hand
- An advanced version for practicing where the game will offer [strategic advice](https://wizardofodds.com/games/blackjack/strategy/calculator/) on what to do in each situation

Start by making the first version. Once you have that built, chat with Claude to update the specs:
> I want to update the blackjack project to add user betting and bankroll tracking. Discuss this with me, then update the specifications document.

Likewise, after you build the second version, update the specs again to incorporate strategic advice.
