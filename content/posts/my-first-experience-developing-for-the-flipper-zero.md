+++
title = "My First Experience Developing for the Flipper Zero"
author = ["Steve Tautonico"]
description = "Description goes here"
date = 2022-08-07
draft = true
unlisted = true
+++

## Preface {#preface}

For those who don't know, the [Flipper Zero](https://flipperzero.one/) is a little open source multi-tool
device that is able to read/write/emulate several wireless protocols such as RFID, NFC, the sub-GHz frequency
range, IR, and more. Since the flipper's firmware is open source, many developers in the community are currently
expanding the official firmware with additional functionality by adding additional plugins and reworking existing features.
One of these default features is the ability to act as a U2F key (over USB). My current U2F device is an (_unspecified_)
hardware U2F and TOTP key combo. I wanted a backup just in case I lost my _unspecified_ hardware key. Using the Flipper
(will be referred to as **f0** for the rest of this article) as a U2F key seemed like a decent idea since it was a default feature.
However, it does not support TOTP by default. The f0 does have a RTC (real-time clock) chip on board, meaning it could
theoretically support a TOTP app. Since the f0 is open source, I decided to try to write it myself.
Note: I will only be discussing my experiences specifically related to the f0. Any issues I had due to my lack of knowledge of C will be left out.


## Research {#research}

Before programming anything, I needed to do some research in order to find out how to even begin programming an app for the f0.
I quickly discovered that no official documentation is available, which made getting started really difficult. I tried asking
the wonderful people of the [discord](http://flipperzero.one/discord) where to start. The most common piece of advice I got
was to take a look at other people's apps and see how they were built. Looking around some firmware forks, I came across a simple
[clock app](https://gist.github.com/CompaqDisc/4e329c501bd03c1e801849b81f48ea61) in the [Unleashed firmware](https://github.com/Eng1n33r/flipperzero-firmware).
Another resource I was pointed to was [Atmanos' Flipper Software Docs](https://flipper.atmanos.com/docs/overview/intro). This
resource ended up being the most useful overall.

The f0's firmware supports three different GUI paradigms:

1.  "_ViewPort_": Simple and very flexible, but no navigation helpers or default components, good for games/graphics applications due to full control of graphics
2.  "_ViewDispatcher and View_": Slightly more complex than _ViewPort_, but has the ability to use reusable views and navigation helpers (the one I ended up choosing)
3.  "_Scenes and Views_": The most complex and heavy, but ideal for complex apps.

After doing a bit of research, I felt confident in my knowledge and began to program...


## Prototyping {#prototyping}

Building a TOTP app for the f0 required two main components: the GUI interface and the TOTP implementation in the backend.

Before I started, I asked the discord to see if anyone has already implemented TOTP. I was told that [Astra](https://github.com/Astrrra) had already
built a little [TOTP demo](https://github.com/wetox-team/flipperzero-firmware/tree/gen-totp/applications/totp).
Now that I knew the complex part of the project was done, all I needed to do was build a simple interface for this implementation.
Little did I know that I would re-write the app three times over.

During my first attempt, I started programming using the "_ViewPort_" GUI paradigm. This attempt ended quickly when I realized that I was
unable to use the list of items, called the `VariableItemList` or the `Submenu` component (they slightly vary in behavior)

During my second attempt, I tried using the "_Scenes and Views_" GUI paradigm. This paradigm was incredibly hard to wrap my head around.
After a few hours of playing around with some code, I was able to get a simple demo working, but my code was polluted with random
code from the prototyping process. At this point, I realized that this paradigm was way too complex for my needs.

I went into my third attempt with a pretty decent understanding of how the first two paradigms work.
From my understanding, the "_ViewDispatcher and View_" system has two main components: the view dispatcher and the views
(if this wasn't already obvious from the name.) Views can be thought about like pages on a website. The views are similar to
the setup in the "_ViewPort_" paradigm, except for the required `alloc` and `free` method. These views are registered with the
view dispatcher component. This component is in charge of changing which view is currently on the screen. When the view dispatcher
is instructed to set the current view, it calls the view's `alloc` function which allocates memory for the required components of the view
(the view itself and the view model (similar to the view's state)), sets the context passed to the view, and sets up the callbacks for input,
drawing, and more. Once the view dispatcher changes views, it calls the current view's `free` function, which is in charge of freeing any
allocated memory in the view.

I started programming, vaguely following along with the official flipper firmware [display test program](https://github.com/flipperdevices/flipperzero-firmware/tree/dev/applications/debug_tools/display_test)
(as suggested by Atmanos's Docs) and was making good progress. The hardest of developing for the flipper seems to be trying to understand
how all the components work together and just how apps are structured in general. Once you understand that, building a flipper app is relatively easy.
Some official documentation on how this all worked would make getting started significantly easier (**wink wink, flipper team 😉**)


## Sources {#sources}

-   [Atmanos' Flipper Software Docs](https://flipper.atmanos.com/)
