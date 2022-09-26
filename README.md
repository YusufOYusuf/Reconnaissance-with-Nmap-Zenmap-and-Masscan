<h1>Reconnaissance with Nnamp, Zenmap, and Masscan</h1>


<h2>Description</h2>
In this lab I learned Nmap the “network mapper” and its usage to perform basic network
port reconnaissance and scanning. I also explored the GUI version, Zenmap, and
its benefits. I also compared these two to the speed of masscan. 
<br />



<h2>Environments Used </h2>

- <b>Kali GNU/Linux</b>
- <b>pfSense</b>
- <b>OWASP Broken Web App</b>
- <b>OpenSUSE</b>
- <b>Security Onion</b>

<h2>Program walk-through:</h2>

<p align="center">
Before I began, I needed to disable the Docker service on this machine as
it interferes with the lab. Failure to do so will cause a segmentation fault on consecutive steps. To disable the Docker service, type the command "systemctl stop docker": <br/>
<img src="https://i.postimg.cc/fRK0FPdB/Screen-Shot-2022-09-25-at-6-50-31-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  
  
  
  
  
<br />
Open and review Nmap’s manual by typing the command "man nmap" and then hit Q when finished:  <br/>
<img src="https://i.postimg.cc/2S2xsGLF/Screen-Shot-2022-09-25-at-6-53-27-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  




  
  
<br />
In the Terminal window, initiate a general Nmap scan on the OWASP BWA machine, with no options by typing command "nmap 192.168.68.12".: <br/>
<img src="https://i.postimg.cc/BQM0zWph/Screen-Shot-2022-09-25-at-6-57-26-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  

  
  
  
<br />
This time, initiate a specific TCP connect scan. Type the command "nmap -sT 192.168.68.12". :  <br/>
<img src="https://i.postimg.cc/CKKH481P/Screen-Shot-2022-09-25-at-7-01-13-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
 
 
 
 
 
 
 <br />
Nmap scans can be noisy at times with its default port scanning range. Limit Nmap to only scan the most popular ports by initiating the command "nmap -F 192.168.68.12":  <br/>
<img src="https://i.postimg.cc/QNWzG2b8/Screen-Shot-2022-09-25-at-7-04-33-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
 
 
 
 
 
 
 
 
 
  
<br />
Use Nmap to try to identify versions of software running on the ports. Type the command "nmap -A 192.168.68.12". :  <br/>
<img src="https://i.postimg.cc/BnFkmn61/Screen-Shot-2022-09-25-at-7-09-54-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
  
  
  
  
  
  
  
  
<br />
Nmap has a set of scripts installed we can use to test for vulnerabilities. Initiate the command "nmap -sC 192.168.68.12" to run a general set of default scripts:  <br/>
<img src="https://i.postimg.cc/BnckWQWL/Screen-Shot-2022-09-25-at-7-14-26-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 
  
  
  
  
  
  
  
<br/>
Nmap is a very powerful tool and in the right hands, you can script different scans and
work with the output. Zenmap is a GUI version of Nmap and allows you to get a better
visual representation of the same information.
<br />
Using the same Terminal window, open Zenmap by typing the command "zenmap" in terminal.:  <br/>
<img src="https://i.postimg.cc/sDcfmznm/Screen-Shot-2022-09-25-at-7-17-35-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 
   
  
  
  
  
  
  
 <br />
In the Target field, enter "192.168.68.12" and select Quick scan from the Profile dropdown. Notice the Command field and compare it to what I did in the last task. Click Scan to begin.:  <br/>
<img src="https://i.postimg.cc/jdLcRxG3/Screen-Shot-2022-09-25-at-7-20-17-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 
  
  
  
  
  
  
  
  
  
  <br />
In the Nmap Output tab, note the output is similar to the command I ran earlier.:  <br/>
<img src="https://i.postimg.cc/FRFSHpng/Screen-Shot-2022-09-25-at-7-23-03-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 
  
  
  




  
  
<br />
Click on the Ports / Hosts tab. Notice the clean, organized output.:  <br/>
<img src="https://i.postimg.cc/9MN6fWBm/Screen-Shot-2022-09-25-at-7-25-52-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 
  
  
  
  
  

<br />
Click on Scan menu and then click Save Scan. This allows you to save the scan information for use later.:  <br/>
<img src="https://i.postimg.cc/prJ1FRf5/Screen-Shot-2022-09-25-at-7-27-49-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 





<br />
You can also scan an entire network. In the Target field, type 192.168.0.0/24 and click Scan. Leave the Profile field set to Quick scan.:  <br/>
<img src="https://i.postimg.cc/TYh4wMy1/Screen-Shot-2022-09-25-at-7-31-49-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 




<br />
On the left, notice the additional hosts that were found. You may need to expand the column to see the full IP addresses.:  <br/>
<img src="https://i.postimg.cc/xTTcNgYc/Screen-Shot-2022-09-25-at-7-33-44-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 






<br />
Here's a picture of the hosts that were mapped:  <br/>
<img src="https://i.postimg.cc/zDwxGDXq/Screen-Shot-2022-09-25-at-7-36-13-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 






<br />
 Click on the Scans tab. Notice the second scan is not saved. If you saved prior
scans, you could load them in here, so you end up creating a database with all
the information collected. In our case, notice that all the information you
collected from both scans is combined.:  <br/>
<img src="https://i.postimg.cc/vZKJt8Vp/Screen-Shot-2022-09-25-at-7-38-42-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 





<br />
Masscan is labeled as the “fastest Internet port scanner,” capable of scanning the entire
internet in under 6 minutes. Open and review masscan’s manual by typing the command "man masscan". Hit Q to exit :  <br/>
<img src="https://i.postimg.cc/QCPQnzJx/Screen-Shot-2022-09-25-at-7-41-57-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 







<br />
Masscan also has many nmap-like features. In the Terminal window, review
these features by typing the following "masscan --nmap" command, press Enter, and review the
output:  <br/>
<img src="https://i.postimg.cc/4NgVnp20/Screen-Shot-2022-09-25-at-7-44-35-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 






<br />
To get started, let’s do a simple scan of the 192.168.0.0/24 LAN network in our
topology. We will only scan for devices that have port 80 open, using a TCP SYN
scan technique. Type the following "masscan -sS 192.168.0.0/24 -p 80" command, followed by pressing Enter: :  <br/>
<img src="https://i.postimg.cc/W1ZBSLwz/Screen-Shot-2022-09-25-at-7-47-19-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/> 











  
  
  
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
