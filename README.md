# Osint/Misc-miniCTF


### Challenge Group | OSINT/MISC | 2000 points

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

The results will be a URL of a chess game: `https://lichess.org/HSdduVhX`. 

For anyone who has played chess, you'll notice that this game is not a real game; it's random.

That's why we start checking for any information that can help us online. 

Searching `chess stego`, you'll find this [website](https://incoherency.co.uk/chess-steg/), and it needs the game moves to decode.

Lichess has its moves noted down below so you're good to go.
```
1. d4 b6?! { (0.00 → 0.90) Inaccuracy. Nf6 was best. } { A40 English Defense } (1... Nf6 2. c4 e6 3. Nf3 d5 4. cxd5 exd5 5. Bf4 c6 6. Nc3) 2. g4? { (0.90 → -0.33) Mistake. e4 was best. } (2. e4 Bb7 3. Bd3 e6 4. Nf3 c5 5. c3 Nf6 6. Qe2 d5) 2... Bb7 3. f3?! { (-0.25 → -1.30) Inaccuracy. Nf3 was best. } (3. Nf3 e6 4. c4 Nf6 5. g5 Ne4 6. Bg2 d5 7. cxd5 exd5) 3... h5?! { (-1.30 → -0.67) Inaccuracy. e5 was best. } (3... e5 4. h4 exd4 5. Qxd4 Nc6 6. Qa4 d5 7. Nc3 d4 8. Ne4 Be7 9. Bg2 Qd5 10. Bf4) 4. Bh3?? { (-0.67 → -2.73) Blunder. g5 was best. } (4. g5 d5 5. Nc3 e6 6. Bf4 Ne7 7. e4 Ng6 8. Qd2 Bb4 9. Nge2 dxe4 10. fxe4 O-O) 4... d6?? { (-2.73 → -0.23) Blunder. hxg4 was best. } (4... hxg4 5. Bxg4 e6 6. Be3 Be7 7. Qd2 Bh4+ 8. Kd1 Qe7 9. Bh3 c5 10. dxc5 Nc6 11. cxb6) 5. Qd3?? { (-0.23 → -2.28) Blunder. g5 was best. } (5. g5 d5) 5... Kd7?? { (-2.28 → 1.41) Blunder. hxg4 was best. } (5... hxg4 6. Bxg4 e6 7. h4 Rxh4 8. Rh3 Nc6 9. Be3 Rxh3 10. Nxh3 Nf6 11. Ng5 Nxg4 12. fxg4) 6. c4?? { (1.41 → -1.22) Blunder. g5+ was best. } (6. g5+ e6) 6... h4?? { (-1.22 → 2.05) Blunder. hxg4 was best. } (6... hxg4) 7. Nc3 Kc8 8. Qf5+ e6 9. Qxf7 Qe7 10. Qg6 c6?! { (2.67 → 4.16) Inaccuracy. Nc6 was best. } (10... Nc6 11. Be3) 11. Bg5?! { (4.16 → 3.03) Inaccuracy. g5 was best. } (11. g5 Na6 12. Bxe6+ Kb8 13. Nh3 Nc7 14. Nf4 Ba6 15. b3 d5 16. cxd5 Qb4 17. Bd2 Qxd4) 11... Qd7 12. Rc1 a6?! { (2.73 → 4.10) Inaccuracy. Na6 was best. } (12... Na6 13. e4 Kc7 14. Nge2 Re8 15. O-O Kb8 16. Be3 Nh6 17. g5 Nf7 18. f4 d5 19. cxd5) 13. Bf4 Ra7?! { (3.74 → 4.95) Inaccuracy. Ne7 was best. } (13... Ne7 14. Qc2 a5 15. g5 Kd8 16. e3 Na6 17. Nge2 d5 18. Na4 Nb4 19. Qb1 dxc4 20. Nxb6) 14. a3?! { (4.95 → 3.94) Inaccuracy. g5 was best. } (14. g5 Ne7 15. Qxe6 Qxe6 16. Bxe6+ Kc7 17. c5 Ng6 18. cxb6+ Kxb6 19. Bd2 a5 20. Bf7 Ne7) 14... Qe7?! { (3.94 → 5.82) Inaccuracy. Ne7 was best. } (14... Ne7 15. Qd3 Kd8 16. Ne4 Ng6 17. Be3 c5 18. Ng5 Rh6 19. Nxe6+ Qxe6 20. g5 Qf7 21. gxh6) 15. Bg2? { (5.82 → 3.51) Mistake. g5 was best. } (15. g5 Kd8 16. c5 Qe8 17. Qxe8+ Kxe8 18. cxd6 Bc8 19. Ne4 Kd8 20. Be5 Rf7 21. f4 Nd7) 15... a5?! { (3.51 → 4.60) Inaccuracy. Nf6 was best. } (15... Nf6 16. Bh3 Qe8 17. Qxe8+ Nxe8 18. g5 Nc7 19. Ne4 Kd7 20. Bg4 Be7 21. Nh3 a5 22. g6) 16. Nh3?! { (4.60 → 3.61) Inaccuracy. g5 was best. } (16. g5 Ba6 17. Bh3 Bxc4 18. Ne4 Bd5 19. Nxd6+ Kd8 20. e4 Ba2 21. Nc4 Nd7 22. Ne2 a4) 16... Kc7? { (3.61 → 6.15) Mistake. Nf6 was best. } (16... Nf6 17. O-O Ba6 18. Qc2 Rb7 19. d5 Bxc4 20. Ne4 exd5 21. Nxd6+ Qxd6 22. Bxd6 Bxd6 23. g5) 17. Rb1? { (6.15 → 3.38) Mistake. c5 was best. } (17. c5 bxc5 18. dxc5 Kd7 19. cxd6 Qe8 20. Qc2 Kc8 21. g5 Ba6 22. Ne4 e5 23. Qc5 Rb7) 17... Ra8?! { (3.38 → 4.81) Inaccuracy. e5 was best. } (17... e5 18. dxe5 dxe5 19. Be3 Nd7 20. O-O Ngf6 21. Qc2 Qf7 22. Ng5 Qxc4 23. b3 Qg8 24. Nb5+) 18. e3?! { (4.81 → 3.22) Inaccuracy. Ne4 was best. } (18. Ne4 e5 19. Bg5 Nf6 20. dxe5 Qxe5 21. Nxf6 gxf6 22. Bxf6 Qe6 23. Ng5 Qg8 24. Qe8 Bc8) 18... Ra7?! { (3.22 → 4.96) Inaccuracy. Nd7 was best. } (18... Nd7 19. Bg5 Qe8 20. Nf4 Ba6 21. Nxe6+ Kb7 22. Qxe8 Rxe8 23. Nxf8 Rxf8 24. Bf1 Rxf3 25. Be2) 19. b3?! { (4.96 → 3.24) Inaccuracy. Ne4 was best. } (19. Ne4 Qd7 20. c5 Nf6 21. Nxd6 Bxd6 22. cxd6+ Kc8 23. O-O Ba6 24. Rfd1 Nd5 25. Bg5 Nf6) 19... Qd7?! { (3.24 → 4.87) Inaccuracy. e5 was best. } (19... e5 20. Bg5 Nf6 21. O-O Nbd7 22. Qc2 Qe8 23. b4 Kb8 24. c5 axb4 25. axb4 Be7 26. Rfd1) 20. Ra1 Ba8 { Black wins. } 0-1
```

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

Long work but you need to have a methodology even in searching for infos.

Thanks.
