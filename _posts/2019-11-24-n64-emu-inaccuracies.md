---
layout: post
title: "The Faults of Nintendo 64 Emulation"
date: 2019-11-24
categories: blog
---
I'm sure you've played a Nintendo 64 videogame on an emulator before. Nintendo's Virtual Console or perhaps some less-official platforms. Whatever you've emulated the N64 on, you've probably thought you were getting a definitive experience. Certainly better than that nasty blurry original N64 with a controller for people with polymelia, right?

WRONG.

You see, the Nintendo 64 had especially difficult hardware to emulate, at first. The CPU was particularly difficult to emulate with ones more common in PCs, then, and the graphics processor was decently unique to the hardware.

Some attempts to create a N64 emulator were made, of course, but nobody got anywhere close to running retail games until UltraHLE in 1999, which ran games at full-speed on relatively average hardware. Of course, the emulator still wasn't very good. It pioneered the concept known as high-level emulation, which in this case - and this is an oversimplification - means it doesn't emulate the actual behaviour of the hardware, like low-level emulation does. Instead, it essentially does the equivalent of that behaviour on the hardware you're emulating with.

This does have its advantages. For one: speed. Low-level emulation (LLE) tends to be slower than high-level emulation (HLE). That's a pretty major benefit, naturally. In some situations, it's also easier to maintain code-wise. But the pros end about there. There's one very major drawback to HLE.

Accuracy.

And that's why N64 emulation is STILL not up-to-snuff with many other consoles. Essentially every emulator for the platform has, until very very recently, had a number of problems. This is made worse by the fact most of them still use an ancient plugin system for various components like input, audio, and graphics, so even on multiple versions of the same emulator, you might have varying output. Of course, you can still enjoy most games just fine even with these inaccuracies. But that doesn't mean they aren't there, and that they haven't had an impact.


### Examples
Let's take a quick look at *The Legend of Zelda: Majora's Mask*. This game was released for the N64 pretty late in the console's lifespan (2000), and it required a special Expansion Pak, which doubled the available memory on the N64. You bet it used some of the more advanced graphical features the N64 allowed for. The game was released in a collection of Zelda games for the GameCube in 2003, and it is one of the first times Nintendo used an official Nintendo 64 emulator.

Even Nintendo knows it's a mess. Sorta. When you load up the game it tells you there will be a... "sound irregularity."

<p align="center">
<img src="/assets/2019-11-24-n64-emu-inaccuracies/1_GCN-Disclaimer.png" alt="Also, they claim the problems come from the 'transfer' of the game from the N64 to GameCube. And not, you know, the emulation."/>
</p>

Well, trust me, you have bigger things to worry about than slight sound skips here and there.

Enabling controller rumble is a death sentence. The game will crash for no evident reason randomly. How did they not catch this?

More notably, the graphics are entirely broken in a number of places. About ten seconds into the game, for example:

| N64                                                                  | GameCube                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/2_N64.png"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/2_GCN.png"/>        |

Yeah, the fog is so thick in the GameCube version, it's impossible to see the background!

Interestingly enough, we have the opposite problem in the next shot:

| N64                                                                  | GameCube                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/3_N64.png"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/3_GCN.png"/>        |

There's no visible fog at ALL in the GameCube version, here.

It gets worse. When Link is hit to the ground, and the Skull Kid gets away, the fog fades away a little. But as you can see...

| N64                                                                  | GameCube                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/4_N64.gif"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/4_GCN.gif"/>        |

The fog flickers in the GameCube version instead of smoothly being reduced.

Why do these fog glitches happen? Well, the fog is achieved with the N64's special Reality Signal Processor (RSP). This is a part of the co-processor which handles graphical calculations on the N64. It essentially picks a colour for the fog, and blends the colour of each pixel with the fog colour. The further from the game camera the pixel is, the more times it blends, which makes it appear as if the fog is thicker farther away.

