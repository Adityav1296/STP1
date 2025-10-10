## Bitlocker-1
Author : Venax

Category : Forensics

Difficulty : Medium

## Description
Jacky is not very knowledgable about the best security passwords and used a simple password to encrypt their BitLocker drive. See if you can break through the encryption!

## Solve
**Flag:** `picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1}`

- Since this time also we are given a disk image file, I started with opening it in the autopsy application. But as is mentioned in the description, it needed a password to open.
- Studying around a bit about bitlocker, I found that it basically encrypts a disk file to keep its content safe. It has two keys : 
   1. Full Volume Encryption Key (FVEK): This is the key that encrypts all the data on the drive. It is stored on the encrypted volume.
   2. Volume Master Key (VMK): This key is used to encrypt the FVEK. An attacker with access to the VMK can decrypt all data on the disk.
The password that we need to find gives us the access to this VMK and that's how we can open up the disk file.
- So with that in mind, I searched further and found that the password or the key to VMK is SHA-256 hashed. Therefore I first obtained that hashed value: 
   
   hash image

- Then I used the `hashcat` command and provided it with the widely known `rockyou.txt` password wordlist to decode the actual password.

   password decode image

- Once I got the password, I simply opened the file in autopsy and found the text document that contained the flag.
   
   flag

## Learnings
1. The disk image files are generally encrypted using bitlocker software to preserve their data and prevent its misuse.
2. It is possible to find the hashed key to VMK of the disk file and once that is found, the disk file can be accessed.

## References
1. [rockyou.txt](https://gitlab.com/kalilinux/packages/wordlists/-/blob/kali/master/rockyou.txt.gz?ref_type=heads)
2. [Medium: Bitlocker-1](https://medium.com/@erichdryn/bitlocker-1-picoctf-writeup-c0b5e4e3ec9b)