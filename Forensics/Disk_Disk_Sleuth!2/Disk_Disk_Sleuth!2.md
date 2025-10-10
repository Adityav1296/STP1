## Disk Disk Sleuth! II
Author : Syreal

Category : Forensics

Difficulty : Medium

## Description
All we know is the file with the flag is named `down-at-the-bottom.txt`

## Solve 
**Flag:** `picoCTF{f0r3ns1c4t0r_n0v1c3_0ba8d02d}`

- Since a disk image was given, we have to find the flag by examining the disk image file. I had already downloaded the compressed file and then extracted it. Then I ran the `file` command on it. And then I listed the partitions present inside the disk image.

  partitions

- After that, I opened this disk image file in the Autopsy application provided by the Sleuth Kit Labs. In there, we can check the different files types based on their extensions. Since it is given in the desciption that it is a `.txt` file, we look for that. 
- Once I found the file, I opened it and the flag was given in the metadata of the file.
  
   pic
   pic
   pic
   pic

## Learnings
1. .img files are disk image files that are a digital copy of an entire storage device. These files are can be used to write the entire data of one device to another similar device.

## References
1. [Wikipedia: IMG(file format)](https://en.wikipedia.org/wiki/IMG_(file_format))
2. [Medium: Disk Image Deep Dive: Uncovering Hidden Flags in Digital Forensics](https://web-cipher.medium.com/disk-image-deep-dive-uncovering-hidden-flags-in-digital-forensics-27e744a38226)