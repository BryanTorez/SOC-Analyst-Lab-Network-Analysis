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
To begin our analysis, we'll first head over to the 'Statistics' tab and click on 'Capture File Properties". We'll take a look at the first packet which in my case is in 2018 1127 at 8302 and then our last packet is at 9216 with a total elapse time of 42 minutes and 3 seconds do note that the first and last packet time will be local to your computer time this means that your time depending on where you're located or what your time zone your computer is set to may be different than mine but as long as you set the time display format to UTC you're okay the reason that we do this check is to ensure that the pcap that was handed to us is within the time frame although usess in a lab environment it is extremely useful in the real world so I want you to get into the habit of the first packet and last packet you don't want to be spending hours analyzing a peap and then finding out that the data is not even in that pcap: <br/>
<br />
<img src="https://snipboard.io/pDlmbJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/R57I0C.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
