---
layout: post
title:  "I Am Enough"
date:   2024-02-06 12:00:00 -0700
categories: general
author: Cooper Hopkin
---

I can't seem to keep current with this blog, but honestly, I feel like I have some pretty good excuses.

I don't want to say I'm the busiest guy ever. I'm definitely not. But for a 20-something, I have a pretty full plate. I talked about it a bit in my last post, but here's a TL;DR. I did the math at one point; with school, my job, and my (unpaid) internship, I'm working the equivalent of two full-time jobs. About 75 hours, give or take. And then factor in all of the things I'm doing alongside my "official" stuff, I'm also the VP of my university's cybersecurity club, I'm training for two different cybersecurity competitions, doing some extra work programming a custom frontend for making Snort rules, helping a friend with her art installation by developing some lighting effects with my microcontrollers, and trying to spend some time with my wife every once in a while. It's a lot.

My wife and I have started up a bit of a mantra: "One more semester. Just one more semester."

All of this looks good on a resume (You can check it out! There's a big button on the top of the page labeled "Resume" and it's pretty neat!). And I'm really enjoying the feeling of accomplishing things and being a significant contributor in the projects I'm working on. Technology is actually my passion, and I'm so happy that I've been able to find something I'm good at and that I enjoy doing. Some people never get that! But boy am I getting tired. And sometimes I wonder if all of this work is actually going to be worth it in the end. Am I actually going to be able to do all of the things I've been dreaming about doing?

If you couldn't tell, I'm stressed about jobs. It's kind of depressing sometimes. Usually I try to keep upbeat, but it still stings when I have all of this experience and education and extracurriculars, and I immediately get rejected for a supposedly entry level job I apply to. I don't want to whine. I really don't, especially since I know that there's a small chance that a future recruiter might read some of these posts (Hi future recruiter! Did I mention my resume?), but it's getting to be a lot. I know it could be worse. I have a steady job, and even if the pay is dismal, my wife and I are surviving. But the end of school is getting close, and I am starting to look to the future, and it's scary. There's a lot of uncertainty right now. I'm applying for jobs all over, and I have no idea where we'll end up. I'm suddenly not going to have the structure and certainty that school brings to my life. I don't even know that I'll be able to get the job that I want, even though the technology sector is always looking for applicants. I want to do penetration testing for my career. I love the feeling of accessing things I'm "not supposed to" (I'm talking CTFs and personal machines. All legal, I promise). But then I look for jobs, and every pentesting job requires 7 years of experience alongside a degree, and I start to get that hopeless feeling in my gut. I know that pentesting isn't really an entry-level gig. But I need experience in pentesting to get a job in pentesting, and suddenly I'm in a recursive loop with no return statement (I'm even a nerd when ranting, look at me!). 

But sitting here, writing all of my depressing thoughts down, I'm remembering something my dad used to say all the time. 

## You are Enough.
<br>
And that's the thing. I am. Despite all the crap I tell myself sometimes. Despite the fear and the uncertainty. Despite the recruiters that turn me down, the contacts I've made that no longer return my emails. I've accomplished more than past-Cooper ever thought I could. I've done more work, learned more things, done more with my hands and mind than I ever could've hoped. What other people say, or more accurately what I __think__ other people say, doesn't matter. I'm proud of the work I've done and am doing. I'm doing great, and and some point, probably sometime soon, there's going to be people who see how much I've done, and they're going to want me to work with them.

So here's what's going to happen. I'm going to keep applying for jobs. I'm going to reach out to all of the people I've networked with. I'm going to keep up with my hobbies and extracurriculars. I'm going to graduate. And I'm going to start a job that I'll enjoy doing. And it's going to be incredible.

Because I'm enough. And I'm not going to let anybody, including myself, convince me otherwise.

-- Cooper

<br>This is a snippet of a program that makes my Raspberry Pi Pico flash "Hello, World!" in morse code. It's in a Python flavor called circuitpython.
{% highlight python %}
import board, digitalio, time

morse = {
    "H" : [1,1,1,1],
    "E" : [1],
    "L" : [1,0,1,1],
    "O" : [0,0,0],
    "W" : [1,0,0],
    "R" : [1,0,1],
    "D" : [0,1,1],
    "!" : [0,1,0,1,0,0],
    "," : [0,0,1,1,0,0],
}

UNIT = 0.1
DOT = UNIT
DASH = UNIT * 3
INTER_ELEMENT = UNIT
LETTER_GAP = UNIT * 3
STOP = UNIT * 7

def dit(led):
    led.value = True
    time.sleep(DOT)
    led.value = False
    #time.sleep(INTER_ELEMENT)

def dah(led):
    led.value = True
    time.sleep(DASH)
    led.value = False
    #time.sleep(INTER_ELEMENT)

def main():
    message = "Hello, World!\n"
    led = digitalio.DigitalInOut(board.GP15)
    led.switch_to_output(value=False)
    for chr in message.upper():
        # Newline will act as STOP character
        if chr == '\n':
            time.sleep(STOP)

        elif chr == " ":
            time.sleep(LETTER_GAP)

        elif chr in morse_alphabet.morse:
            for unit in morse_alphabet.morse[chr]:
                if unit == 0:
                    dah(led)
                elif unit == 1:
                    dit(led)
                # Characters always have a 1 unit wait between dits/dahs
                time.sleep(INTER_ELEMENT)

        else:
            print("Character not supported")
        
main()

{% endhighlight %}