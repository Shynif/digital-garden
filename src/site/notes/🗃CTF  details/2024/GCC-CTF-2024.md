---
{"dg-publish":true,"permalink":"/🗃CTF  details/2024/GCC-CTF-2024/","tags":["Wrap-up","Mid","Challmaker","GCC"]}
---

# GCC CTF 2024 🍻
Special format, I'll rate my challs one by one and will conclude at the end 😁

## Reverse
### Array programming rocks
I really liked that challenge. From the making to the maintenance it was amazing.
Reversing, what I call, "high level programs" is something I love in reverse engineering.
Reversing meta template C++, Compiled Python, Array programming languages, ... 💝

So for this chall I made a *UIUA* program, easy to reverse and especially easy to understand.
Problem is, **everyone one was scared af of it.**
There was ~45-50 solves so yeah it was easy as intended but people reversed it at the end. Even waiting for more challenges to come and finishing challenges from other categories 💀

I still see this challenge as a win. I don't mind people being scared of my challenges at first glance, if at the end I get positive reviews I take it as a big win. Happily it was the case here! 🥰💖


## Misc
### Legerdemain
**OK. I failed.** I pushed the wrong version of the challenge... So we did a *Revenge* and I pushed this time the latest version! (with also "f" banned just to see what challengers would come up with! And it was a fantastic idea!!!)

For the making I liked it. One thing, I had to remake it from scratch after I got my review! I will thank Drahoxx for it 🤗😈 it was very much needed, looking at it from my perspective right now! He advised me with his experience on how to make it better and I will definitely take it as a great lesson on chall making!

> "Make a real application *THEN* add a vulnerability to it" - Drahoxx

As of my understanding :
	➡️ It helps the players in the comprehension
	➡️ It guides the player with prior knowledge / expectations
	➡️ It structures the challenge
	➡️ It reassures the player and help him start the challenge
	➡️ It feels more rewarding when solved.
	("You found an exploit in X" more than "you exploit this and flagged")

Overall people where very happy. It was an easy Pyjail with a hecking lot of "movement" possible. There was as much vulns in the challenge as there are holes in swiss cheese 😋 Loved by beginner for its simplicity (a lot even thought their clever findings were the intended solution when there were many) and liked by pros for the feeling of quickly destroying and pwning it in a lot of different ways 👨‍💻
For every solve there was a new payload with a different technique!

My slides about the different solutions can be found [[👩‍🏫Writeups/GCC CTF 2024 - Legerdemain\|here]] ☺️🐍
Definitely the best part with such a pyjail with a broad range of exploit is the WU reading 💖📝
There are around 10 big mains exploits with 5 nice techniques that you should look at!



## OSINT
You can check both challenge writeups [[👩‍🏫Writeups/GCC CTF 2024 - OSINT\|here]]
### But they so tasty
I received some messages stating :
> "I would have posted a death treath but I just saw your write-up and I'm really impressed. Really learned a lot"

I think this challenge was the best I've made. Very original. People loved it. A complete bowl of fresh air in the nature of the information requested while staying in known grounds. Really a big win in my book.

The challenge description might need a remake to make it more beginner friendly but still I'm 100% proud of it.

I recently met amazing players at hackday 2024 Finals and well :
- "Hey this chall' makes me think of the GCC CTF 's OSINT challenges, there was one with a flan it was really fun and I learned a lot recently, idk if you participated or not?"
- "Hi I'm Shynif, challmaker for the OSINT challenges, very happy to meet you 🥰🤗🤝"

### Music from the city
OMG what a disaster!!! 😅😂
It was a Medium difficulty OSINT challenge hidden in a Intro trenchcoat!
3 testers flagged it in 10s-20s max, so I put it in Intro level but wow the description threw everyone off and *after reviews changes, even very very very small*, spiked up the difficulty. I "only" changed the name and removed the profile picture and well... I didn't verify for collision with the real world! Plus people didn't have full context from the description and it added very special OSINT techniques, hygiene and methodologies that beginner just don't have. (Backtracking mainly)
I discussed more in depth about it in the writeup!

By the way, *posting writeups in advanced, ready to be published*, was the best move. Everyone *needed* the answers and were so relieved to find them instantly posted 🤗💖 Also as a side note, memes based on the two challenges were absolutely hilarious! 😋


# Conclusion
There were some lessons learned! 😋
I improved my knowledges in chall making, especially *good challenge* challenge making.
This first experience went really well but some points are a reminder to still look after all my future work.
Challenge making is not an easy task and is a **balance of fun and challenging** that needs to be mastered on its own.

For next time I will give *more care to challenge descriptions*, maybe even ask someone else to write them for me!
And other key point to improve is *challenge ratings*. There were all off. Testing more isn't the solution as we saw in OSINT but definitely I should work on it a bit more and try to understand what a challenge rating really transcends and means.