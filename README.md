# 10line-lander
Lunder Lander game in Turbo BASIC XL for Atari 8-bit. Entry for 2019 10-line BASIC contest

Use the joystick controller to land your LEM (lunar excursion module) on a moon. Land on one of the green landing pads. The trigger fires the main thrusters, pushing the ship upward against the moon’s gravity. Left/right stick movement fires the side thrusters for horizontal movement.

A control panel shows your vertical speed (indicated by ↓), horizontal speed (→), strength of gravity on the moon (G), and amount of fuel (F). To land safely, you must touch down on a landing area with a vertical speed of 10 or less, and horizontal speed of 5 or less. Flying off the sides or the top of the screen is deadly. Running out of fuel is not recommended.

Each moon is a little different, with gravity ranging from light (G5 in the control panel) to heavy (G20.) Moons usually have one or two landing pads. (Rarely, you will come across a moon that has none! In this case you will die. I’m sorry. Space exploration is dangerous.)

The first Lunar Lander that I was exposed to was Atari’s vector arcade version, which seemed amazing — and impossibly difficult. Later, my dad bought the Adventure International version of Lunar Lander for his Atari 800. (It was one of the few pieces of Atari software that he didn’t pirate.) In that version, the LEM doesn’t rotate. Instead, side thrusters push the ship horizontally while it remains in a vertical position. I did the same in my version.

(That’s where I learned the word “hybrid.” The stats on the back of the box said “Language: Hybrid.” I wondered if that was some programming language I hasn’t heard of; dad explained that the word meant “a combination of two things.” In this case, BASIC and assembly language.)

Benj Edwards wrote a great [history of Lunar Lander games](https://www.technologizer.com/2009/07/19/lunar-lander/)

I’ve wanted to program a Lunar Lander-type game since I was a teen. I’m pretty sure I tried it using shape tables on my Apple IIc in AppleSoft BASIC, and experimented with it in Atari BASIC at some point, but I never could get the movement with respect to thrust and gravity right. I didn’t have the math concepts. But in the past few weeks, with my buddy helping with the math for Bouncy; and reading [Bruce Artwick’s book Microcomputer Displays, Graphics and Animation,](https://amzn.to/2Sa5Dhd) I now know jussssst enough math to be dangerous with Atari graphics. So I was finally able to create a version of Lunar Lander, and in 10 lines of Turbo-BASIC XL.

For the contest, my program fits in the 120-characters-per-line category. In terms of cramming stuff into 10 lines, it’s some of my best work and I learned a lot. Several times I thought the program has to be done, there was absolutely no more room to squeeze in another feature. Then I’d find a way to do something in fewer bytes, making room for a tiny improvement elsewhere.

My favorite was replacing for-next loops to move or generate data with the MOVE statement, with copies memory around RAM. For instance, I needed to zero out Player (sprite) data. Normally I’d do that with FOR I=P+512 TO P+896:POKE I,0:NEXT I. But — MOVE DPEEK(88),P+512,384 does the same thing with fewer bytes (and much faster.) But I needed to copy from an area of RAM that is all zeros. Where would I find such a place? A newly blank screen is filled with zeros. At another point, I needed a mess of random-looking data for the ship explosion. I started with a FOR-NEXT loop writing RANDom numbers, but ended up moving random bits of data from the Atari ROM into sprite memory. Again, it was much faster and took of less precious program space.  I’m not implying at all that I invented this technique, but I figured it out on my own and it was satisfying.
