---
title: "Migrating from Linux to Windows."
date: 2020-10-20T19:22:47+05:30
draft: false
tags: ["windows", "wsl2", "development", "linux"]
---

## General Trivia

Yes, I am a backend developer and I use Windows for development.
I know this is quite opinionated and depends heavily on one's workflow, but here are my 2 cents on it anyway.

I have been using GNU/Linux for quite a while now and I'm quite comfortable with it. I have worked with all kinds of flavors and distributions and since most of the tools I'm accustomed to using work out of the box on Linux, I wasn't tempted to go back to Windows for whatsoever reason.

However, I was aware of this WSL ecosystem fellows at Microsoft were building around Linux to attract developers to stick with 
Windows and I did try it. It wasn't as mature back then and I was not ready to hop off the "I use Linux" train, just yet.

## Here Comes WSL2

So one of my friends, [Gaurav](https://www.linkedin.com/in/gauravsaini964/); who is in a similar line of trade as me texts me that he's been using WSL2 and it's just nice.
That was tempting. I had windows on dual boot that I was using for casual gaming on my work machine.

WSL2 has been released with Windows 10, version 2004 out of the box, however, there are [steps](https://docs.microsoft.com/en-us/windows/wsl/install-win10) to follow to get on board with it. It's trivial and easy, just follow the link.

## Setting up

I am a backend developer who tends to use python and my whole development phase revolves around a few tools of the trade, which are:

1. Terminal (with window splitting)
2. Chrome (Browser)
3. VS Code (My primary Text Editor)
4. Postman (API Testing Tool)
5. DataGrip (DataBase Tool)

These all can run as good on Windows as they work on Linux, the problem is setting up python and the libs.
They just work better on Linux + there is a better chance of preemptive detection of issues that may occur on Linux environments.
All in all, I am using Linux inside Windows for development and keeping windows clutter-free.

Now Terminals are sexy, and we all know that for a fact. The one thing I loved the most on Windows is the new [Windows Terminal](https://www.youtube.com/watch?v=8gw0rXPMMPE). Unlike Command Prompt and Powershell, it is just amazing, not to mention it has (great themes)[https://windowsterminalthemes.dev/] and yes, it has window splitting.

## Down to Business

So now I have Windows Terminal and WSL2 enabled. I headed to Microsoft Store and searched "Ubuntu" and installed it.
I first replaced the `.ssh` folder that it had with my `.ssh` folder and doing a `chmod 400 *` on the contents of that folder.

If you use VS Code you must know of this tool called ["Remote SSH"](https://code.visualstudio.com/docs/remote/ssh).

I use this tool to connect to my bastion server and do pre-prod/staging deployment tests. It lets you open files in a folder and edit them *but* also if you want to do say, `runserver` in a Django project, it binds your `localhost` to bastion's `localhost`
and that is just amazing for last moment testing.

This Remote SSH tool not only lets you connect with remote machines but also to WSL and container targets, just like the one I installed.
You can just go to the Extensions section of the VS Code and get your hands on them.

![Extensions](/images/windows_to_linux/remote_extensions.png)


## Finale

So all in all, I am still using Linux but without dual boot and I am liking it so far.
I don't have to care about unoptimized apps (*coughs* Slack *coughs*) and all my tools run out of the box, just fine.