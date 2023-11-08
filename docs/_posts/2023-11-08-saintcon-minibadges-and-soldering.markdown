---
layout: post
title:  "Saintcon, Minibadges, and Soldering, Oh My!"
date:   2023-11-06 08:00:00 -0700
categories: jekyll update
author: Cooper Hopkin
---

If there's anything you should know about me, it's that I have ADHD. Like, I actually have it. Clinically diagnosed and all that. This is important, because if there's one symptom I have that's obvious, it's hyperfocusing.

Now, what exactly is hyperfocusing? Basically, I latch onto an activity, and that's all I'll do. It borders on obsession. I'll start it, I'll buy all of the supplies I need for it, and I'll go at it for hours at a time (much to the chagrin of my wife). And often, I'll get really good at it. Most of the time it only lasts for days. Usually that's if I can't get good at it very quickly, it's not very interesting, or if the "end product" of the activity isn't very satisfying. But once in a while I'll find something I really enjoy, and I'll keep at it (usually I'll stop obsessing over it, fortunately). That's how I started with a few of my hobbies, like woodturning and (interestingy enough) cybersecurity.

I'm sure you can tell where this is going from the title.

A couple of weeks ago, I went to a conference called Saintcon. It's a cybersecurity conference like Blackhat or Defcon. I was able to score a ticket through my internship, which was fantastic because the tickets are expensive and I'm a poor college student. It was incredible. It was about 3.5 days long, and I learned and networked more in those three days than I have basically anywhere else besides school. I was talking to industry professionals, learning about security solutions that are out there, and learned a bit about a dozen different communities, like OT/IoT hacking and the Space sector.

But most importantly (to this post, at least), I learned how to solder.

Saintcon has a big sort of long running side-activity called minibadges. Basically, they're 2 cm x 2 cm printed circuit boards that come with components like LEDs and resistors (almost all surface mounted) that you can collect and assemble yourself by soldering everything together. That's what sent me down the long, deep rabbithole of soldering. Over the course of 3.5 days, I managed to gather about 80 minibadges, including duplicates and the special badges that were specifically meant for the 2023 badge (there was a whole RPG minigame, it was awesome). I collected so many that at some point I decided to just continue collecting badges and worry about assembling them after the conference. They all look something like this:

<div class="row">
    <div class="col">
        <img src="/assets/images/minibadge_front.JPEG" class="float-start img-fluid" alt="Front of a minibadge">
        <p class="text-center text-body-secondary">Front of a Captain America Badge</p>
    </div>
    <div class="col">
        <img src="/assets/images/minibadge_back_glued.JPEG" class="float-end img-fluid" alt="Front of a minibadge">
        <p class="text-center text-body-secondary">Back of the Captain America badge. It has a blob of hot glue so that the light from the LED is diffused through the translucent part of the badge</p>
    </div>
    <div class="col">
        <img src="/assets/images/minibadge_back.JPEG" class="float-center img-fluid" alt="Front of a minibadge">
        <p class="text-center text-body-secondary">Back of a different badge that doesn't have hot glue on it. Note the two LEDs and the resistor, all of which are SMDs</p>
    </div>
</div>

I also bought a board at the Saintcon shop that holds 100 minibadges so that I can display all of the badges that I collected and assembled. I had to solder all 200 headers for the board, a button that controls how fast the clock on the board ticks (Some of the minibadges can flash with the clock!), a little device that allows power I/O, an on/off switch, and a mini-usb port for power:
<div class="row">
    <div class="col">
        <img src="/assets/images/10x10_front.JPEG" class="float-start img-fluid" alt="Front of the 10x10 board">
        <p class="text-center text-body-secondary">Front of the 10x10 board with all of the minibadges lit up</p>
    </div>
    <div class="col">
        <img src="/assets/images/10x10_closeup.JPEG" class="float-center img-fluid" alt="Closeup of 10x10 board">
        <p class="text-center text-body-secondary">A closeup of the 10x10 board with some fun badges</p>
    </div>
    <div class="col">
        <img src="/assets/images/10x10_back.JPEG" class="float-center img-fluid" alt="Back of the 10x10 board">
        <p class="text-center text-body-secondary">Back of the 10x10 board. See all of those soldered pins? I did all of those. The only thing I didn't do was add the ICs for the clock.</p>
    </div>
</div>

So that's what got me into soldering. I bought a cheap soldering iron off of amazon, some lead-free solder (I didn't realize that there was an actual difference between leaded and lead-free solder at that point), and a magnifying device with helping hands, and got to it. It sparked something in me. I loved it. Figuring out what iron heat worked best, making sure the joint looked nice (that took a lot of practice), and figuring out how to make the LEDs look just right when I plugged the minibadge in. I loved the challenge of working with the tiny 0603 (1.55 mm long), 0402 (1 mm long), and even a 0201 (.6 mm long) size LEDs and resistors. It was great, And now I'm hooked. I'm watching soldering videos on Youtube. I'm buying soldering kits online. I'm even working on designing my own PCBs using Kicad. 

