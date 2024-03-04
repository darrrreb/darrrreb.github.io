---
title: THM Wireshark writeup
date: 2024-03-04
---
This is where I will writeup the 3 TryHackMe Wireshark rooms:
[ ] The Basics
[ ] Packet Operations
[ ] Traffic Analysis

Information on my TryHackMe journey is [here](https://darrrreb.github.io/2024/03/04/THM.html)

### Room 1 - The basics
###### Task 1: Introduction
This task gave a basic introduction of Wireshark and had 2 questions which could be answered by reading through the introduction. I was also prompted to start the virtual machine where I would be completing future tasks.
###### Task 2: Tool Overview
This task gave us a list of use cases for Wireshark, such as detecting security anomalies. It went on to teach us about the GUI of Wireshark, what each section means as well as detailing some features such as colouring, sniffing and merging.
The questions for this task allowed me to use Wireshark for the first time. 

The first required us to read the capture file comments, which can be found in Statistics -> Capture File Properties. Upon reading the comments for the whole file, the flag is revealed which is the answer to the question.

The second question asks us for the total number of packets in the file. This information can be found in the Capture File Properties, or at the bottom of the Wireshark window. I opted to look at the latter to find the answer.

The final question asked for the SHA256 hash of the exercise file. This, like the other answers, is found in the properties, upon copy and pasting the value in, I had completed the entire task.
###### Task 3: Packet Dissection
This task was all about the Details pane found at the bottom of the Wireshark GUI. The theory tells us that by clicking on a packet, we can see its details which is split up into the sections of the OSI (or TCP/IP) model. For each packet, there is information about the frame, MAC adresses, IP adresses, protocol and application protocol, which corresponds to the first 5 layers of the 7 level OSI model. The questions for this task involved looking at the details section to find information.

The first question asked me to look at packet 38, and find the markup language used under the HTTP protocol. I navigated to packet 38 and scrolled to the bottom of the details pane to find the application data. This is where I found the answer to this question.

The second question asked for the arrival date of the packet. I had to search a little for this, but found it quickly within the HTTP section under "date"

The third question asked for the TTL value, again, I just had to search the details pane for this combined with my knowledge of the OSI model and found the answer for this under Internet Protocol.

The fourth question required us to find the TCP payload size. I knew this would be located under the TCP protocol section, so I scrolled through it and found the value.

The final question asked for the e-tag value. This question was the hardest of the 5, as I did not know what an e-tag value was. After researching, I found out it was to do with HTTP response headers, therefore I checked the HTTP section of the details pane and sure enough, I was able to find the e-tag information.
###### Task 4: Packet Navigation
This Task included a lot of theory before the exercises. I decided to follow along with the theory as I read through this task to ensure that I knew exactly what was being talked about and to futher familiarise myself with the Wireshark GUI. The task taught me about finding packets using the search feature, navigating between packets, marking packets, packet comments, exporting packets, exporting objects, time display and expert info. The questions were relevant to all these new features I had been taught about

Question 1 required use of the search function to search for "r4w" and find the name of an artist. Using the search function revealed that r4w was just the start of the artists name, and the rest of the name could be found next to the search result.

Question 2 took me on an adventure to find the answer. Orignally, I had to check the comments of packet 12. The comments contained another task, to export the JPEG file in another packet and then get the MD5 hash for this JPEG. I located the packet and exported the file to my desktop. By running the MD5sum command of linux, I was able to copy down the hash, and paste it into the answer box.

Question 3 involved finding a .txt file in the file. I used the search function and searched for ".txt" but originally could not find it. However, after searching for a while I saw the relevant text file in the details pane. To see it in full, I exported the file and then viewed it with a text editor. This revealer text art of an alien, with a name underneath. This name was the answer to the question.

Question 4 was the simplest of the 4. I had to see how many warnings were present from the expert info. I went to Analyze -> Expert Information and the value was on my screen.
###### Task 5: Packet Filtering
This task talked over the variety of different ways the packets in a capture file could be filtered using Wireshark. Prior to this task, I did not realise that the Wireshark GUI was so powerful. However, I learned that many different queries can be generated just from clicking through the GUI. For example, by just clicking on a HTTP protocl in the details section, you can filter by all HTTP packets. I can very clearly see how the variety of filtering functions would help a lot in an investigation of network traffic. I was taught about apply as filter, conversation filter, colourise conversation, prepare as filter, apply as column, and follow stream. In the final set of questions I had to use these filters to get the answers.

For the first question, I had to filter by http, as described above
