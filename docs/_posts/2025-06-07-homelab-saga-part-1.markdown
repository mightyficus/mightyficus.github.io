---
layout: post
title:  "Corporate Greed Made Me Do It"
date:   2025-06-07 20:00:00 -0700
categories: general
author: Cooper Hopkin
---

My homelab started out in the same way that I think a lot of people's homelabs do: Corporate greed.

Specifically, ads. I really hate ads, and I think a lot of people feel the same. On my personal computers, dodging ads is really easy. Install Firefox, install uBlock Origin, boom. No ads. Toss in something to block cookies, and I'm golden. But you can't really do that on, say, a smart TV or a smartphone app. I found out that there's a pretty easy solution for that: a PiHole.

The idea of a PiHole is fairly simple. You change your DHCP server to make all of your devices point at the PiHole for DNS, the PiHole takes those requests, filters out requests for domains known for serving ads, and sends along the rest of them. It's called a DNS sinkhole. It doesn't handle all that much traffic, since it's just the DNS requests, so a relatively lightweight machine can handle it without issue. I already had a couple of Raspberry Pis kicking around, so I set it up, and boom. No more ads. Well, almost. It's all based on lists of domains to block, so if an ad domain isn't on one of those lists, it gets through. The lists get updated pretty frequently to catch these, but if you're feeling ambitious, you can manually add domains to block to try to stop those ads from getting through.

The thing about the PiHole is that it's extremely easy to set up, and it's extremely lightweight. The Raspberry Pi that hosts PiHole has 4 GB of memory, and even with other services running on it, I don't think I've ever seen seen it use more than half of that. To install it, all you really have to do is clone a GitHub repository and run the setup script. Or pipe a script directly into bash, if you're feeling like being risky. It sets itself up, and all you really have to post-setup is change your DHCP server to get all of your devices to point to the PiHole as a DNS server. You could even set up the PiHole to be your DHCP server, if you really wanted to.

So that's all I really did at first. I set it up and forgot about it. I had other things going on, and I kinda just forgot about it. There were some moments of panic when I started to do some home automation (that's another post in the making) and did some network segmentation and all of my computers suddenly couldn't access the internet because the DNS server suddenly wasn't in the right place (remember kids, it's always DNS), but other than that, it was just part of the magic network box that I didn't need to think about.

Then my router got the ability to easily display some of the North/South traffic flow of my network (internet in/out), and I went down the rabbit hole.

I noticed that some of the DNS requests leaving my router weren't coming from the PiHole. Remember, the PiHole is a DNS sinkhole. Any DNS query leaving the router should be coming from that Raspberry Pi, otherwise the PiHole would be useless. I was intrigued and frustrated (and maybe a little bit paranoid), so I dug in. I noticed that all of the DNS queries that weren't going through the PiHole was coming from IoT devices, and I remembered reading that sometimes IoT devices have DNS servers hardcoded into them, and don't actually use the DNS servers given to them by their DNS lease. This is to get around exactly what I was doing: setting up a DNS sinkhole and not allowing telemetry data (and who knows what else) to get to the internet. Corporate greed was at it again. Clearly, I wanted to stop this. I couldn't let greedy corporations get my data. So I did some research into it and learned about DNAT Masquerade firewall rules, and eventually got my router to redirect any DNS queries to the PiHole, whether it was intended for that destination or not.

This all got me thinking about privacy and security hygeine. It was already on my mind, since I recently had reason to get rid of as much social media as I could that could be used to reveal my personal info. Other than LinkedIn and this website (I don't even like my info being there, but I like having job interviews even more), I try to stay as anonymous as I can online. So I started thinking about things that could enhance my privacy. I remembered learning about different internet protocols in college, and that DNS queries are, by default, unencrypted. So in theory, someone (like, say, an ISP) could intercept those packets and know exactly what websites I'm visiting, and there was nothing I could really do to stop them. I didn't like that. So then I started to research DNS-over-HTTPS (DoH), which encrypts DNS queries in the same way that your actual internet traffic is encrypted. There are still issues (someone has to receive those queries and respond, which is a potential point of failure), but that sounded like something I wanted. That's when I started to figure how much PiHole has going on under the hood. 

The PiHole itself doesn't support DoH, but it integrates really well with services that do. So I got dnscrypt-proxy set up, which is essentially a service that translates DNS queries into DoH queries. It also has a lot under the hood, and I plan on tackling some of that when I get the chance. But that's for future Cooper to figure out. But this led me to discover that both dnscrypt and PiHole have some pretty rich APIs for gathering data analytics, and I thought that would be pretty cool to be able to look at that. So I started looking at Grafana, because I heard someone at work talking about it once. Then I learned about how Grafana doesn't actually aggegate or process data, it just visualizes it, so I started learning about Prometheus. I was looking at all of this and thought, "Wow, I'm starting to do a lot of stuff on my network, I wonder what all of this traffic looks like." I was also starting to play with vulnerable machines for pentesting practice, so I already had that on my mind, and decided I should look at SecurityOnion. I spun that up, saw how much memory it used, immediately ditched it, started looking into other solutions, and finally found out what this whole "ELK Stack" thing was that I always had wondered about. All of this was a lot, so I bought a little Intel NUC and set up Proxmox to host all of it (or at least most of it). Around this time, I had also started to get fed up with how much I'm paying for streaming services, and got working on a Plex media server. And I already had these IoT devices that kicked off the rabbit hole, so I started playing with Home Assistant. I wanted to be able to easily access all of these services that I suddenly had going, and got working on an Nginx reverse proxy. I didn't want to add manual DNS entries to the PiHoe that pointed at the same machine, so I learned about dnsmasq and wildcard local domains. And... And... And... 

That's how it all started. A PiHole, some naughty IoT devices phoning home, wanting to poke some corporate goon in the eye for all of the data they wanted from me, and a whole lot of stubborness. And now I have a _lot_ of technology to keep up with. I have a lot of this set up, but I haven't even scratched the surface of what all of it can do. And I'm having _so much fun_. Looking through documentation isn't a drag, it's a scavenger hunt. Running into an issue isn't demoralizing, it's the promise of a dopamine rush once I eventually figure it out. It's been so long since I've actually felt passionate about a home project. But I'm seeing this huge multi-project ordeal that I've created for myself, and rather than feel daunted, I feel excited.

This is just the starting point. I'm going to try to write about some of the things I'm wanting to do and challenges I've faced while setting things up. There's so much more I want to do, and I want to document it all.

--Cooper 

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