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
   
   <img width="934" height="770" alt="Screenshot 2025-10-10 183819" src="https://github.com/user-attachments/assets/046ce491-6b20-44d5-9744-31a6f4c840fb" />


- Then I used the `hashcat` command and provided it with the widely known `rockyou.txt` password wordlist to decode the actual password.

   <img width="942" height="716" alt="Screenshot 2025-10-10 183748" src="https://github.com/user-attachments/assets/c3352879-868c-4241-9a46-502482d2f56f" />

- Once I got the password, I simply opened the file in autopsy and found the text document that contained the flag.
   
   <img width="1704" height="730" alt="Screenshot 2025-10-10 183833" src="https://github.com/user-attachments/assets/78a5f15f-449f-4258-b846-e13aabc301db" />



## Learnings
1. The disk image files are generally encrypted using bitlocker software to preserve their data and prevent its misuse.
2. It is possible to find the hashed key to VMK of the disk file and once that is found, the disk file can be accessed.

## References
1. [rockyou.txt](https://gitlab.com/kalilinux/packages/wordlists/-/blob/kali/master/rockyou.txt.gz?ref_type=heads)
2. [Medium: Bitlocker-1](https://medium.com/@erichdryn/bitlocker-1-picoctf-writeup-c0b5e4e3ec9b)
