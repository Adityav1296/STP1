# Schlagenheim

## Description
Your quest continues, but you feel something odd about this room. The only artifact on this floor is a corrupted file held in the hands of a jet-black statue, frozen in the pose of a band mid-performance. The passcode to the next floor is hidden within this piece of music, but it can’t be played, as if the wrong extension has scrambled it.

You must take the corrupted file and repair it to reveal the true code that will unlock the door forward.

## Solve
**Flag:** `citadel{8lackM1D1wa5c00l}`

- For this challenge, since the description tells us that the file is scrambled with a wrong extension, the first thing I did was to use a hex editor to see if I can find some clue:

   ![alt text](<Screenshot 2025-10-19 193316.png>)

- This shows that the file is a M1D1 file, which is actually a MIDI file used for music production. Now, I looked up the magic bytes for MIDI files and set them up correctly and saved the file: 

   ![alt text](<Screenshot 2025-10-19 193339.png>)

- Using a MIDI player, I played the file and found the flag.