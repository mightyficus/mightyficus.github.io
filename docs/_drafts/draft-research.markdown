---
layout: post
title:  "Research (Yes I do that too)"
date:   2024-02-20 12:00:00 -0700
categories: general
author: Cooper Hopkin
---

Sometimes I forget that the reason I started this blog is to show off my research.

To be fair, sometimes I'm not sure how much I can share. And that's not an excuse, I am actually working on a project that has to do with national security. We're working with the Department of Homeland Security and CISA to help protect critical infrastructure. That's stuff like water treatment plants, refineries, and power facilities (nuclear, hydroelectric, coal, etc). But now I've gotten some information about what I'm actually allowed to talk about, so I don't feel bad about sharing what I've learned. That being said, I still need to be somewhat vague for security reasons. 

If you're keeping up with the news in the tech world (or even sometimes just the regular news), you know that a lot of critical infrastructure is being attacked right now. It seems like they're mostly focusing on water plants at the moment, but I'm sure if the trend continues, the attacks will start branching out to other critical services like power. The problem that we're facing right now is that critical infrastructure locations used to have really good security, but as the internet has evolved, the locations haven't really kept up. Some of it is really simple, common stuff. Misconfigurations in services, weird subnetting, and staying up-to-date with patches. You may be thinking, "Why is this so bad? Everyone has these issues, and it usually doesn't result in anything *too* bad." Well, there's a lot of reasons that make these mistakes more dangerous.

First, critical infrastructure is high profile. A successful attack against a nuclear power plant can be significantly more demoralizing than a commercial data breach. You hear that some data was exfiltrated from some gaming or social media website, the reaction is generally "Well that sucks, guess I need to change some passwords." Someone attacks a power plant, and your reacting is more along the lines of "This is really, really bad. I could lose power. That's nuclear, and that word is scary." Then you hvae the politics that always surround high profile critical infrastructure, like nuclear and wind power. If something like that is exploited, suddenly you have politicians that are using that as an excuse to cut funding or as an excuse to pass laws against those services. I am definitely not going to get into politics here, but we should not be using a breach of a single location as a reason to shut down an industry.

Finally (kind of, there's a lot more complexity than I even mentioned), there's the simple aspect of the criticality of these services. Yeah, if a data breach happens to some corporation (*cough* Equifax *cough*) it's bad. That's a lot of private information in the hands of people who don't care what happens to that information, as long as it makes them money. But that's nothing compared to what could happen if someone gets into a water treatment plant. You change the settings of a single machine, and suddenly a nuclear power plant is starting to overheat, or there's a lot more chlorine going into the water that we drink, which can be very, very bad. So the difference is between someone getting their hands on your data versus poisoning a city's water supply. Suddenly that data breach doesn't seem as important, right?

But I said earlier that our critical infrastructure used to be pretty secure. What happened?

The Internet happened.

It used to be that the only way do any major damage to the operational systems of a water treatment or power plant would be to gain physical access to the devices on those systems. They were air-gapped. That didn't make it impossible to attack (think Stuxnet), but it did make it very difficult. But now, for convenience, those devices are networked, usually in the same network as everything else. This makes things really easy for operators. They don't have to go down to the production area to control systems or apply security patches. It likely increases productivity and worker safety. But when you put anything on a network, no matter what kind of safeties you put into place, those devices are suddenly at risk. You add in the fact that OT devices (the stuff that control industrial proccesses, like pumps and sensors) are *extremely* fragile, and you have a recipe for disaster. I'm talking so fragile that an Nmap scan with the wrong parameters can crash the system.

But that isn't the worst of it. If the security were top-notch, I would sleep a bit better at night. But it's not.

This will be my life. I'm working as a vulnerability analyst, and I want to keep doing that. I'll be the one looking at how these systems could be accessed and exploited. But right now, I'm somewhat inexperienced. I'm about to finish up my degree, so I have a good knowledge base, but I don't have a lot of real-world experience yet. At the place I'm working with, we've already fixed some stuff, and they're starting to look a lot better. But what I'm seeing still makes me nervous. I know that there's a lot of places that aren't getting any help. Who maybe don't even know that they're vulnerable. 

But like I said, we're working with the DHS and CISA. They're going to start implementing policies nationwide that will set procedures and guidelines that will help these places with their security postures, and they'll be basing some small part of those policies on information I've collected. And in the meantime, I'm researching. I'm finding vulnerabilities and figuring out how to prevent them from being exploited. It feels good, being able to contribute to something that will help everyone. Even if I'm inexperienced, I'm getting better. And anything I find is being sent up the ladder, and I'm sure someone a lot better at this than me is taking what I'm finding and doing something with it.

I guess, if nothing else, that's something I'm learning from this. I can make a difference just by trying. I can help, even if I'm inexperienced. Because the only way to get experience is by trying, and that's what I'm doing. Maybe one day I'll be the one further up on the ladder, being pointed in the right direction by some kid who's just starting out. It makes me hopeful for my future. Even if I'm in a funk, I can look at the things I've done and be proud that I'm helping keep people safe, which is what I've wanted to do since day 1. And I'm starting to realize that whoever passes me up to do more stuff like this is missing out. I'm going to be an asset wherever I go. And sometime (hopefully) soon, someone is going to see that, and they're going to snatch me up before anyone else can. In the end, I'm helping people, and I know I'm valuable.

And that feels pretty good.

-- Cooper

I'm just going to keep this one short. Here's some Rust:
{%highlight Rust%}
fn main(){
    println!("Hello, World!");
}
{%endhighlight%}