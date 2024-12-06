<h1>SOC Analyst Lab - Network Analysis (Malware) </h1>


<h2>Description</h2>
As a SOC analyst, you will eventually be required to investigate p-caps, AKA your packet captures. Packet capture is a networking practice involving the interception of data packets traveling over a network. Once the packets are captured, they can be stored by IT teams for further analysis. My being in all this is to prepare you for when the time comes. I'll continue to provide you with walkthroughs on how you can begin analyzing suspicious activity using Wireshark, a network protocol analyzer. In today's lab, we'll be going over the Blue Team Cyber-Range's 'Network Analysis-Malware Compromise' challenge assignment, which is listed under medium difficulty. Let's get started...


<h2>Applications Used </h2>
REMnux Malware Toolkit Website (https://docs.remnux.org/install-distro/get-virtual-appliance)
Blue Teams Labs Login Website (https://blueteamlabs.online/login)

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
Now once you're in Wireshark, the first thing you want to do is customize your columns and the time display format. I have mine already set up from previous labs, but I'm going to teach you how to do that. You want to first head over to view, and go under time display format. You want to select UTC date and time of day. : <br/>
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
Next, let's take a look at DNS since we saw that in our 'Protocol Hierarchy. So go back to Wireshark and let's type in DNS. Now we do see 'klychenogg.com', 'cochrimato.com', 'opendns.com', 'in-addr.arpa', and some other ones and that's about it. So the only new one is 'opendns.com'. I don't think that's anything of concern because if we take a look at what open DNS is, we can see it is a company providing domain name system resolution services with features such as fishing protection, optimal content filtering, and DNS lookups. Seems pretty normal to me. Going back over to Wireshark here, let's clear out the filter. If you recall on packet 911, the user downloaded a RAAR file. So let's go and take a look at that packet. So we see the get-request towards the RAR file over to the IP address of 95.1 1811 198.23. If we scroll down, we do see some back and forth communication towards the internal IP address and towards this 95 address. Eventually, we see some more traffic towards our 83 address and ooh on packet 123 we get a new IP of 185. 2441 15230 and this occurred on 163857 : <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
: <br/>
<br />
<img src="https://snipboard.io/SKWgji.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/t6dWjO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/296s5t.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
