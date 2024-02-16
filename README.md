# Wireshark-network-PCAP-analysis-Lab-VM

## Objective


This Network Analysis Lab was aimed to impliment my Wireshark PCAP analysis skills and add onto my Cybersecurity job simulation that I completed on Forage for the company AIG. The Job simulation had to do with Apache Log4j Vulnerability within the company and I had to do tasks to Identify and look into the Vulnerability and using Python to bruteforce an encrypted password. With this hands-on Lab I can deepen my understanding on Apache Log4j and how it would look like in a PCAP/scenario, improve my network security, familiarize with attack patterns, and defensive strategies.

### Skills Learned


- Advanced understanding of Apache Log4j Vulnerbility.
- Proficiency in analyzing and interpreting a PCAP.
- Development of recognizing attack patterns and critical thinking/problem-solving skills in cybersecurity. 
- Enhanced knowledge of network protocols and security vulnerabilities.
- More expirence with malware analysis, (C2) and data exfiltration tecniques


### Tools Used


- WireShark for packet analysis PCAP or examining network traffic.
- VirusTotal to detect if IP was malicious or had a bad reputation.
- CyberChef to decrypt Base64 code.
-  GeoIP to map out the IP Addresses

## Steps

<p align="center">
Lab overview : <br/>
<img src="https://i.imgur.com/fg42cJE.png" height="80%" width="80%" alt="Lab overview"/>
<br />
<br />

AIG Cybersecurity Job simulation Overview, you can see which teams that are affected by this Vulnerability:  <br/>
<img src="https://i.imgur.com/z1Z09XF.png" height="80%" width="80%" alt="Set up network on DC VM"/>
<br />
<br />
This is the WireShark PCAP for the Apache Log4j vulnerability that I used: <br/>
<img src="https://i.imgur.com/vfG5Dea.png" height="80%" width="80%" alt="DHCP IPv4 network set up"/>
<br />
<br />

I started off by looking at endpoints to view the locations to see where the IP's are coming from. As you can see there are a lot of different source IP’s, which showed me that this was a distributed attack/scan coming from different places:  <br/>
<img src="https://i.imgur.com/d890etu.png" height="80%" width="80%" alt="enter the powershell on DC VM"/>
<br />
<br />
After taking a look at the endpoints, I checked the conversations to see who was sending/recieving the highest amount of packets to see a pattern. as you can see the IP address (198.71.247.91) had the highest :  <br/>
<img src="https://i.imgur.com/D7pRFcf.png" height="80%" width="80%" alt="Once the page is loaded use the link to access OpenVAS and use the username to log in"/>
<br />
<br />
I then applied a display filter for the IP address, As you can see in packet 444 Under the “POST HTTP”, it shows the user-agent “jndi” with a base64 code which we will focus more on:  <br/>
<img src="https://i.imgur.com/GGdMjoa.png" height="80%" width="80%" alt="Once the page is loaded use the link to access OpenVAS and use the username to log in"/>
<br />
<br />
After decrypting from base64, we can see what the malicious code was trying to do. I also entered the IP address into VirusTotal and as you can see other community members also identified it as malicious Log4 shell IP. This attack would allow the attacker to remote execute and access anything they want (Zoom in if needed, click on image) :  <br/>
<img src="https://i.imgur.com/hJr7sls.png" height="80%" width="80%" alt="Once the page is loaded use the link to access OpenVAS and use the username to log in"/>
<img src="https://i.imgur.com/wayNKUX.png" height="80%" width="80%" alt="Once the page is loaded use the link to access OpenVAS and use the username to log in"/>
<br />
<br />

Now what I want to see is if the server ever does a TCP “SYN”/ initiates the callback which would then allow the Apache Log4j exploit to occur which it did not :)  <br/>
<img src="https://i.imgur.com/eIv77Hc.png" height="80%" width="80%" alt="Once the page is loaded use the link to access OpenVAS and use the username to log in"/>
<br />
<br />
 That is the end of my project, thank you for checking this out! :)
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
*Ref 1: Network Diagram*
