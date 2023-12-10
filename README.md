# Osint/Misc-miniCTF

Here are the official write-ups for the OSINT miniCTF ISI:

### Challenge Group | OSINT | 5900 points

- [Young Prodigy - 500 points](#Young-Prodigy--500-pts)
- [Rap Battle - 500 points](#Rap-Battle--500-pts)
- [Meet #2 - 500 points](#Meet-2--500-pts)
- [Meet #3 - 500 points](#Meet-3--500-pts)

## Young Prodigy | 500 pts

### Task

In this edition, we are inspectors. The only information we have is the username `dr1zzyju1ce`.

### Solution

The challenge provides you with a username. The first natural step is to look that up on social media. 
You can do it manually or install [Sherlock](https://github.com/sherlock-project/sherlock) and execute the following command: `python3 sherlock.py dr1zzyju1ce`. 
There, you'll find a GitHub account with an interesting projects section, providing a hint on where to search next based on his profile picture.

The next step is to reverse search the image either with `Yandex` or `Google Images`. 
Scrolling through some articles will lead you to the [true story](https://afamily.vn/quy-tu-11-tuoi-gia-lam-hacker-roi-doa-tung-anh-nong-cua-bo-me-bat-ca-nha-nop-315-trieu-de-tieu-vat-20210205150850321.chn) of the guy and the city he's from, which is `Ghaziabad`.

And that's your flag: `Securinets{ghaziabad}`.

## Rap Battle | 500 pts

### Task

We have another username `sw1ft1eesw1ft` and need to find out where a meet is taking place.

### Solution

The search results give us a [Twitter account](https://twitter.com/sw1ft1eesw1ft).
We find a user URL id `31ddw65lujcwhd4shqsgtrnzd23i` and save it for later use. 
Now we need to find the "user's favorite website," which can be found by exploring the Twitter account and discovering that this user is engaging with Spotify-related posts.

Now we need to find the format of the URL to see the user's account. Clicking on your own profile, you'll find the URL like this: `https://open.spotify.com/user/sa6hw2f0j70354v0p138wklvw`. Replace the id we already got to get this URL: `https://open.spotify.com/user/31ddw65lujcwhd4shqsgtrnzd23i`.

Next, we can only find a playlist. Looking at its [content](https://open.spotify.com/playlist/424EqFwanMCT5g6lK6FieN),
it looks like a message: `Hey ya let's do this together. Let's meet soon. Come Here: Costumes, Layered, Lonely`.
and the location we're looking for is ciphered in these 3 words.

Searching for a 3-word location, you'll find this website [What3words](https://what3words.com/).

Next search with the 3 words you got to finally get the location, which is `cafe noir`.

Flag: `Securinets{cafe_noir}`.

## Meet 2 | 500 pts

### Task

We got a [file](file.txt) and need to find the second location of the meeting.

### Solution

When you first look at the file, you'll notice a lot of whitespaces, but they vary on each line. 
This is when you consider it could be a cipher. Taking that number to [dcode.fr](https://www.dcode.fr/cipher-identifier) will help you get some results. It's a [Whitespace Language](https://www.dcode.fr/whitespace-language) indeed.

The results will be a URL of a chess game: `https://lichess.org/HSdduVhX`. For anyone who has played chess, you'll notice that this game is not a real game; it's random.
That's why we start checking for any information that can help us online. Searching `chess stego`, you'll find this [website](https://incoherency.co.uk/chess-steg/), and it needs the game moves to decode.
Lichess has its moves noted down below so you're good to go.

You decode it to get the flag location: `isi_blocC_n404`.

Flag: `Securinets{isi_blocC_n404}`.

## Meet 3 | 500 pts

### Task

We got information that the next meet is hinted somewhere in a kaos pad or something like that.
The only available information is this URL id: `ro.iNgVO6a$W02`.

### Solution

The hunt starts with finding what kaos pad means. 
After some research, you'll come across this [chaospad](https://pads.ccc.de/), as it was quite popular back in the day. 

Again, using the same methodology, we need to find how the pads are shown. We try to create a new one to get the URL we are looking for: `https://pads.ccc.de/U9aRIe5YAn`. 
We change the id again, but this time we get this error: `Oops! A server error occurred. It's been logged. Please email <support@etherpad.com> if this persists`.

We poke around more on the website and try to share a pad to find that it's not the same URL format for read-only pads: `https://pads.ccc.de/ep/pad/view/ro.XJR3AU8u3rC/latest`. 
Now we can see the content of the [pad](https://pads.ccc.de/ep/pad/view/ro.iNgVO6a$W02/latest).

The person writing in it normally and suddenly deleted everything and pasted this paragraph:

```
Dear Decision maker ; Your email address has been submitted

to us indicating your interest in our briefing . We

will comply with all removal requests ! This mail is

being sent in compliance with Senate bill 2616 ; Title

1 ; Section 305 ! This is not a get rich scheme . Why

work for somebody else when you can become rich inside

55 weeks . Have you ever noticed nobody is getting

any younger & people will do almost anything to avoid

mailing their bills .

Well, now is your chance to capitalize

on this ! We will help you decrease perceived waiting

time by 140% and decrease perceived waiting time by

170% ! You are guaranteed to succeed because we take

all the risk ! But don't believe us . Mrs Anderson

of Indiana tried us and says "I was skeptical but it

worked for me" . We assure you that we operate within

all applicable laws . You will blame yourself forever

if you don't order now . Sign up a friend and you'll

get a discount of 10% ! Thank-you for your serious

consideration of our offer !
```
Again reading something this gibberish means only one thing. That it's a cipher!
We search spam cipher and you'll get [spammimic](https://www.spammimic.com/) where you can decode the spam text you get `mhamdia` as a result. 
Flag: `Securinets{mahmdia}`

Long work but you need to have a methodology even in searching for infos
Thanks.
