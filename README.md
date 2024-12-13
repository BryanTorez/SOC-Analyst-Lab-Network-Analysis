<h1>SOC Analyst Lab - Network Analysis (Malware) </h1>


<h2>Description</h2>
As a SOC analyst, you will eventually be required to investigate p-caps, AKA your packet captures. Packet capture is a networking practice involving the interception of data packets traveling over a network. Once the packets are captured, they can be stored by IT teams for further analysis. My being in all this is to prepare you for when the time comes. I'll continue to provide you with walkthroughs on how you can begin analyzing suspicious activity using Wireshark, a network protocol analyzer. In today's lab, we'll be going over the Blue Team Cyber-Range's 'Network Analysis-Malware Compromise' challenge assignment, which is listed under medium difficulty. Let's get started...


<h2>Applications Used </h2>
REMnux Malware Toolkit Website (https://docs.remnux.org/install-distro/get-virtual-appliance)
<br />
<br />
Blue Teams Labs Website (https://blueteamlabs.online/login)
<br />
<br />
Zui Website (https://www.brimdata.io/download/)
<br />
<br />
Wireshark Website (https://www.wireshark.org/download.html)


<h2>Walk-through Project:</h2>

<p align="center">
Over on Blue Team Cyber-Range, make sure you register for an account and once you're in you want to head over to the 'Challenges' section. From here, go ahead and search up "network analysis". What we want to do is click on 'Network Analysis - Malware Compromise', this one is listed as a medium difficulty. Finally, click on 'Start Challenge'. : <br/>
<br />
<img src="https://snipboard.io/qVoN7I.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/qnC8Mh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/PTmDz1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/0YVlSx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Taking a look at the scenario. 'A SOC Analyst at Umbrella Corporation is going through SIEM alerts and sees the alert for connections to a known malicious domain. This traffic is coming from Sarah's computer, an Accountant who receives a large volume of emails from customers daily looking at the email gateway logs for Sara's mailbox there is nothing immediately suspicious, with emails coming from customers. Sara is contacted via her phone and she states a customer sent her an invoice that had a document with a macro, she opened the email and the program crashed. The SOC team retrieved a PCAP for further analysis.' : <br/>
<br />
<img src="https://snipboard.io/VO2sFJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now this right here is a very realistic scenario that happens more often than you might think. Let's go ahead and download our file by clicking on 'Download File'. And then we'll extract the password, 'btlo'. On the desktop, I'll go ahead and extract it using 7zip. I'll type in "btlo" and now we have a new PCAP called 'traffic-with-dridex-infection'. So I'll open this up with Wireshark. And the first thing you want to do with Wireshark, assuming you already have Wireshark downloaded if you don't have Wireshark downloaded head over to 'Wireshark.org'. Click on "Get started". Then select either Windows or Mac OS depending on your operating system.: <br/>
<br />
<img src="https://snipboard.io/2npVhZ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Kxd5bJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ZI5FjS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/A1giB9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/9yxljp.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/3Bkeij.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/qGWtlF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now once you're in Wireshark, the first thing you want to do is customize your columns and the time display format. I have mine already set up, but I'm going to teach you how to do that. You want to first head over to view, and go under time display format. You want to select UTC date and time of day. : <br/>
<br />
<img src="https://snipboard.io/9lw1dL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Xv2Nds.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/YpP9fq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Then you want to customize your columns. To do that head over to 'Edit'. Click on 'Preferences'. Go over to 'Columns'. From here, you want to click on '+' and a new column will be created. You want to type in "Source Port" as the title. Under 'Type', double-click it and you want to select 'Src port (unresolved)'. Then do the same for 'Destination Port'. I'll go ahead and remove this since I already have a source and destination. If everything is good to go you should have a new column of 'Source port' and 'destination port'. The time is incredibly important because you'll want to report your findings in UTC to make it less confusing.: <br/>
<br />
<img src="https://snipboard.io/BpVCYx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/cpBi3r.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ai2El1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/sUJSfZ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Hn7wN8.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/tNfvXg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Pues0H.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To begin our analysis, we'll first head over to the 'Statistics' tab and click on 'Capture File Properties". We'll take a look at the first packet which in my case is on '2018-11-27' at '8:30:12'. Then our last packet is at '9:12:16' with a total elapsed time of 42 minutes and 3 seconds. Do note that the first and last packet time will be local to your computer time. This means that your time, depending on where you're located or what time zone your computer is set to, may be different than mine. As long as you set the time display format to UTC you're okay. The reason that we do this check is to ensure that the PCAP that was handed to us is within the time frame. Although useless in a lab environment, it is extremely useful in the real world. So I want you to get into the habit of the first packet and last packet. Since you don't want to be spending hours analyzing a PCAP and then finding out that the data is not even in that PCAP. : <br/>
<br />
<img src="https://snipboard.io/pDlmbJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/R57I0C.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Next, we'll want to check out the protocol hierarchy. So let's go over to 'Statistics' and click on 'Protocol Hierarchy'. Here we see what kind of protocols exist in this PCAP. So there is DNS, there's TLS and HTTP. Close this out. The next thing we want to take a look at is the conversations. So again, 'Statistics' then 'conversations'. Click on the 'ipv4' tab and we'll sort it by bytes, where the highest bytes are at the top. Looking at the top three conversations, we see our internal IP of '10.11.27.101' is communicating with three external IP addresses. The first starts with '95', the second '176' and the third, '83'. So let's put this in our notes. : <br/>
<br />
<img src="https://snipboard.io/lO3tdF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ixADah.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/LwHuI5.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/VBiuzN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/tDObVk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's take a look at the first entry of this PCAP. Under the 'Info' column, we see that there's a standard DNS query out to this domain here 'A klychenogg.com' and right underneath it we have 'response'. So what this means is that this particular domain 'A klychenogg.com' responded with an IP address of '95.181.198.231. If you recall, this IP is one of the top IPSs that we saw under the 'Conversation' tab. What we can do is go over to 'Virustotal.com'. Then we can just type in the domain and we see that 10 vendors is flagging this as malicious. : <br/>
<br />
<img src="https://snipboard.io/2rVRIy.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/V8uj4K.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Lp7C9P.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now let's go ahead and check the IP address. So this one is again '95.181.198.231'. So I'll go ahead and type in the IP address here in 'Virustotal.com.' and I'll hit enter. We don't see any vendors flagging this as malicious, but we do see that this IP is located in Russia. Now a question we can ask is, "Does our client do any business with Russia?" If the answer is no, we might be on to something. Let's go back over to our Wireshark. Now take a look at packet number six. Which occurred at '16:30:15'. We see our first HTTP get-request. I'll go ahead and right-click this. Click on 'Follow' and then 'HTTP stream'.: <br/>
<br />
<img src="https://snipboard.io/dCOaU0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Q8Cfib.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/2uB1KF.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/lTsRmu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/iAlFme.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Looking at the request, we see a file towards 'spet10.spr' at the top. The file response packet shows an MZ header right here. With the infamous string of "This program cannot be run in DOS mode." If you weren't aware, this is a Telltale sign of a portable executable. Such as a 'exe.' or a 'dll'. Let's go ahead and put that in our notes. : <br/>
<br />
<img src="https://snipboard.io/8s4zP7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/FeO5Bn.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/7IL3rx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Again this occurred at '16:30:15' at the top of Wireshark. I'll go ahead and remove the filter. Now let's scroll all the way back up here. What we can do is filter out specifically this '95' IP address and look for HTTP protocols. To do that I'll go ahead and right click the protocol of HTTP and then I'll click on 'Prepare as Filter' then 'Selected'. : <br/>
<br />
<img src="https://snipboard.io/IsYScw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/LagRlM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/l32apo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I'll right click the '95' address. Go over to 'Prepare as Filter' and then I'll '...and Selected'. Now looking at our filter, we see it automatically updated. So it's saying to look for the protocol of HTTP and where the IP destination. Which is this '95' IP address on the top. So let's go and hit enter. : <br/>
<br />
<img src="https://snipboard.io/qiw067.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/mAnR6M.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We see two results. So one which is is the packet six. Which is the one that we're already aware of. Then on packet 911, we see a get request to a RAR file. I'll right-click this. Click 'Follow', then click on 'HTTP Stream'. Again the request is towards a do RAR file, but looking at the server packet response we see a bunch of random characters. This doesn't really tell us too much yet, but let's just keep note of when this occurred. So this happened at '16:38:39'. : <br/>
<br />
<img src="https://snipboard.io/XIZ3OR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/6mGkIj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/s8rLhR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/KIFCVa.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/N3KgQ6.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/3qhH81.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
All right, now we want to take a look at the second IP address that was listed in our conversation. I'll go ahead and modify our query to look for the IP address of '176.32.33.108'. I'll go ahead and modify the query to 'ip.addr == 176.32.33.108'. Now you might be wondering why I am using 'ip.addr' and not 'Source' or 'Destination' and that is because I'm interested in this IP address as either a 'Source' or a 'Destination' and we can do this by using 'ip.addr'. Let's go ahead and hit enter. Let's scroll all the way up here. Taking a look at the first packet which is packet number 285 that occurred on '16:30:37' UTC time. We see our three-way TCP handshake 'SYN' and 'ACK'. : <br/>
<br />
<img src="https://snipboard.io/6XtbMs.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/zAg3Sj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/F9h2r7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
On packet number 288, we have our first HTTP get-request and it seems to be getting some kind of image. So let's go ahead and right-click. Click 'Follow' and then click 'HTTP Stream'. Looking at the request we see this '.avi' file on the domain of cochrimato.com. Let's quickly check that over on Virustotal. We have seven vendors flagging this as malicious. Going back over to our Wireshark, we see the IP address of the 176. So let's go ahead and check that on Virustotal. Just like the previous IP address, there are zero vendors flagging this as malicious and it is also located in Russia. : <br/>
<br />
<img src="https://snipboard.io/0c4djg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/NmYlfh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ced4Zp.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/EBTRZN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ubQD2C.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The next thing we want to do is take a look at the last IP address that we saw in the 'Conversations' tab. I'll type in 'ip. == addr 83.166.247.211'. Make sure that we're to the top. So the first packet was on 754 and this occurred at '16:31:52'. Looking at the traffic here just appears to be all encrypted traffic based on the TLs version 1.2. : <br/>
<br />
<img src="https://snipboard.io/ws9ID8.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We can take a look at the field called the SNI field, found within the 'Client Hello' packet. This will tell us what domain the internal IP is trying to access. We can filter for 'Client Hello' packets by selecting packet 757 which contains a 'Client Hello' as we can see under the 'Info' column. So it already has an SNI field called 'mautergase.com'. We can filter the 'Client Hello' by selecting the packet. Then expand our 'Transport Layer Security'. So go ahead and expand that. I'll expand the 'Handshake Protocol' and 'handshake type'. We see it as 'Client Hello'. So what we can do is right-click this, click on 'Prepare as Filter' and click on 'Selected'. Now we see all 'Client Hello' traffic, along with the SNI field.
<br />
<img src="https://snipboard.io/0bo3Ha.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/MsG4F8.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/9gtOub.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/OREj5G.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/pw8Ry4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now let's search this domain on Virustotal here. So there are two vendors flagging this as malicious. Let's search up the IP address next and I'm willing to bet that this is also located in Russia. Now two vendors flagging this as malicious: <br/>: <br/>
<br />
<img src="https://snipboard.io/RmJjW1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/0AtkpY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps">
<br />
<br />
<br />
<br />
Next, let's take a look at DNS since we saw that in our 'Protocol Hierarchy. So go back to Wireshark and let's type in DNS. Now we do see 'klychenogg.com', 'cochrimato.com', 'opendns.com', 'in-addr.arpa', and some other ones and that's about it. So the only new one is 'opendns.com'. I don't think that's anything of concern because if we take a look at what open DNS is, we can see it is a company providing domain name system resolution services with features such as fishing protection, optimal content filtering, and DNS lookups. Seems pretty normal to me. <br/>
<br />
<img src="https://snipboard.io/3HGpWM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/S7aBZq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/GRtkNh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/3ZhoKL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Going back over to Wireshark here, let's clear out the filter. If you recall on packet 911, the user downloaded a RAR file. So let's go and take a look at that packet. So we see the get-request towards the RAR file over to the IP address of '95.181.198.231'. : <br/>
<br />
<img src="https://snipboard.io/fr06NS.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/d7ejfx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
If we scroll down, we do see some back-and-forth communication towards the internal IP address and towards this '95' address. Eventually, on packet '1203' we get a new IP of '185.244.115.230'. This occurred at '16:38:57'. So TCPs handshakes both 'SYN' and 'ACK', we also get our 'Client Hello' but there is no SNI packet. What we can do is search on Virustotal of the address '185.244.150.230'. Where we'll then find five vendors are flagging this as malicious.: <br/>
<br />
<img src="https://snipboard.io/3ZCzxi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/prJGvi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/WgaP3T.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To help with this investigation we can use another tool called Zui. To download this tool, you can search on Google for "Brim Data Inc.". Go over to 'Download' and you want to download Zui. : <br/>
<br />
<img src="https://snipboard.io/mA4CTk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/b9R1Ko.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So with Zui downloaded, double-click that and what we can do is just drag our PCAP in. Once that's done you'll see a nice green check mark and select' Query Pool' on the top right corner. Now from here, we can begin querying our PCAT. : <br/>
<br />
<img src="https://snipboard.io/37AHjU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/P20Qly.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/4HVRy1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/0vGJEc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So what I can do is just type in 'alert' and then hit 'enter'. Now we see an alert here with also some SSL traffic. Still, I'm interested in any alerts that this particular PCAP had generated. So let's right-click the event type of 'alert'. I'll select 'Filter == Value'. So now I see 'event_type equal == "alert"'. Wow, we have 12 alerts. : <br/>
<br />
<img src="https://snipboard.io/sXMV0h.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/ZB3TzV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/LqFzKx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/P5UnFI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/gAIxYw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Looking at the source IP address, we see the new IP that we just identified which is '185.244.115.230'. (Just so you're aware, the time is the earliest at the bottom and the latest is at the top.): <br/>
<br />
<img src="https://snipboard.io/gAIxYw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/zpgYHM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
So let's look at the earliest event for this particular IP address. I'll go ahead and expand that. I'll also expand this alert field. Take a look at the signature, we have "ET MALWARE ABUSE.CH SSL Blacklist Malicious SSL certificate detected (Dridex)". : <br/>
<br />
<img src="https://snipboard.io/49lVsY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/RKx3Ch.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/LpDFz1.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Looking at the second one it appears to be the same signature. : <br/>
<br />
<img src="https://snipboard.io/JezLXl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/vXw3lj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/FENpDi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Expand the last one and that is also the same signature, but if we scroll down and look at the category it says "Domain Observed Used for C2 Detected".: <br/>
<br />
<img src="https://snipboard.io/gBNif4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Co3zJU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/wADSvL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now if we used Zui in the beginning and loaded this PCAP in, we would have immediately seen alerts that would be pretty interesting for us to Zone in. And this is why it's always good to have an IDS ready to go to take a look at any PCAPS that you feed it so we can see if it can generate any alerts. With that being said, we can say that this user is likely infected with the 'Dridex' malware. If we head over to our Wireshark we can export all of the downloaded files that the the user had downloaded. To do that, I'll go ahead and just remove the filter. Select 'File' at the top. Go over to 'Export Objects'. Select 'HTTP'. Now you can see all the files that are downloaded. : 
<br/>
<br />
<img src="https://snipboard.io/dwFIAT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/WtcBEo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Kaqzpt.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/A9NPsg.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Before you download all of these files, do make sure that you are in a virtual machine. Just in case you accidentally execute malware. I'll click on 'Save All' and let's create a new folder called Malware. I'll select that folder, and that's it. : <br />
<br />
<img src="https://snipboard.io/FsCnk4.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/17KYPv.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/bfXUqu.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/qGwe9m.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Let's head over to our malware folder and these are all the files that exist. What I can do is hold-shift then right-click and I'll open up a Linux shell here. I'll type in 'file *' and we can see that the 6.avi file has 'ASCII text'. We see 'MS Windows icon resource', 'data', and 'ASCII text'. We also see a portable executable which is the file that we observed earlier at the beginning of this PCAP. Finally, we can see another '.avi' that's another ASCII text. Now I can go ahead and just type in 'sha256sum' to generate a file hash for all of these files, but I wanted to show you how you can do this in Powershell; just in case you don't have WSL installed. Now if you wanted to install WSL, just type in 'wsl --install', but do make sure that you're running Powershell with administrative privileges. To generate a file hash for all of the files, you simply type in 'Get-FileHash *' then hit enter and that is it. We have all of the file hashes here. By default, it generates a 'sha256' hash.: <br/>
<br />
<img src="https://snipboard.io/mtWl5U.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/CAbXon.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/5PwDNM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/yTd2Iw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
We see 'MS Windows icon resource', 'data', and 'ASCII text'. We also see a portable executable, which is the file that we observed earlier at the beginning of this PCAP. Finally, we can see another '.avi' that is another ASCII text. Now I can go ahead and just type in 'sha256sum' to generate a file hash for all of these files, but I wanted to show you how you can do this in Powershell; just in case you don't have WSL installed. Now if you wanted to install WSL, just type in 'wsl --install', but do make sure that you're running Powershell with administrative privileges.: <br/>
<br />
<img src="https://snipboard.io/yTd2Iw.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/2UXaKt.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/YG6kRr.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
To generate a file hash for all of the files, you simply type in 'Get-FileHash *' then hit enter and that is it. We have all of the file hashes here. By default, it generates a 'sha256' hash.: <br/>
<br />
<img src="https://snipboard.io/sVXqA7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/v659jd.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Now we can go ahead and copy these file hashes and search on Virustotal to see if any of them exist. Searching the hash on Virustotal of the executable that was requested in the beginning, 60 vendors have reported this as malicious. Looking at the threat categories we have Trojan and spyware. Going over to the community, looking at the classification, we see this as 'ursnif'. Now I believe we have enough information to begin and answer the questions. : <br/>
<br />
<img src="https://snipboard.io/74RN1d.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/n9rcVx.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/KfvUlo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Heading over to the questions here. The first question is, 'What is the private IP of the infected host? 
<br />
Taking a look at the get-request. we see that the private IP is '10.11.27.25'.
<br />
The second question is, 'What's the malware binary that the macro document is trying to retrieve?
<br />
We saw that as 'spet10.sspr'. : <br />
<br />
<img src="https://snipboard.io/eFoRgm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/xkhjLM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/EDoXtm.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
Third question is, 'From what domain HTTP requests with GET /image/ are coming from?' 
<br />
So I can type in 'HTTP.request.method == GET'. This will show us all of the get-requests. We see the requests from images here, and we see the IP of 176, but I believe it was asking for the domain. So what we can do is right-click 'Follow' and then select 'HTTP Stream'. Now, we see the domain right here. So I'll type in 'cochrimato.com'. : <br/>
<br />
<img src="https://snipboard.io/gulpBk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Fuje60.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/tBahJU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/R5x14m.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/Rs91dM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The fourth question is, 'The SOC Team found Drideex, a follow-up malware from the Ursnif infection, to be the culprit. The customer who sent her macro file is compromised. What's the full URL ending in .rar where Ursnif retrieves the follow-up malware from?'
<br />
We can go back over to Wireshark. Type in 'http. request.method == GET'. Right-click packet number 911. Click 'Follow' and then click 'HTTP Stream'. Finally, copy and paste the raw file at the top of the page. You might ask, "How did I know it was HTTP?" Well if we go over to Wireshark, the protocol is HTTP and the port is '80'. So that's how I know. : <br/>
<br />
<img src="https://snipboard.io/rlQ9cU.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/3jVnOB.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/nA6W4j.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/nA6W4j.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/2Fr6W5.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
The final question is, 'What is the Dridex post-infection traffic IP address beginning with 185.?'
<br />
Thankfully, we used Zui. Which helped us identify this IP address. Which is '185.244.150.23'. Let's copy that head over to the questions and go ahead and paste that in. Now you've completed this lab!: <br/>
<br />
<img src="https://snipboard.io/JK4pa7.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/rYxbJj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/XNm3WG.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
I hope by following along you do feel a little bit more confident in your skills when analyzing PCAPS. As that is a skill that will benefit you going forward in your IT career. : <br/>
<br />
<br />
<br />
<br />
