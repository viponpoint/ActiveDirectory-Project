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
The primary objective of setting up this Active Directory project is to create a comprehensive, realistic, and controlled environment for learning, testing, and improving cybersecurity practices. Specifically, this project aims to:

Build and Secure an Active Directory Environment:
Install and configure Active Directory on a Windows Server to establish a robust directory service infrastructure.
Add Windows client machines to the Active Directory domain to simulate a real-world enterprise network.

Implement Advanced Monitoring and Logging:
Deploy Splunk Universal Forwarder to collect and forward logs from Windows machines to a central Splunk server for analysis.
Install Sysmon on Windows clients to provide detailed event logging, enhancing the ability to detect and analyze suspicious activities.

Simulate Attack Scenarios and Test Defenses:
Utilize Atomic Red Team to simulate a variety of attack techniques and tactics used by adversaries, testing the resilience of the Active Directory environment.
Deploy Kali Linux to serve as a penetration testing platform, executing various security assessments and vulnerability exploits.

Set Up Supporting Infrastructure:
Configure an Ubuntu server to host additional tools and services required for the project, providing a versatile platform for various security operations and integrations.

Conduct Brute Force Attack Simulation:
Use Crowbar on Kali Linux to perform brute force attacks against the Active Directory environment, specifically targeting user accounts and passwords to evaluate the effectiveness of password policies and account lockout mechanisms.

Enhance Incident Response Capabilities:
Monitor and analyze logs using Splunk to detect and respond to the brute force attacks and other simulated threats.
Develop and implement incident response strategies based on the detection of simulated attacks, improving overall security posture and response times.

Improve Security Skills and Knowledge:
Gain hands-on experience with a variety of cybersecurity tools and techniques.
Understand the integration and interaction between different security components within an enterprise network.
Enhance knowledge of attack vectors and defense mechanisms through practical application and testing.

Document Findings and Best Practices:
Generate detailed reports on the setup, configuration, attack simulations, and responses.
Develop best practices for securing Active Directory environments based on the outcomes of the project.

Conclusion
By setting up this comprehensive Active Directory project, the objective is to create a controlled and realistic environment that allows for thorough testing of security measures, improvement of monitoring and incident response capabilities, and the enhancement of overall cybersecurity skills. This hands-on experience for me is invaluable for understanding the complexities of enterprise security and preparing for real-world cybersecurity challenges.

### Skills Learned

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
- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Windows Server 2022 was used to install and configure Active Directory, which serves as the primary directory service for user and computer management within the domain.
- Windows 10 Client Machine was used to act as domain-joined client machines for testing user authentication, policy enforcement, and monitoring.
- Active Directory Domain Services (AD DS) was used to manage domain resources, user authentication, and policy enforcement within the Windows Server environment.
- Splunk Universal Forwarder was used to collect and forward log data from Windows machines to the Splunk server for centralized log analysis.
- Sysmon (System Monitor) was used to provide detailed event logging on Windows machines, capturing high-value security event data.
- Kali Linux was used to serve as a penetration testing platform, executing various security assessments and vulnerability exploits against the network.
- Crowbar (Brute Force Tool) was used to perform brute force attacks against services such as RDP, SSH, VNC, and others, specifically targeting Active Directory credentials.
- Splunk inputs.conf
  
## Steps
The objective is to install virtual machines on virtualbox. By the end of the installation, i had one Windows 10 machine, one Kali Linux up, one Splunk server, and one Windows Server 2022. Diagrams to follow


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

