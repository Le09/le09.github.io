---
title: "my Linux journey"
order: 10001
date: 2026-04-12
first_posted: 2026-04-12
edits:
---

_I became a Linux user the day I spent more time trying to launch a game than I would ever spend playing it._

## University: introduction to the bazaar OS

I was not born a Linux user.
My first encounters with Linux were in university.
All labs were on computers running Linux, but many labs were on wildly different environments: some computers were running GNOME, others were running KDE, with a different set of default applications installed (I did not get a perfect score on an assignment because the lab test was on KDE, which was the first time I used it, so I wasn't able to type everything fast enough).

First-year students had to follow 5 lab sessions to discover Linux (starting long after the first labs on Linux started).
However, these lacked any relevance to any practical use: we had a few hours on `make`, while we never had to compile anything in C longer than a few lines in a `main` to define a sorting algorithm and print an array.
The other courses were in Java, and people would recommend using Maven anyway.

There was one on the command line, but it was similarly lacking context.
The weirdest thing is that this course presented the CLI as the only way to interact with a computer.
By the end of the afternoon, I was bewildered: what was the point of this, when I can just open the folder in the file manager? 
It was before we were introduced to servers, and months before OS 101.

There's a very famous essay called "The Cathedral and the Bazaar", by Eric Raymond.
It argues that proprietary software is like a cathedral, with planning decided top-down by the company management, while open-source software is like a bazaar. 
Its actors can communicate, but they are independent agents with their own approach and their own goals.
What results is a self-organized system with its own efficiency.
The metaphor applies to almost every aspect of the OS: there are dozens of desktop environments -- the flashy UI that is the first thing you see -- while Windows or Apple has only one, that is barely configurable.

## The evangelist

It was a friend who was extremely busy with his first year of medical school who proselytized every time we met.
He was obviously overwhelmed and built his own intellectual garden to make it through the experience.
He was the one who got me to read "The Cathedral and the Bazaar"; for him, this essay was a glimpse into a better society, so it was a mandatory reading.
He also made me read Richard M. Stallman's _Free Software, Free Society_, and gifted me a copy of O’Reilly's _Running Linux_.

It left important seeds: every "IT" or "computer" problem would be seen through a broader perspective, including societal and political implications.
That was still not enough to convert me fully, as I did not foresee how much computers would eat the world.
Pretty ironic that he got totally infected by the Linux virus while I couldn't really care either way, despite the university courses where Linux was pushed a lot more.

## Automate all the things

On the side, I was discovering how to automate things on Windows to speed up my process.
I was translating a book, and so I wrote a few Windows scripts glued together by an `.hta` "interface" to launch my work environment, check dictionaries, etc.
I wanted to automate every step that was a bit time-consuming, and obviously a mechanical task.

This is where the first crack showed in Windows. 
A few games, either after they stopped or crashed, would not restore the desktop resolution. 
Instead of 1920x1080, I would get 1360x768, and the mouse would be 2x2 pixels big.
Fixing that meant that you had to go 2 or 3 times menu down the control panel, select the obviously correct option among 12 stupid ones, click, wait 3 seconds, then click "yes I'm sure". 
That drove me mad.
I searched everywhere, but there was no proper command to do that.
There was obviously something wrong: this was long and painful, but the OS didn't give you any way to do that?
I discussed with a few people, and all the solutions they had were extremely hacky and disgusting.
Like to use VBScript to send keystrokes to the Windows Display Settings dialog. 
Are these people serious???

## Difficult beginnings: unfriendly hardware

Linux has the best CLI-first experience; it's in its DNA, coming from its Unix philosophy heritage. 
Every automation step would generally translate as a simple command.

But there was a big problem preventing me from switching to Linux.
My first laptop already had its 4 available partitions --MBR only allowed that many-- used by the system and its backup files.
I was too afraid to brick my laptop, as I definitely needed it for university.

So, I first started with Wubi, short for Windows‑based Ubuntu Installer.
It allowed you to install Ubuntu inside Windows (XP/Vista/7) around the late 2000s without partitioning your disk.
But that was not really a proper solution that gave Linux a chance either; the experience was a bit gimped.

Then, it was Poulsbo. Behind that horrible name hid horrible problems.
This is the GMA500 video hardware driver.
I got Linux to run on an ultraportable, but the experience was not very smooth.
It required a lot of tweaks, and even then there were still problems.

The usability experience was generally good.
The default applications, by 2008, were already quite mature, and did a good job on most productivity front.
For the work I had to do, Latex and compilers were simply better than on Windows. 
And all of this was free, without risks of viruses due to shady cracks of essential software. 

What marred this experience was that I basically tried to use Linux on hardware that was hostile to it, so support was only as good as it could get through the hard-work of the community.
But it gave a scary impression, as I was not sure that would not be blocking when I would really depend on the system.
It required also to handle 2 systems, to interrupt work to switch from one to the other. 
A lot of mental overhead and maintenance work.

## the last excuse collapses

Ultimately, the reason I still ran Windows was to run games. 
"LiNuX hAs no gaems", as the meme goes. 
I never considered myself a gamer, but I still wanted to be able to run Guilty Gear XX, and still be able to run one or the other when I felt like it.  

But one day, I spent a few hours trying to get a game to run (it was "The Ball", not that it is very relevant).
I can't say whether it was two or four hours, but it was very frustrating to debug the problem that caused the crash.
A terrible realization dawned on me: I would barely play half an hour of that game anyway, I just didn't have time for it.
So why would I lose time battling to run something that I wouldn't care for? Wasn't I just chasing the high that video games could produce as a child, without any hope for it to materialize?
I had nothing to lose by embracing Linux fully.

## Radicalization

Without ideological bias, Windows was simply restricting my agency.
While I still wanted to use Windows, I made excuses for everything that I found wrong with it.
But managing the system in parallel showed how much more maintenance it requires, how complicated it is, and how resistant it is to efficiency.
However, you get it pre-installed, on officially supported hardware, and you got to learn it through cultural osmosis. 
In a world where you would start on Linux, every step would be so jarring that Windows would be a hipster oddity.
I felt duped; all of my pre-conceived beliefs were Windows propaganda! 
At this point, I tried to remove any dependency on proprietary systems in general, and that became as obsessive as it was for my friend.

It took a few years to swallow that bitter pill, and get back to normal: Linux is simply the most practical, easy choice, and it aligns with my values.
Linux is just solid, the natural choice if you simply want a working OS to focus on your actual work, while Windows is restricting your agency.

## The real world: Linux is autonomy

Funnily enough, by giving up games and other "Windows-only" software, I got everything.
Steam embraced Linux, so I got to use a good system and have one-click installs for games I can enjoy when I have time. 
There isn't anything I miss from my system. 
All improvements and speedups work how I like them, my Wacom tablet works flawlessly, the system looks how I like it.

Nowadays, it is very hard to function in society without depending on a proprietary system -- no Apple, Microsoft, or Android.
I've made a lot of compromises that my younger self would not have accepted because how of barely sustainable these choices would be. Yet, that shows that the fight is more important than ever.
