# `Hey, GitHub!`

- [Interaction](#interaction)
   - [Modes](#modes)
   - [Command Categories](#command-categories)
   - [IDE Control](#ide-control)
   - [Code Generation/Editing](#code-generationediting)
- [Tips and Tricks](#tips-and-tricks)
- [Known Software Limitations](#known-software-limitations)


Imagine a distant future where keyboards and mice are off-limits to all things code. How would we code then?

Unfortunately, that distant future is *today* for a non-trivial number of our fellow developers. Be it due to an accident, or a condition such as Repetitive Stress Injury.

These developers still code by the ingenious use of assistive technologies like speech recognition. However, upon closer inspection, we found that these technologies leave much to be desired. In particular, when it comes to code dictation, the structurally unforgiving nature of code makes it difficult to express out loud.

Most of us are aware of the internet meme
```
Programming is like writing a book ... 
except if you miss a single comma on page 156 the whole thing makes no damn sense" 
- unknown
```

In particular, due to the interleaving of the symbols in code, contemporary code dictation solutions subject us developers to a awkward code/symbol dictation. And imagine if that awkwardness is removed; how productive we all will be as developers. That’s where `Hey, Github!` can help.

With Copilot, Github ushered in a new paradigm of software development. With the power of your voice, we’re excited to bring the same benefits of Copilot to even more developers. GitHub is renewing its vision to be the home for *ALL* developers, and this experiment is just one of many steps we’ll be taking to make that a reality.

<a href="#top">Back to top</a>
# Interaction

Hey, GitHub! provides voice-first UX to make copilot accessible to even more developers. 

The voice interaction underneath uses an embedded version of [Microsoft's embedded speech solution](https://azure.microsoft.com/en-us/products/cognitive-services/speech-to-text/#features). In particular, our solution leverages the Java SDK; thus, we need Java runtime as a system prerequisite. If you do not already have a Java runtime or JDK installed (at least Java 11), a place you can get one is [here](https://learn.microsoft.com/en-us/java/openjdk/download).

On Linux it also relies on the `play` command from the `sox` package for making notification sounds. For example you can use `apt install sox` on Ubuntu to get this if you don't already have it. If you don't have it, text to speech will still work, but you won't hear notifications.

Like contemporary voice assistants, our solution relies on a wake word to turn the speech- recognition on and off. So `Hey, GitHub!` is our keyword of choice.
`Hey, GitHub!` obviously, because “GitHub” is fantastic and, more importantly, to show our commitment to bringing voice control to all aspects of the GitHub product in the future.

The simplest way of getting started is to say, `Hey, GitHub!` followed by a command.
For example, we can say things like, "Hey, GitHub, toggle sidebar."

## Modes

We understand that using the hot word over and over again can get old pretty soon, especially when developers are in the zone for building software. So we made a special "active mode" just to avoid tongue fatigue.
In active mode, developers do not have to say, "Hey, GitHub!" to activate the speech-to-text service. The extension continuously listens and responds appropriately to the commands. To activate the active mode, developers can say, "Hey, GitHub, start active mode." To deactivate the active mode, developers can say, "stop active mode."

## Command Categories
The voice commands can be broadly categorized into two categories:

1. IDE Control
2. Code Generation/Editing


## IDE Control

These commands help with IDE interactions. Here are a few examples of these commands

1. "toggle sidebar" -> toggles the sidebar
2. "goto line 56" -> moves the cursor to line 56
3. "toggle zen mode" -> toggles zen mode
4. "run code" -> run code in terminal
5. "save" -> save the current file
6. "save all"  -> saves all open files
7. "undo" -> undo the last action
8. "redo" -> redo the last action
9. "clear console" -> clears the terminal
10. "zoom" -> zooms in
11. "zoom out" -> zooms out
12. "pause mic" -> pauses the listening
13. "goto end" -> moves the cursor to the end of the file
14. "go to the end of line number 28" -> takes cursor to the end of line 28 in the active editor window (if open)
15. "insert a new line at line number 12" -> takes cursor to line 12 and then adds a newline (within active editor window)
16. "select line 43" -> selects line 43
17. "select lines 5 to 10" -> selects lines 5 to 10 
18. "delete line 15" -> deletes line 15
19. "delete lines 4 to 16" -> deletes lines 4 to 16
20. "delete lines 10 to the end" -> deletes lines starting from 4 till the end of file
21. "go to next class" -> moves the cursor to the next class
22. "select previous function" -> selects the previous function
23. "select current symbol" -> selects the current symbol 
24. "select function `set Collection`" -> tries to find and select the function `setCollection`


We have over 300 uniquely identifiable commands in this category and we are constantly adding more.

## Code Generation/Editing

These commands help with writing code:

1. "write code to print the gcd of 2 numbers" -> generates a code suggestion. Try to be as specific as possible with what you want. 
2. "change the return type of the function to a boolean" -> edits the suggested code currently displayed in "ghost text"
3. "explain the code" -> explains a manually selected range of line(s), playing the response as an audio interaction
4. "explain lines 4 to 7" -> explains the range of lines specified

<a href="#top">Back to top</a>
# Tips and Tricks

We are chasing the dream of having a very natural and conversational experience with the `Hey, GitHub!` extension, but are still in the early stages of development. Therefore, we would like to highlight some tips and tricks to help you get the most out of the extension.

- If the larger functionality is not generating the desired results, consider breaking down the problem into smaller pieces. For example, if we want to generate a rock-paper-scissors game, we can start by generating a series of functions that can be used to play the game. Then, we can use the generated functions to build the game.
    - a function to randomly select between rock, paper, and scissors
    - a function to accept the user's input and validate it
    - a function to compare the user's input with the computer's input and determine the winner
    - a function to play the game

- Some helpful formulations for the `Hey, GitHub!` extension: 
    - "lets put it all together" - oftentimes, this phrase is useful to write a function that can tie together the smaller functions we have generated earlier.
    - If the goal is to synthesize a method body, consider using the following formulation: "a method `intended method name` that accepts parameters `parameter names with types` that `intended functionality` and optionally return `return type`"

- You can ask the extension to explain code to you, for example "explain lines 5 to 9"

- You can also converse with the assistant. For example here is your side of one possible conversation:
    - give me some ideas to add up a list of numbers
    - ok, show me some code
    - ok, let's insert that code

- Since the extension relies on the GitHub Copilot infrastructure, it is important to note that the code completions responses are non-deterministic. Therefore, it is possible that the extension may return slightly different code completions for the same input. Thus, canceling the code completions and trying again may yield a different result.

- The underlying speech recognition technology estimates the end of an utterance based on the silence in the audio stream. Since different folks have different speaking styles, we have left the silence threshold as a configurable parameter. You can change the silence threshold by editing the `Hey, GitHub!` extension settings. The default value is 1.25 seconds. However, if you are feeling particularly adventurous, try setting the value to 0.5 seconds.

- Likewise, the rate at which the extension speaks out the responses is also configurable. You can change the speech rate by editing the `Hey, GitHub!` extension settings. The default value is 100% of the normal speech rate. However, this value can be set to any value between 1% and 200%.

- We recommend having a good microphone to get the best experience with the `Hey, GitHub!` extension. In our experience, a good microphone greatly improves the accuracy of the speech recognition and as a result, the accuracy of the entire extension. 

- There is way to define custom commands for the `Hey, GitHub!` extension. In the extension configuration you can define a custom utterance and map it to a known VS Code command. For example, if you want to define a custom command to toggle the sidebar, you can define the utterance as "toggle sidebar" and map it to the VS Code command "workbench.action.toggleSidebarVisibility".

- If you would like to use your speech-to-text engine to interact with `Hey, GitHub!`, you can direct the output of these systems into the `Hey, GitHub!` Webview's chat input.
Remember to turn off the default speech-to-text engine by clicking on the microphone icon on the web view.

<a href="#top">Back to top</a>
# Known Software Limitations

"Hey, GitHub!" is a proof-of-concept extension that is not intended for production use. Instead, it is an experiment that demonstrates the potential of voice-first UX for developers. While we are working hard to eliminate as many bugs as possible, there are some known limitations that we would like to highlight.

- The extension is currently only available via a signup process. We are working on making it available to everyone. 
- The extension competes with the code completions of the IDE and the GitHub Copilot infrastructure. This can lead to some unexpected behavior. Therefore, the users are encouraged to turn off the GitHub Copilot functionality when using the "Hey, GitHub!" extension.
- The extension only supports one instance of VS Code. The extension may produce undesired results if you have multiple VS Code instances open.
- The extension currently works with the default microphone of the system. We are working on adding support for users to select the microphone of their choice attached to the system.
- The extension has been tested on Windows 10 and macOS. While the software should work as is on a Linux machine, we have not tested that completely.

<a href="#top">Back to top</a>
