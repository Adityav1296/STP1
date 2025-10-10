## Secret of the Polyglot
Author : SYREAL

Category : Forensics

Difficulty : Easy

## Description
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?

## Solve
**Flag:** `picoCTF{f1u3n7_1n_pn9_&_pdf_2a6a1ea8}`

- Using a hex editor we can read the initial magic bytes of the file which shows:

  <img width="857" height="162" alt="Screenshot 2025-10-09 182423" src="https://github.com/user-attachments/assets/c50ea8aa-b3c0-4596-b8b5-172f88cda66a" />


- Since the file is shown to be a png file, we first change the file extension to `png`. That way we can obtaing the first half of the flag : `picoCTF{f1u3n7_`
- After that, we can use the hex editor to change the initial magic bytes of the file to those of a pdf : `25 50 44 46 2D` and save the file. This time when we open it, we will get the second half of the flag : `1n_pn9_&_pdf_2a6a1ea8}`

## Learnings
1. Polyglot files are files that can be interpreted correctly as two or more different file types, depending on the application or program processing them. These files exploit the flexibility of file format parsers, allowing the same file content to be read and interpreted in multiple ways.
2. A file signature is a unique identification number seen at the beginning of a file. It tells you the file’s type and provides information about the data it contains. A computer uses it to determine how to read it or what application to use to open it. 

## References
1. [Wnesecurity : What are Polyglot files and how do hackers use them](https://wnesecurity.com/what-are-polyglot-files-and-how-do-hackers-use-them/)
2. [Wikipedia : List of file Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
3. [What is a File Signature? - Definition by ThreatDotMedia](https://threat.media/definition/what-is-a-file-signature/)

