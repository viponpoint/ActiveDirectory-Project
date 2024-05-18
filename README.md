# Active Directory-Project

# Introduction
 
The goal of this project is a start from nothing at all to a fully functional domain environment built on Prem. 
This project allows one to learn how to install and configure Active Directory, Splunk, Kali Linux, Sysmon, Windows machines, 
Atomic Red Team,  and Ubuntu Server.

To start this, I created my diagram and mapped out the building of  the lab logically along with the hardware requirements.
For this project, i used virtualbox to set up everything.
And for those that might asked, why the diagram, the main reason is to help understand how data might flow and how the pieces are strung up together. 

I used a total of two servers, one for splunk, and the other for active directory. Two computers, one target machine, and one attacker machine, and these were all installed using virtualbox. 

# Diagram
![Screenshot 2024-05-11 171331](https://github.com/viponpoint/ActiveDirectory-Project/assets/138403216/22837d67-26a9-40c8-95cf-09aa97858300)

## Objectives
Will provide more info about this below.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Advanced understanding of SIEM concepts and practical application.
- Development of critical thinking and problem-solving skills in cybersecurity.
- Proficiency in analyzing and interpreting network logs.
- Installation and configuration of Windows Server 2022
- Installation and configuration of Splunk Server
- Installation and configuration of Windows machine, splunk universal forwarder, sysmon, actomic red team. 
- Installation and configuration of Kali linux machine for the bruteforce attack using Crowbar.
- Understanding of forwarders (Universal and Heavy Forwarders) and configuring them to send data to the Splunk indexer.
- Initial configuration of Splunk, including setting up management ports, specifying directories for indexing data, and configuring Splunk to start at boot.
- Setting up and managing DNS, which is critical for AD operations.
- Installing the Active Directory Domain Services (AD DS) role.
- Promoting a server to a domain controller.
- Initial configuration tasks, such as creating the first domain in a new forest.
- Installation, configuration, and management of Windows Server operating systems.
- Enhanced knowledge of network protocols and security vulnerabilities.


### Tools Used
[Bullet Points - Remove this afterwards]

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Crowbar
- Splunk inputs.conf
  
## Steps
Our objective is to install our virtual machines on virtualbox. By the end of the installation, you should have one Windows 10 machine one Kali Linux up, one Splunk server, and one Windows Server 2022. Diagrams to follow


The objective is to install and configure both sysmon and splunk onto my Windows target machine and Windows Server so they can start collecting telemetry and send logs over to our splunk server. Diagrams to follow


The objective is to install and configure active directory onto my server, and then promote it to a domain controller, and finally configure the target machine to join the newly created domain. Diagrams to follow


The objective is to use Kali Linux to perform a brute force attack onto the created new users. By doing so, we will be able to see what this looks like by using splunk to query for this activity afterwards. Also, the set up and installation of atomic red team and then run a test using atomic red team to generate telemetry and detect similar attacks.
Diagrams to follow


## Splunk inputs.conf
Splunk inputs.conf

[WinEventLog://Application]

index = endpoint

disabled = false

[WinEventLog://Security]

index = endpoint

disabled = false

[WinEventLog://System]

index = endpoint

disabled = false

[WinEventLog://Microsoft-Windows-Sysmon/Operational]

index = endpoint

disabled = false

renderXml = true

source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational

