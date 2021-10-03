---
layout: post
title: How To Use Magic Wormhole
author: nfd
tags:
    - explainer
    - technical
    - short
---
Magic Wormhole is a way to move files between computers over the Internet securely.
I'm writing this guide for people who just want to send or receive a file
and don't want to have to mess around too much.

*You can also find my latest guide on using Magic Wormhole (likely this page) with this URL, which is easier to read over the phone:* [nfd.moe/worm](https://nfd.moe/worm)

## wormhole-gui
A simple, good application for using Magic Wormhole is [wormhole-gui](https://github.com/Jacalz/wormhole-gui).
Let's go over how to get the latest version on most computers.
Head over to [its releases page](https://github.com/Jacalz/wormhole-gui/releases/)
and look at the top post--that should be the newest release.
There's a bunch of links underneath.
I'll help you pick which one to use.

#### Windows
Get the one that ends in `windows-amd64.zip` or similar.
Once it's downloaded, unzip the folder, run the `.exe`,
and you're good to go.

You may see a popup from Windows SmartScreen.
This is because Windows Defender hasn't seen large numbers of people run the program,
not because it isn't safe.
If you wish, click the "more info" link on top of the SmartScreen popup,
then "Run Anyway."

#### macOS
You want one of the two with "macOS" in the name.
If you know you have an x86_64 system,
pick the `amd64` one.
If you know you have an Arm system,
pick the `arm64` one.

If you don't know which one you have,
find the Terminal app,
type in `uname -m`, and hit enter.

* If you see something like `x86_64` or `i386`,
pick the amd64 option.

* If you see something like `arm` or `aarch64`,
pick the `arm64` option.

* If you see something else (like `powerpc`),
there probably isn't a quick and easy way to use wormhole-gui
for you right now.

If you're still not sure,
you can search online for your model of computer,
which should tell you which architecture you have.

#### Linux
Most Linux users probably already know what to do:
check your distro's package manager,
check for the CLI clients [magic-wormhole](https://magic-wormhole.readthedocs.io/en/latest/welcome.html) or [wormhole-william](https://github.com/psanford/wormhole-william)
if you don't want to bother with a graphical app.

If you don't already know what to do,
you *probably* want to download the `linux-amd64.zip` link.
If that one doesn't work, maybe try the `linux-arm64` one.
You can use the same `uname -m` trick in the macOS section.

## Usage
If you want to send a file,
go to the Send tab.
If you want to receive one, go to the Receive tab.

#### Sending files
On the Send tab, click the big plus button at the top,
then the type of thing you want to send.
If it's a file or directory, pick it out with the file picker.

An entry for the file should show up in the main window.
There should be a passphrase to the right of the file's name,
and it should look kind of like `4-detergent-kickoff`.
That's the phrase the person receiving the file needs to hear.
Read or send it to them,
and wait for the progress bar to the right to fill all the way
before you close wormhole-gui.

#### Receiving files
On the Recieve tab, there's a textbox to input the passphrase for the file you're
supposed to be receiving.
Enter it in there.
Remember the dashes between the words.
When the file's finished downloading,
you'll find it in your Downloads folder.

That's it.
If you found anything in this guide confusing,
please email me to let me know: nfd@nfd.moe

