# Setup Claude Code

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

You can run Claude Code at any time in the terminal by typing `claude`. Let's practice writing some simple programs.

First, notice that you're in *the Claude Code application*, not the regular terminal. You can run your normal terminal commands by typing an exclamation point inside Claude.make a new directory for this unit:
```
mkdir 2-Claude_Code_Intro
```
Then `cd` into it
```
cd 2-Claude_Code_Intro
```





