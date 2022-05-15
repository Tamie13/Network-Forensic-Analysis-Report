### Network Forensic Analysis Report



### Time Thieves

At least two users on the network have been wasting time on YouTube. Usually, IT wouldn't pay much mind to this behavior, but it seems these people have created their own web server on the corporate network. So far, Security knows the following about these time thieves:

*They have set up an Active Directory network.*
*They are constantly watching videos on YouTube.*
*Their IP addresses are somewhere in the range 10.6.12.0/24.*

- You must inspect your traffic capture to answer the following questions:*

    -  What is the domain name of the users' custom site?
       -  Filter: ip.addr==10.6.12.0/24
       -  Frank-n-Ted-DC.frank-n-ted.com  
    -  What is the IP address of the Domain Controller (DC) of the AD network?
       -  Filter: ip.addr==10.6.12.0/24
       -  10.6.12.12
    -  What is the name of the malware downloaded to the 10.6.12.203 machine?
       -  Filter:
       -  File = june11.dll   Name= Googleipdate.exe

After exporting the file june11.dll it was uploaded to *VirusTotal.com* for analysis
the following was determined:

1. The name of the malware was **Googleipdate.exe** and
2. It is classififed as **Trojan Malware.**

*Images below depict analysis using **VirusTotal.com and Wireshark** to get the information seen above. (To view in full screen click image)*

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Network%20Analysis%20Images/VirustTotal%20Findings.png" width="600" height="625"> 

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/Malware%20File.png" width="600" height="625">

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/Export%20Object%20Filter%20For%20File.png" width="600" height="625"> 

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/frank-n-ted.png" width="600" height="625">


### Vulnerable Windows Machine

The Security team received reports of an infected Windows host on the network. They know the following:
Machines in the network live in the range 172.16.4.0/24. The domain mind-hammer.net is associated with the infected computer.
The DC for this network lives at 172.16.4.4 and is named Mind-Hammer-DC.
The network has standard gateway and broadcast addresses.

-  Inspect your traffic to answer the following questions:

    -  Find the following information about the infected Windows machine:
       -  Host name: ROTTERDAM-PC
       -  IP address:  172.16.4.205
       -  MAC address: (00:59:07:b0:63:a4)

    -  What is the username of the Windows user whose computer is infected?
       -  matthijs.devries

    -  What are the IP addresses used in the actual infection traffic?
       -  IP Address: 172.16.4.205
       -  IP Address: 172.16.4.4
       -  IP Address: 185.243.115.84

*Images below depict analysis using **Wireshark** to get the information seen above. (To view in full screen click image/s)*

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/kerberos.CNameString%20and%20ip.addr%3D%3D172.16.4.0:24.png" width="600" height="625"> 

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/bootp%20Domain%20Name.png" width="600" height="625"> 

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Wireshark/Src:%20Mindhamer%20Dst:%20Rotterdam.png" width="900" height="625">

### Illegal Downloads

IT was informed that some users are torrenting on the network. The Security team does not forbid the use of torrents for legitimate purposes, such as downloading operating systems. However, they have a strict policy against copyright infringement.

-  IT shared the following about the torrent activity:

    -  Find the following information about the machine with IP address 10.0.0.201:
       -  Filter: ip.src==10.0.0.201 and kerberos.CNameString
       -  MAC address:  00:16:17:18:66:c8
       -  Windows username:  elmer.blanco
       -  OS version:  BLANCO-DESKTOP

    -  Which torrent file did the user download?# Network-Forensic-Analysis-Report
       -  ip.addr==10.0.0.201 and http.request.method==GET
       -  Betty_Boop_Rhythm_on_Reservation.avi.torrent

*Images below depict analysis using **Wireshark** to get the information seen above. (To view in full screen click image)*

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Network%20Analysis%20Images/ip.addr%3D%3D%20%26%26%20http.request.method%3D%3DGET%20(torrent).png" width="650" height="650"> 

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Network%20Analysis%20Images/Torrent%20%26%20Betty%20Boop.png" width="650" height="650">

Extra: Betty Boop Website Image Below

<img src="https://github.com/Tamie13/Network-Forensic-Analysis-Report/blob/main/Network%20Analysis%20Images/Betty%20Boop.png" width=" 600" height=" 625">
