# Selected Ambient Work

## Description
The symphonic adventure does not end here. On the next floor, a single song keeps echoing through the floor, repeating in a haunting loop. Amid the sound, you find a note left by a past candidate. It hints that the song holds a secret message, hidden in plain sight, much like how Aphex Twin concealed his face within his music with the help of spectrograms.

To move forward, you must find the message hidden in this sound.

Note: Separate the words in the flag with _ and make it UPPERCASE. Example: citadel{S3L3CT3D_AMB13NT_W0RK}

## Solve
**Flag:** `citadel{1_L0V3_1DM}`

- For this challenge, the description mentioned spectrogram which is basically used to visualize the signal frequencies. So I opened the file in a spectrogram to get some clue to finding the flag.
- While listening to the audio, it clearly contained a morse code which was being masked by another audio. So initially nothing really clicked until after observing the visualizer I saw that there were certain blocks being formed in it. 
- Those blocks turned out to be useful as I was able to find out the lowest and highest frequencies between which the morse code existed which was 659HZ to 784Hz. So setting those frequencies in the morse code audio decoder, I got the entire morse code message:

```
E IICHARD D JAMES AKA APHEX TWIN IS A BRITISH MUSICIAN, COMPOSER AND DJ ACTIVE IN ELECTRONIC MUSIC SINCE 1988 1 L0V3 1DM AND IS A PIONEERING FIGURE IN THE INTELLIGENT DANCE EMUSIC IDM GENRE.
```

- Now, earlier I had obsered that the spectrogram displayed the word citadel{} in the time interval from 1:00 to 1:12 minutes. So I found the message in that time interval and that was the flag for the challenge.