As you can expect, special hardware like the RSP is the hardest to emulate. That's why we have all these graphical glitches: it's simply not emulated accurately. And since most N64 emulators do graphics with HLE, and development on one N64 emulator is based on development of other ones, these problems tend to carry over across most N64 emulators. The fog glitch, specifically, however, has been fixed since the Wii VC version, and it does not appear on most modern N64 emulators, thankfully.

# But there are some that do.
And there is more than one example within the next five minutes of the game.

Link falls down a hollow tree and appears to hallucinate, and you see a lot of fuzzy colourful outlines of things you'll eventually see later in the game. The "fuzzy" part comes from an alpha dithering effect the RSP enables. This is used in a number of games like Super Mario 64's vanish cap and teleporters. However, Nintendo's emulator didn't do this until the Wii U Virtual Console, and many Nintendo 64 graphics plugins still fail to do this.

| N64                                                                  | GameCube                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/5_N64.gif"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/5_GCN.gif"/>        |

Now, this is where you start seeing lasting effects - and in fact the biggest problem with these inaccuracies. Let's take a look at that scene in the 3DS remaster.

| 3DS                                                                  |
| :---:                                                                |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/5_3DS.gif"/>       |

Yep! Even in the 3DS version the effect is missing. I do think it would've looked better with the effect, but it's not too big of a deal.

But the next one? Oh boy. This is a pretty important effect that doesn't work properly on most emulators.

The titular mask has some otherworldly abilities, and it uses this magic effect a number of times throughout the game. It looks like there's some sort of magic pulsing through it, and there's a large cloud of this magic that surrounds it. But not only is the translucency on the cloud the wrong amount, the blue magic is missing the core blue part, and only the purple outline is displayed.

| N64                                                                  | GameCube                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/6_N64.png"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/6_GCN.png"/>        |

It really just looks worse on GameCube. And this is rarely emulated properly. Even on the Wii U Virtual Console, it's broken! The problem here is a translucency shader the game used, which essentially adds or subtracts pixel colours to or from the one that overlaps. Only basic support for this seems to exist in most HLE emulators, so the more advanced methods used here don't work.

Now, given the severity of this bug, surely they fixed it for the 3DS version, right?

| 3DS                                                                  |
| :---:                                                                |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/6_3DS.png"/>       |

Nope! They redid this effect, but given the highlight on the purple colour and the lack of the lightning-esque energy graphic, it's safe to say they looked at the broken version and based their new graphics on it.

And indeed, there are more instances of broken graphics in Zelda. There's a boss in Ocarina of Time, for example, that uses a similar translucency shader that doesn't work at all even on the Wii U release, and the 3DS developers didn't include the effect either. But let's take a look at something else, for some variety.

Banjo Kazooie has a big emphasis on puzzles. And to show this, right off the bat, the menu is built with puzzle pieces before being displayed! To do this, the game essentially captures an image of the first frame on the menu and splits it up into textures. These textures are then applied to the puzzle piece. But here's the problem: many emulators will avoid reading the frame-buffer every frame to make the game run faster. You'll see why this is a problem pretty much immediately upon looking at the screenshot from the emulator.

| N64                                                                  | Emulator                                                              |
| :---:                                                                | :---:                                                                 |
| <img src="/assets/2019-11-24-n64-emu-inaccuracies/7_N64.png"/>       | <img src="/assets/2019-11-24-n64-emu-inaccuracies/7_EMU.png"/>        |

Yeah, it just fills the puzzles with black instead. This problem, of course, is pretty noticeable, so many graphics plugins have the option to read from the buffer every frame.

There are plenty other games with problems like these. Paper Mario is notorious for being horribly inaccurate and slow on emulators because it uses a lot of special RSP effects. But nobody really talks about these smaller problems. That doesn't mean they're not important! Emulation is slowly but surely improving. The latest version of GLideN64 for Mupen64Plus, for example, doesn't have any of the problems I've mentioned at all in this post. I hope someday, N64 emulation is good enough that people can experience the console's games as they were originally intended on modern hardware.