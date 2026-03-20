# Hidden Content

There are lots of secrets and unused content hidden throughout the OS. Most of it was either redundant, repetitive, or just plain bloat.

***

## BIOS

The Bios was only seen in 3 different versions, completely disconnected from each other. Just a note, but it seems that right before each major code rewrite the BIOS was removed, probably because it caused so much bloat.&#x20;

**v5.1**: Could be accessed through the "advanced" panel in settings, or in the bottom right when hovering over the power and wifi buttons in the login screen. It offered fixes to common errors, which were saved and logged upon happening, some limited user settings, and even some basic proxy config.

**v10:** Either through the welcome screen in the top left when logging in for the first time, or within "Security" in the settings. It was the first time it appeared in black and green, and it offered quick access to many more functions than in v5.1.

**v15:** This version's BIOS could be customized in the System. See [BIOS Commands](../docs/creating-content/bios-commands.md) for more details on how it works. It can only be opened through:

1. Opening terminal
2. Type `js`
3. Enter: `API.win.setShowBios(true);`

***

## Chatbot

The chatbot is only in 3 versions as well, that being v12.5, v14 and v15.

v12.5: The chatbot is a long series of if statements. Its not a real chatbot, it just regurgitates whatever you say to it. For example, saying "bug" or "issue" repeats whatever issue you tell it.&#x20;

v14 & v15: This is a somewhat sophisticated AI, built using an intent based model in python. However, the weightings were way off for some inputs, and it caused some text inputs to be completely overlooked. Also it was a pain to implement.

You can open the chatbot in v14 & v15 by:

1. Opening terminal
2. Type `js`
3. Enter: `API.win.setMenu("Chatbot");`

***

If you made it this far, congrats.
