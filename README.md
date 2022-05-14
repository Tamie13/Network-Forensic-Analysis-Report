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

After exporting the file june11.dll it was uploaded to VirusTotal.com for analysis
and the following was determined that **Googleipdate.exe** is classififed as
**Trojan Malware.**


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
