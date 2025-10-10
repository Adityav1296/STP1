## Disk Disk Sleuth! II
Author : Syreal

Category : Forensics

Difficulty : Medium

## Description
All we know is the file with the flag is named `down-at-the-bottom.txt`

## Solve 
**Flag:** `picoCTF{f0r3ns1c4t0r_n0v1c3_0ba8d02d}`

- Since a disk image was given, we have to find the flag by examining the disk image file. I had already downloaded the compressed file and then extracted it. Then I ran the `file` command on it. And then I listed the partitions present inside the disk image.

  <img width="942" height="335" alt="Screenshot 2025-10-10 140618" src="https://github.com/user-attachments/assets/a0c119f4-e535-47e5-aad9-a7110ea0ffe9" />

- After that, I opened this disk image file in the Autopsy application provided by the Sleuth Kit Labs. In there, we can check the different files types based on their extensions. Since it is given in the desciption that it is a `.txt` file, we look for that. 
- Once I found the file, I opened it and the flag was given in the metadata of the file.
  
   <img width="1709" height="960" alt="Screenshot 2025-10-10 135247" src="https://github.com/user-attachments/assets/68b36fc7-3e2c-4312-baa3-bb38df3467d2" />

   <img width="1705" height="521" alt="Screenshot 2025-10-10 135426" src="https://github.com/user-attachments/assets/bc68f1a4-70e8-4590-8477-d81a6c201d2b" />

   <img width="1709" height="545" alt="Screenshot 2025-10-10 135440" src="https://github.com/user-attachments/assets/b2cafef2-ad37-453f-a2d8-ea4a1c3f980d" />

   <img width="1709" height="978" alt="Screenshot 2025-10-10 135500" src="https://github.com/user-attachments/assets/8a2bbf84-dedd-4b63-bc6b-95d4f9f21386" />


## Learnings
1. .img files are disk image files that are a digital copy of an entire storage device. These files are can be used to write the entire data of one device to another similar device.

## References
1. [Wikipedia: IMG(file format)](https://en.wikipedia.org/wiki/IMG_(file_format))
2. [Medium: Disk Image Deep Dive: Uncovering Hidden Flags in Digital Forensics](https://web-cipher.medium.com/disk-image-deep-dive-uncovering-hidden-flags-in-digital-forensics-27e744a38226)
