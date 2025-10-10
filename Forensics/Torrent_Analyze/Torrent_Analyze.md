## Torrent Analyze
Author : Mubarak Mikail

Category : Forensics

Difficulty : Easy

## Description
SOS, someone is torrenting on our network.
One of your colleagues has been using torrent to download some files on the company’s network. Can you identify the file(s) that were downloaded? The file name will be the flag, like picoCTF{filename}.

## Solve
**Flag:**`picoCTF{ubuntu-19.10-desktop-amd64.iso}`

- To open the torrent.pcap file, we use a packet capture application such as Wireshark. Once opened, we enable the following protocols to search for torrent files : 

   ![Enabled Torrent Protocols](<Screenshot 2025-10-10 084349.png>)

- Now, searching for entries by applying these filters, we find a number of entries of `bt-dht` type with the ip address `192.168.73.132` occuring mulitple times. Therefore I assumed that this is the source address that we need to look for. 
- For a torrent file downloaded via a magnet link, the metadata is stored in the info_hash which is the SHA1 sum of the torrent file and is found in the bencode of the torrent files. Therefore, we use it along with the ip address that we found before as the new search filter :
   
   ![search results](<Screenshot 2025-10-10 094347.png>)

- We can see that all these files have the same source address and the same info_hash. Now, searching up the info_hash on a browser gives us the name of the file downloaded which is : `ubuntu-19.10-desktop-amd64.iso`

## Learnings
1. Wireshark application can be used to intercept packets and filter them based on protocols. We can also extract/view the desired packet data using this tool.
2. Torrent files can be downloaded via a http server or a magnet link. The files downloaded over magnet links have their metadata stored inside the info_hash of the file. 
3. The “infohash” is the SHA1 Hash over the part of a torrent file that includes:
   1. ITEM: length(size) and path (path with filename)
   2. Name: The name to search for
   3. Piece length: The length(size) of a single piece
   4. Pieces: SHA1 Hash of EVERY piece of this torrent
   5. Private: flag for restricted access
4. Bencode (pronounced like Bee-encode) is the encoding used by the peer-to-peer file sharing system BitTorrent for storing and transmitting loosely structured data. It supports four different types of values:
   1. byte strings
   2. integers
   3. lists
   4. dictionaries
The metadata files are bencoded dictionaries.

## References
1. [Wikipedia : Bencode](https://en.wikipedia.org/wiki/Bencode)
2. [StackOverflow : info_Hash](https://stackoverflow.com/questions/28348678/what-exactly-is-the-info-hash-in-a-torrent-file)
3. [CTF Handbook : Wireshark](https://ctf101.org/forensics/what-is-wireshark/)