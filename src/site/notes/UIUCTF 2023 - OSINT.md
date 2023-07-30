---
{"dg-publish":true,"permalink":"/UIUCTF 2023 - OSINT/"}
---

# UIUCTF 2023 - OSINT ┻┳|･ω･)

## Finding Artifacts 1: 50 points

> David is on a trip to collect and document some of the world’s greatest artifacts. He is looking for a coveted bronze statue of the “Excellent One” in New York City. What museum is this located at?
>
> **Hint 0:**
> The first two characters of the statue begin with "ma"
>
> **Hint 1:**
> It is very prevalent in southern Asia

### Our list of clues:

​	"Excellent One"; NYC; museum; coveted; bronze statue; "Ma..."; Asia

The Asian hint is pretty hard to find throught normal search so I chose `Google search for images`. By using some Google search tips like *"Excellent One"* to find a precise name and *Ma\** to find a statue name beginning with "Ma" we can find some interesting results :

<center>Searched: <b>"Excellent One" NYC museum bronze statue Ma*</b></center>

![image-20230703144410676.png](/img/user/imgTypora/image-20230703144410676.png)

<center>Searched: <b>"Excellent One" statue NYC</b></center>

![img](https://cdn.discordapp.com/attachments/1109186533854019664/1124652569843732510/image.png)



## What's for Dinner?: 50 points

> Jonah Explorer, world renowned, recently landed in the city of Chicago. He was spotted at a joyful Italian restaurant in West Loop. He uses a well known social network and loves documenting his travels and reviewing his food. Find his online profile.
>
> **Hint 0:**
> what does joy translate to?

I shortened the challenge's text to just what we need. We are looking for an *Italian restaurant in West Loop* with for only clue the importance of the word "joy". It is not far-stretched that Hint 0 asks us to translate "joy" in Italian so we get "*Gioia*".

By searching "**gioia italian restaurant chicago**" on Google we get only **1** restaurant, Gioia Chicago. **Jackpot !**

By clicking the first link for *Yelp.com* we find a 2 weeks old review from *Jonah E.*, our Jonah Explorer.

![image-20230703145704418.png](/img/user/imgTypora/image-20230703145704418.png)

![image-20230703145621391.png](/img/user/imgTypora/image-20230703145621391.png)







## Finding Jonah?: 50 points

> Jonah offered a reward to whoever can find out what hotel he is staying in. Based on the past information, can you find out what the hotel he stayed at was?

![chicago.jpeg|500](/img/user/imgTypora/chicago.jpeg)

So we need to find from what Inn in West Loop Chicago this picture was taken from... Let's fire **Google Earth** 🌎

![image-20230703150923795.png](/img/user/imgTypora/image-20230703150923795.png)

![image-20230703150934666.png](/img/user/imgTypora/image-20230703150934666.png)

Welcome to *West Loop*! On What's For Dinner I didn't tell anything but I spent a lot of time on this map. The hint for Gioia was really essential I suppose... If we come back to our challenge, we can spot **tall buildings only on the right edge of West Loop**.

We will try to spot theses "obvious" architectural elements from the given picture :

![image-20230703151236731.png|100](/img/user/imgTypora/image-20230703151236731.png) and ![image-20230703151254295.png|100](/img/user/imgTypora/image-20230703151254295.png)

Why theses? By looking on Google Earth there is ~4 antennas and ~2 round buildings. Let's find the needle ᕕ( ᐛ )ᕗ

![image-20230703151627560.png](/img/user/imgTypora/image-20230703151627560.png)

Luckily for us there is only **1** building that matches our search! (tall + oval on 2 side + right on 2 side)

![image-20230703151817690.png](/img/user/imgTypora/image-20230703151817690.png)

And then you see the big picture! ⊂◉‿◉つ

![image-20230703152228337.png|400](/img/user/imgTypora/image-20230703152228337.png) ![image-20230703152348180.png|250](/img/user/imgTypora/image-20230703152348180.png)

![image-20230703153237995.png](/img/user/imgTypora/image-20230703153237995.png)

When we have had enough fun we can flag by looking up the hotel name on Google map ʕ༼◕ ౪ ◕✿༽ʔ



## Jonah's Journal: 50 Points

> Jonah took notes into an online notebook and pushed his changes there. His usernames have been relatively consistent but what country is he going to next?
>
> **Hint 0:**
> forks, trees, pushing, and pulling

Well there is only one app with forks, trees, pushing and pulling... Let's go on Git, starting from Github!

<center>https://github.com/JonahExplorer</center>

![image-20230703154828851.png](/img/user/imgTypora/image-20230703154828851.png)

![image-20230703154913728.png](/img/user/imgTypora/image-20230703154913728.png)

Sooooo*ooooooooo* :

- it's our Jonah
- Nope China isn't the flag
- Flight UA5040 is an inland flight to Pennsylvania
- 2 branches ...

![image-20230703155202736.png](/img/user/imgTypora/image-20230703155202736.png)

Hmmm...

![image-20230703155230535.png](/img/user/imgTypora/image-20230703155230535.png)

2 commits ahead ...

![image-20230703155327726.png](/img/user/imgTypora/image-20230703155327726.png)





## First class mail: 50 Points

> Jonah posted a picture online with random things on a table. Can you find out what zip code he is located in?
>
> **Hint 0:**
> I think code is cool

![chal.jpg|500](/img/user/imgTypora/chal.jpg)

So this challenge is *pretty* easy if you skip ALL the random bullshit. Here is a list of *some* very deep rabbit holes you can fall in and waste hours on :

- Trying to cross data from the different elements:
	- Lanyi Insurance, a local Erie Insurance from Pennsylvania ... Nope
	- Apple products? iPad, AirPods, iPhone 11 (used to take the photo)
	- Beloved hand lotion ... owned by Unilever ... ok ?
	- Aloys Schmitt 's *preparatory exercices for the piano* ... Nope, no big music stuff in Pennsylvania
	- Edwin Land biography, inventor of the polaroid technology and the eponym company ... Nope
- Trying to find more deep information about other elements (that freaking block calendar!)
- Trying to relate everything to Pennsylvania
	- ... Because the Flight UA5040 goes to Pennsylvania
	- ... Because the challmaker doxxed himself and lives in Pennsylvania
- Trying to use the challmaker's real zip code. **Remember to clean your f-ing metadata. It's OSINT >:**(

After all of that you can search this ![image-20230703161358231.png|200](/img/user/imgTypora/image-20230703161358231.png) on Google and find it's a **[POSTNET](https://fr.wikipedia.org/wiki/Postnet)** code

Translated it's: ``0100110011110011100111110011100111001101011001101100``

You can use Wikipedia's table to decode the number or just throw it to Dcode  “ψ (｀∇´) ψ

![image-20230703162137647.png](/img/user/imgTypora/image-20230703162137647.png)





## Recap

It was a really fun and diversified capture the flag OSINT-wise. We had fun exploring reviews, maps, social networks and discovering nice ways to hide some stuff to the naked eye. Most importantly we learned to always keep looking and to clean our goddamn metadata!

​		***See you next time! (˵ ͡~ ͜ʖ ͡°˵)ﾉ⌒♡\*:･。.***

<p style="font-family:'Courier New',monospace;margin-left:70%">hey<br>ily<br>shy</p>





