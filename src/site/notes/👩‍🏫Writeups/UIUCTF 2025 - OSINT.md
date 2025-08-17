---
{"dg-publish":true,"permalink":"/👩‍🏫Writeups/UIUCTF 2025 - OSINT/","tags":["Writeup","OSINT","UIUCTF"]}
---

# UIUCTF 2025 - OSINT ┻┳|･ω･)

## Mr. Blue Sky suite
### Mr. Blue Sky
> Mr. Blue Sky is your average go-lucky **BlueSky** user, but is there something more to his profile? See if you can find anything on [his profile](https://bsky.app/profile/mrbluesky1989.bsky.social)

Nothing special to note from the assignment so let's dive into this BlueSky account right away!

![Pasted image 20250817164823.png|300](/img/user/imgTypora/Pasted%20image%2020250817164823.png)
<center>mrbluesky1989 's BlueSky profile</center>
Let's do some simple checks 🧐

![Pasted image 20250817165506.png](/img/user/imgTypora/Pasted%20image%2020250817165506.png)

Do we have anything interesting ?
- Posts/Responses ❌
- Media/Videos ❌
- Starter kits ✔️ => *My Favorite Places on BlueSky* 🧐
- Lists ✔️ => *Bird Enjoyers* 🧐

If we look into the [*Bird Enjoyers*](https://bsky.app/profile/mrbluesky1989.bsky.social/lists/3ltgaktavzh2i) list we don't find anything interesting... other than very cute birbs pics 🥺💖

But if we look into the Starter kit [*My Favorite Places on BlueSky*](https://bsky.app/starter-pack/mrbluesky1989.bsky.social/3ltg7yccidn2t) we do find something interesting... 👀

![Pasted image 20250817170202.png](/img/user/imgTypora/Pasted%20image%2020250817170202.png)

Ok! Pretty easy challenge, let's keep on moving!

### Bad Blood
> Mr. Blue Sky is just trying his best to build a following, but he's been trying to *hide interactions* from a particular troll! See if you can find something on that *user's profile*.

#### Clues
Hmmm now we will need to find a profile interacting with our user Mr Blue Sky.

We can note:
- "*hide interactions*", maybe an answer was hidden ? Maybe deleted ?
- "*user's profile*", the flag will be on this bad guy's profile.

#### Finding the missing interactions
As we saw in the first challenge there is 1 post by Mr Blue Sky. Let's inspect that!

![Pasted image 20250817174134.png](/img/user/imgTypora/Pasted%20image%2020250817174134.png)

Look at that 🧐 **5** reposts we *can check* but **6** total linked to that post 👀

So now we have two paths:
- **Chad path**: look at the BlueSky API and get all the information needed.
- **Idiot Osinter path**: use a BlueSky post analyzer like [Romiojoseph's one](https://romiojoseph.github.io/bluesky/bluesky-post-analyzer), which also utilizes the API but all the work is already done for us

If we look at the 6 Replies/Quotes we find [this Quote](https://bsky.app/profile/16degreesofscorpio.bsky.social/post/3lspn7ri5z22t)

![Pasted image 20250817175620.png](/img/user/imgTypora/Pasted%20image%2020250817175620.png)

And on this profile we have our flag!

![Pasted image 20250817175852.png](/img/user/imgTypora/Pasted%20image%2020250817175852.png)

### BONUS: Bypass 2 challenges in 10 seconds
Ok you know in crypto we sometimes crack the challenge by using some known clear text? Usually the **flag format**. In our case it will be ``uiuctf{...}`` (maybe upper cased).

What happens if we look at what BlueSky knows about this flag format? 🙂

![Pasted image 20250817180238.png](/img/user/imgTypora/Pasted%20image%2020250817180238.png)

Well that was easy.

Why didn't the challmaker think about it? My theory is that they are too used to OSINT on Twitter.
Twitter wouldn't have found the accounts as the search feature is pretty limited (I believe on purpose) and you need some large analysis to do the same. But on BlueSky, the all mighty powerful API has a pretty broad search engine. Flags are nowhere safe 😈

### Age of Aquarius
> Now that we know about Mr. Blue Sky's troll, we can learn more about *her*. It looks like she's got a *birthday party coming up*, can you figure out *in which country (and province or state, if relevant)*?

#### Clues
We now need to find where 16degreesofscorpio (the profile previously found) was born. **Easy right?** 🙂

![subtle-foreshadowing.gif](/img/user/imgTypora/subtle-foreshadowing.gif)

What we know:
- She is a woman
- There will be information about her birthday party
- We are looking for a place

#### Digging for the birthday party
On 16degreesofscorpio's Bluesky profile we find two links:
- [A Tumblr account](https://www.tumblr.com/16degreesofscorpio)
- [A Tumblr page](https://16degreesofscorpio.tumblr.com)

There are many posts, people followed/following. [Take a quick look for yourself](https://www.tumblr.com/16degreesofscorpio), *it's a pretty good exercice to find meaningful information through the noise.*

Due to the sheer amount of data I won't go into details and will only show some interesting posts I deemed important, like:

![Pasted image 20250817182216.png](/img/user/imgTypora/Pasted%20image%2020250817182216.png)

Oh! So we just need to find more information about where this birthday party will be held and we will have our flag! So easy! 🙂

![Pasted image 20250817182338.png](/img/user/imgTypora/Pasted%20image%2020250817182338.png)

``July 22nd - 1 week - three days = math = July 12th``
Ok! Good to know!

![Pasted image 20250817182723.png](/img/user/imgTypora/Pasted%20image%2020250817182723.png)
<center>random post found scrolling the people 16degreesofscorpio follows</center>

Oh... Oh... Oh no... 😧
The... The chart... Oooh nooo*ooo* 😭

![Pasted image 20250817182930.png](/img/user/imgTypora/Pasted%20image%2020250817182930.png)

Well this chart will be useful 🙂(🔫)

Ok now we have two choices:
- Bruteforce all the possible rotations to find the exact location degrees and birth time that generated that chart on astro-seek.com
- Dig for more information

What I did during the CTF: none, I went to bed.

But for this writeup we will try to do the intended way and find more information to able to read the chart ⛏️👷

If we look online we find the signs and their symbols:
- ♈ => aries
- ♉ => taurus
- ♊ => gemini
- ♋ => cancer
- ♌ => leo
- ♍ => virgo
- ♎ => libra
- ♏ => scorpius
- ♐ => sagittarius
- ♑ => capricorn
- ♒ => aquarius
- ♓ => pisces

And from the exact same site that made the chart, astro-seek.com, we find a [reverse engineering of birth chart page](https://horoscopes.astro-seek.com/reverse-engineering-chart-astrology-online-calculator)!
It needs the following information to recover the birth date and **place**:
- Sun (☉)
- Moon (☾)
- Saturn (♄)
- ASC
- MC

Now let's try to read the chart and reverse it!

![Pasted image 20250817190744.png](/img/user/imgTypora/Pasted%20image%2020250817190744.png)

*Where moon?* Well no moon needed! If we [input these degrees and signs in the reverse calculator](https://horoscopes.astro-seek.com/calculate-reverse-engineering-chart/?znameni1_navrat=rak&znameni1_stupen=21&znameni2_navrat=kozoroh&znameni2_stupen=0&znameni2_minuta=00&znameni2_sekunda=00&znameni3_navrat=vodnar&znameni3_stupen=16&znameni4_navrat=stir&znameni4_stupen=16&znameni4_minuta=00&znameni4_sekunda=00&znameni5_navrat=panna&znameni5_stupen=7&znameni5_minuta=00&znameni5_sekunda=00&house_system=placidus), we get:
- birth date: **July 12**, 1992, 22:15:35
- birth place: **54°56’35’’N, 106°13’44’’W**

![Pasted image 20250817191324.png](/img/user/imgTypora/Pasted%20image%2020250817191324.png)

And voilà! We get our flag and astrology trauma forever! 🥰💖♋


---

## Geoguesser Suite
### park
> This picture was taken in a park. Find the name of the park.

We have this image given:
![park.jpg|500](/img/user/imgTypora/park.jpg)

If we do the classic search on [**Google Lens**](https://www.google.com/imghp) (also called *Google Images*) we get links to "Tegnérlunden, Stockholm" which is our flag.

![Pasted image 20250817194734.png](/img/user/imgTypora/Pasted%20image%2020250817194734.png)

### cherry_blossom
>I love *cherry blossoms*! But why is this one growing *indoors*?
>This picture was taken inside a *building.*

We have this image given:
![cherry-blossom.jpg|500](/img/user/imgTypora/cherry-blossom.jpg)

Oh! An *indoor fake cherry blossom*. The closeup is pretty weird but with *the structure, the railings and the car*, **Google Lens** should do the trick!

![Pasted image 20250817195339.png](/img/user/imgTypora/Pasted%20image%2020250817195339.png)

Hmmmm, nothing.
Let's try **adding keywords** ✨

![Pasted image 20250817195451.png](/img/user/imgTypora/Pasted%20image%2020250817195451.png)

So. We can try many different keywords but for me it did not work.

Well, if we can't filter by keywords, let's **filter on the image itself**!
We can select the structure part to have Google Lens focus on that!

![Pasted image 20250817202220.png](/img/user/imgTypora/Pasted%20image%2020250817202220.png)

![Pasted image 20250817202017.png](/img/user/imgTypora/Pasted%20image%2020250817202017.png)

Look at that! It's our structure with the same trees and railings!

If we click on the article we find that it is about the "Big in Japan" exhibition at the **Autoworld** museum in Brussels, Belgium.

> Note: If we still did not find anything. Another last resort trick would be using a VPN in the US (where challmakers are) to have the closest information from Google that the challmakers had when making and validating the challenge.



## Recap

Overall really fun OSINT challenges. It was a *fantastic introduction to BlueSky* and *a good Google Lens skill assessment*. I recommend that you try yourself and tinker with the challenges, it's pretty fun and you can stiffen your OSINT foundations a lot.

​		***See you next time! (˵ ͡~ ͜ʖ ͡°˵)ﾉ⌒♡\*:･。.***

<p style="font-family:'Courier New',monospace;margin-left:70%">hey<br>ily<br>shy</p>





