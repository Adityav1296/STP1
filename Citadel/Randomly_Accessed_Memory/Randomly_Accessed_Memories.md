# Randomly Accessed Memories

## Description
On your ascent to this floor, you hear these fragments being played back —

```
clone it, pull it, reset it, stage it, 
commit, push it, fork, rebase it. 
merge it, branch it, tag it, log it, 
add it, stash it, diff, untrack it … 
```

You look around and discover a chamber containing a vast archive of Daft Punk’s music, intertwined with cryptic commits left behind by other musicians. They seem ordinary at first glance, but not everything in the history is what it seems. The archive: https://github.com/evilcryptonite/daft-punk-archive

## Solve
**Flag:** `citadel{w3_4r3_up_4ll_n1t3_t0_g1t_lucky}`

- In this challenge, a github repository was given to us. So I checked that out and there were a number of text files given in it but on looking through the files, I didn't find anything point to the flag.
- So I checked out the commits. There, on the first page only, I found the following:

   ![alt text](<Screenshot 2025-10-19 182059-1.png>)

- Checking the commit, I found this small part of the flag:

   ![alt text](<Screenshot 2025-10-19 182127-1.png>)

- Since this was the third chunk of the flag, I looked further and found the other two chunks as well:

   ![alt text](<Screenshot 2025-10-19 182235-1.png>)


   ![alt text](<Screenshot 2025-10-19 182307-1.png>)

- Now since I got all the chunks, I used a base64 decoder and decoded each chunk to get the flag.