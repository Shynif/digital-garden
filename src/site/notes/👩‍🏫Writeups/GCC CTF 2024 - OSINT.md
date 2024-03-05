---
{"dg-publish":true,"permalink":"/👩‍🏫Writeups/GCC CTF 2024 - OSINT/","tags":["Writeup","OSINT","GCC"]}
---

# Challmaker's OSINT *WU* ୧ ‧₊˚ 🍮 ⋅ ☆

## Music from the city
> One of the students in our school named Jean just dropped a new song 🎧
> ... but I can't find him somehow 😔 Can you find Jean's song?
> He's from the same city as our school, it shouldn't be hard to find him!

### Initial intel
- Jean
- Student
- From the same school as GCC
- He made a song
- Challenge tagged with *Sound*

> [!Chall-maker's NOTE]
> Ok I should have written "the same city as our CTF team". Everyone looked for our school *directly* and chose the other place where our school is located... Looking for Jean + Lorient instead of Jean + Vannes.
> 
> Second note, I changed the name of the man after testing. I used to be Marc, but I switched to Jean... There is a Jean doing music in our school... Oh no... Well I want to thank everyone who boosted his stats! You guys are amazing 💖
> 
> Last side note, as an excuse for tagging it as "Intro" difficulty, 3 testers all found it in under 20s (no jokes)

<br><br>
### Which city?
- Google "GCC ctf club"
- Check Twitter or "association page" or LinkedIn page

➡️ https://twitter.com/gcc_ensibs => Vannes, France
➡️ https://www.linkedin.com/company/gcc-ensibs/ => Vannes, Bretagne
➡️ https://www.helloasso.com/associations/gcc => exact location within a map (Vannes)

Many kept Lorient till the end. Reconsidering facts is really difficult for beginners and added way too much difficulty to the challenge. My apologies for it 😔

<br><br>
### Sound page?
Soundcloud or Bandcamp (or maybe a specific websites for music from cities)?

Let's start with the classic **Soundcloud**:
- search "*jean vannes*" or modify the search url https://soundcloud.com/search/people?q=jean&filter.place=vannes
- get 8 accounts
- https://soundcloud.com/jean_the_crepe_enjoyer

*Welp* sometimes you can't make the best challenges. Sometimes the search engine is just too powerful :/

> [!TIP]
> Many looked for the song. You have no intel about the song other than it exists and came out. Don't look for ghost.


---



<br><br><br><br>

## But they so tasty ... 😔🍰
>Our OSINT teacher, sir Staffengaouehll, joined us in class dead tired.
>Apparently he started running 👀
>Problem is, he didn't stop his bad habit of savoring **2 coconut flan slices almost everydays!**
>
>You alarmed him but he won't listen.
>  > "It's not **that** bad ???"
> Show him why he should watch out by giving him the amount of kilo Jouls he gets every time he eats his 2 flan slices!

### Initial intel :
- **Sport** ("running") + Tagged "Sport"
- *Food* ("**2 coconut flan slices**", "kilo Jouls")
- surname "**Staffengaouehll**"

> [!Chall-maker's note]
> Again, people were searching a bit too close to reality. Everyone looked for Staffengaouehll thinking it's a real identity. **So they looked for him in our school's teacher directory** 💀
> It's true that some CTFs use real IDs but take it as a fact at the start. The internet lies keep caution.

<br><br>
### Search for "Staffengaouehll"
- Google: ``nothing :/``
- Username search sites or scripts: ``nothing :/ (Well before someone created a skype account)``

Hmmmm really sneaky man. Let's go back to our intel. Let's search for Sport websites!
- Strava
- Apple health
- AllTrails
- Komoot
- Adidas Running
- ...

<br><br>
### Let's start with Strava! 🙂
We search and find [one account](https://www.strava.com/athletes/126771692)!!!

> [!CAUTION]
> https://www.strava.com/athletes/search behaves """weirdly""" (maybe blocking traffic not using a referer from Strava.com) and *blocks outsides queries*. Meaning we need to search **from within the site**, it is the reason why *most Username search engines get false positives searching Strava*.

But it is empty...
![Pasted image 20240304152215.png](/img/user/imgTypora/Pasted%20image%2020240304152215.png)
**Fun fact: Strava needs an account to ~~stalk~~ watch someone's activity :)**

So now we have one [running session](https://www.strava.com/activities/10136656435)!
![Pasted image 20240304152437.png](/img/user/imgTypora/Pasted%20image%2020240304152437.png)
*Hmmmmmm*
![Pasted image 20240304152450.png](/img/user/imgTypora/Pasted%20image%2020240304152450.png)
![Pasted image 20240304152510.png](/img/user/imgTypora/Pasted%20image%2020240304152510.png)

<br><br>
### Where do the ~~babies~~ 2 coconut flan come from ?
So, he spent a lot of time in a *supermarket*. It is not too far fetched (at least according to my chall's reviewer) that *he bought the flan from this supermarket*.

The supermarket is under the ``Carrefour`` franchise. No website or any information online can be found about flan slod in **this** specific supermarket in Theix.

There are *local promotion magazines* with no info about flan slices. BUT there is a search for available products in the *Drive* section! Tho I strongly advice not to use it as the *availibility* of a product in one specific supermarket is *very blurry* on purpose. They will mostly find your product available everywhere. Or maybe the contrary... This flan was marked as unavailable during the CTF and consequently had its info hidden 😮

So let's use the **main search feature**! We can search for "*flan*" and **jump from links to link** or directly translate in french "coconut flan" to search for "flan noix de coco"... the latter gives us nothing :/

Yeah sorry you need to search for "flan coco" instead... Just **jump from links to links.** 🐇

*✩°｡𓍢ִ໋Hello boyyyyyyy˚｡⋆˚*♡   https://www.carrefour.fr/p/gateau-flan-coco-3523680276581
![Pasted image 20240304153046.png](/img/user/imgTypora/Pasted%20image%2020240304153046.png)
> [!Chall-maker's note]
> Why this one? It's the only one with detailed nutritional values 🙂 **No guessing, it's OSINT**
> 
> The chall' was based on [another flan](https://www.carrefour.fr/p/flan-patissier-aux-oeufs-frais-carrefour-bon-app-3560070391011). An heavily industrial Carrefour branded flan version that had a nutritional table on the back of it. I kept it until they added the nutritional table to normal products 👀 then I switched.

<br><br>
### _Slaps flan_ This bad boy can fit so many _Jouls_
BrØther...
![Pasted image 20240304154019.png](/img/user/imgTypora/Pasted%20image%2020240304154019.png)

So, we have the calorific value in kJ for every 100g

We have the price for 2 slices

We have the price for 1kg of cocnut flan

**Math ?!?!**
For once you won't do trig' in OSINT but basic math! 😊💖
$${2,69 \over 6,90} \times {1000} \times {761 \over 100} \approx 2966.7 \space kJ$$

---


<br><br><br><br>


## Recap

Hope you had fun! The tickets don't tell the same story 😋 but afterward I got only positive reviews which is reassuring. Some have learned to *pay very much attention to initial intel*, to *not trust everything Google says*, to always reconsider the path you're on / reconsider not fully backed up facts.
As a chall-maker I learned a lot too! 📝 I need to make more precise challenge description to limit possible search ranges. I need to keep an eye on known intel and should always see my challenges with new eyes. It could lead to new perspective and approaches. And finally, I need to search myself for possible collisions with real world data, avoiding possible rabbit holes 🕳️🐇

​		***See you next time! (˵ ͡~ ͜ʖ ͡°˵)ﾉ⌒♡\*:･。.***

<p style="font-family:'Courier New',monospace;margin-left:70%">hey<br>ily<br>shy</p>




<br><br><br><br>


# Memes 🤡💖

O(1) < O(n) < O(n²) < O(n!) < O(wrong flags in OSINT)

![Pasted image 20240304153338.png](/img/user/imgTypora/Pasted%20image%2020240304153338.png)
Posted by K.L.M, stats **mid-CTF** (imagine at the end)

![Pasted image 20240304153421.png](/img/user/imgTypora/Pasted%20image%2020240304153421.png)
Posted by 𝕎𝑎𝑛𝑛𝑎𝐶𝑟𝑦


Imagine finding the solution for the challenge like this
![Pasted image 20240304153525.png|400](/img/user/imgTypora/Pasted%20image%2020240304153525.png)
Posted by Fabien