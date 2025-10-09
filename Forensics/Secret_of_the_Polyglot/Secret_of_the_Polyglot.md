# Secret of the Polyglot
Author : SYREAL

Category : Forensics

Difficulty : Easy

## Description
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?

## Solve
**Flag:** `picoCTF{f1u3n7_1n_pn9_&_pdf_2a6a1ea8}`

- Using a hex editor we can read the initial magic bytes of the file which shows:

![Hex editor showing the initial magic bytes of the challenge file]("C:\Users\adity\OneDrive\Pictures\Screenshots\Screenshot 2025-10-09 182423.png")

- Since the file is shown to be a png file, we first change the file extension to `png`. That way we can obtaing the first half of the flag : `picoCTF{f1u3n7_`
- After that, we can use the hex editor to change the initial magic bytes of the file to those of a pdf : `25 50 44 46 2D` and save the file. This time when we open it, we will get the second half of the flag : `1n_pn9_&_pdf_2a6a1ea8}`

## References
1. [Wnesecurity : What are Polyglot files and how do hackers use them](https://wnesecurity.com/what-are-polyglot-files-and-how-do-hackers-use-them/)
2. [Wikipedia : List of file Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)

