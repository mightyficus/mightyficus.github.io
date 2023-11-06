---
layout: post
title:  "The Purpose of All This"
date:   2023-11-06 08:00:00 -0700
categories: jekyll update
author: Cooper Hopkin
---

I've always felt weird about blogs.

That's got to be surprising, right? I mean, I am currently writing a blog of my own free will and volition, even if it's about how weird blogging is for me. So if you're confused, don't worry about it, you're in good company. 

Part of why I'm doing this, though, is because I know it'll help me in the long run. I get to post my progress on projects, brag about accomplishments, and overall keep track of my wild trains of thought (trust me, there are several). And maybe keeping up a blog will forc-- I mean, persuade me to keep up with any projects I'm currently working on. Because sometimes I'll just... forget to work on a project. Or I'll get so busy with work and school that I won't feel like I have time to work on anything, then I'll sit on the couch doomscrolling on reddit or diving into a rabbit hole about creating a 8-bit computer from scratch (Which, interestingly enough, is actually a project I might do someday. I blame [Ben Eater][ben-eater] for that one). So maybe if I feel like I need to write about it, I'll actually do it.

That assumes I'll keep up with the blog posts, of course. I'm kind of really bad at that. I haven't ever been able to keep a journal going for more than a couple of weeks. My dad used to do it before he passed away from cancer (You should [read some of his posts][ben-blog], he was an incredible writer), and I have no idea how he did it. That man was a stirling example of sheer will. I'm biased, of course, but just about anyone who knew him would agree with me. He did what he wanted, and nothing would get in his way. Not even cancer.

So there it is. Hopefully I can write some blogs, keep up on projects, and learn something in the meantime. Maybe even teach someone else something new, even if they're only learning from my mistakes. Here's hoping.

-- Cooper 

I'm going to try to write a Hello World Program in a different language for each post. For easy languages, I'll make it unnecessarily complicated. This week will be python, my favorite language.
{% highlight python %}
def printPhrase(phrase):
    for chr in phrase:
        print(chr, end='')
    print()

def main():
    printPhrase("Hello World!")

if __name__ == "__main__":
    main()
{% endhighlight %}

{% assign image_files = site.static_files | where: "image", true %}
{% for myimage in image_files  %}
        {{ myimage.path }}
{% endfor %}


[ben-eater]: https://www.youtube.com/beneater
[ben-blog]: https://benfightstodd.blogspot.com/