I can see myself doing this as a hobby for a long time. It's nice to have a hobby that has cool, physical results that I can point at and be proud of. If you've never soldered, I would definitely suggest trying it out. It's surprisingly cheap. You can get a soldering iron, solder, a magnifying/helping-hand tool, and a couple of soldering practice kits on Amazon for less than $75. And the consumables like solder, flux, and tip cleaners are super cheap as well. Maybe you'll like it. Maybe you'll love it like me. Can't hurt to try, right?

--Cooper

Hello World in [Brainf*ck](https://en.wikipedia.org/wiki/Brainfuck)

{% highlight brainfuck %}
[ 
Brainfuck is an esoteric programming language that essentially
emulates a turing machine. You have cells that contain 1-byte 
values. > moves to the next cell, < moves to the previous cell, 
+ increments the value, - decrements the value, . outputs the
ASCII encoded value of the current cell, "," accepts one byte
of ASCII encoded input and stores it in the current cell. If the 
current cell is 0, "[" will cause the instruction pointer to jump
to the matching "]" command, and after a "[" instruction, if the byte
in the current cell is non-zero, ] will jump back to the matching 
[ command.

This whole thing is an initial comment loop in brainfuck. Because the data 
pointer at the beginning of a program is always 0, when the compiler
sees the "[" at the beginning of the instruction set, it will 
immediately jump to the matching "]" instruction. Be careful, 
because anytime you use a "[" in the initial comment loop, the
loop still has to be balanced with a corresponding "]" instruction.

This program should print out Hello World. I hope. ]]

++++ ++++            Set C0 to 8
[
    > ++++          Add 4 to C1; This will always set C1 to 4
    [               Because the cell will be reset with each loop
        >++         Add 2 to C2
        >+++        Add 3 to C3
        >+++        Add 3 to C4
        >+          Add 1 to C5
        <<<<-       Decrement loop counter in C1
    ]               Keep going until C1 is 0; 4 loops
    >+              Add 1 to C2
    >+              Add 1 to C3
    >-              Subtract 1 from C4
    >>+             Add 1 to cell 6
    [<]             Move to the first cell containing 0 you find; should be C1
    <-              Decrement loop counter in C0
]

Current Results:
C0  C1  C2  C3  C4  C5  C6
0   0   72  104 88  32  8

Currently at C0 = 0
>>.                 C2 contains 72 which is H
>---.               Subtract 3 from C3 to get 101 which is e; print
++++ +++..          Add 7 to C3 to get 108 which is l; print
+++.                Add 3 to C3 get 111 which is o; print
>>.                 C5 = 32 which is " "; print
<-.                 Subtract 1 from C4 to get 87 which is W; print
<.                  C3 = 111 which is o; print
+++.                Add 3 to C3 to get 114 which is r; print
---- --.            Subtract 6 from C3 to get 108 which is l; print
---- ----.          Subtract 8 from C3 to get 100 which is d; print
>>+                 Add 1 to C5 to get 33 which is !; print
>++.                C6 = 10 which is newline; print
{% endhighlight %}