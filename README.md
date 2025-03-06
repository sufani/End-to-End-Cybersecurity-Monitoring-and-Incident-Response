# End-to-End Cybersecurity Monitoring and Incident Response

This project implements a robust cybersecurity monitoring and incident response solution that simulates, detects, and responds to a variety of attack vectors. It integrates key security tools like **ELK Stack**, **Mythic C2**, **Elastic Defend (EDR)**, and **oSTicket** to ensure real-time detection, response, and mitigation.

## Key Features
- **ELK Stack**: Aggregates and analyzes security logs in real-time. Custom Kibana dashboards visualize data on **RDP**, **SSH**, and **Mythic C2** activity. Automated alerts detect suspicious behaviors like **brute-force login attempts** and **C2 communications**.
- **Elastic Defend (EDR)**: Provides endpoint protection by enabling automated isolation of compromised systems. Integrated with the ELK Stack, it enhances visibility into endpoint activity and network-level threats.
- **Mythic C2**: Simulates **advanced persistent threats (APTs)** and malicious agent behavior. It establishes **C2 communication** for testing and training purposes, allowing for controlled attack simulations.
- **oSTicket**: Automates incident response by forwarding alerts from the ELK Stack into a ticketing system. This simplifies the process of assigning, tracking, and resolving incidents.

## Technologies Used:
- **ELK Stack (Elasticsearch, Kibana, Logstash)**: For aggregating, analyzing, and visualizing security data.
- **Elastic Defend (EDR)**: For endpoint protection and containment of compromised machines.
- **Mythic C2**: For simulating attacks and testing security defenses.
- **oSTicket**: For incident management and automated alert handling.
- **Vultr**: For provisioning and managing cloud-based server instances.


## Project Walk-through:

### 1. Project Overview Diagram

![Project Overview Diagram](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/CybersecurityMonitoring&IncidentResponse.drawio.png?raw=true)

### 2. Deploying Servers on Vultr

![Vultr Servers](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/all%20Vultr%20Servers.jpeg?raw=true)

This screenshot shows the **Vultr** servers used in the project, including the **ELK-Server**, **Fleet-Server**, **Linux-Server**, **Mythic-Server**, **osTicket-Server**, and **Windows-Server-RDP**.

### 3. Setting Up Elasticsearch and Kibana

**Kibana Configuration**  
I configured **Kibana** by setting encryption keys and integrating it with **Elasticsearch** to collect and visualize security data.  
![Kibana Config](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Kibana%20Config.jpeg?raw=true)

**Kibana Dashboard**  
The **Kibana Dashboard** was set up to display security data, confirming that Kibana was properly configured to monitor and visualize threats.  
![Kibana Dashboard](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Kibana%20Dashboard.jpeg?raw=true)

### 4. Installing and Configuring Elastic Agent

**Installing Fleet Server**  
I installed the **Elastic Agent** on the **Fleet Server**, enabling centralized management of the agents.  
![Install Fleet Server](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Install%20Fleet%20Server.jpeg?raw=true)

**Adding Fleet Server**  
I added the **Fleet Server** to **Elastic Fleet**, configured the server policy, and enrolled the agents.  
![Add Fleet Server](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Add%20Fleet.jpeg?raw=true)

### 5. Integrating Sysmon and Linux Logs

**Configuring Sysmon and Ingesting Logs**  
I configured **Sysmon** on the **Windows Server** to monitor system activities and ingested **Windows Defender** and **Sysmon logs** into **Elasticsearch** for analysis.  
![Sysmon Config](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Sysmon%20config.jpeg?raw=true)  
![Windows Logs](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Windows%20Logs.jpeg?raw=true)

**Linux Logs Integration**  
On the **Linux Server**, I used the **Elastic Agent** to collect logs and send them to **Elasticsearch**, providing a comprehensive view of system activities across both platforms.

### 6. Setting Up Alerts for Threat Detection

I configured **detection rules** in **Kibana** to detect **RDP** and **SSH brute-force** login attempts. These alerts are automatically triggered, allowing me to investigate the incidents further.  
![SSH & RDP Alerts](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/SSH&RDPalerts.jpeg?raw=true)

### 7. Simulating Attacks with Mythic C2

**Configuring and Running Mythic C2**  
I configured the **Mythic C2** server and ran a payload to simulate a **C2 attack**.  
![Mythic Configuration](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/MythicConf.jpeg?raw=true)  
![Mythic GUI](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/Mythic.jpeg?raw=true)

**Running the Payload**  
I executed the payload (`svchost-soc-lab.exe`) on the **Windows Server**, which established a C2 connection back to the Mythic server.  
![Running Payload](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/PayloadRun.jpeg?raw=true)

**Verifying C2 Activity**  
To confirm the payload's activity, I checked the **Mythic C2 callback** status and ran the `whoami` command to verify the system's identity.  
![Mythic C2 Callback](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/MythicC2.jpeg?raw=true)  
![Whoami Command](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/RunCmd.jpeg?raw=true)

### 8. Creating Detection Rules for Mythic C2 and Brute Force Attacks

**Mythic C2 Detection Rule**  
I created a **detection rule** for **Mythic C2** to alert on any agent activity and connections with the C2 server.  
![Mythic C2 Detection Rule](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/MythicRule.jpeg?raw=true)

**Suspicious Activity Detection Rules**  
I set up detection rules to capture suspicious network behavior and potential malware activities, such as **process creation**. This helps in identifying abnormal behavior that could signal a **malware infection**.  
![Suspicious Activity Detection Rules](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/SuspiciousActRules.jpeg?raw=true)

### 9. Automating Incident Response with oSTicket

**Installing and Connecting oSTicket**  
I set up **oSTicket** for incident management and connected it to the **ELK Stack** using **webhooks**. This ensures that alerts from the ELK Stack automatically create tickets in **oSTicket** for further handling.  
![oSTicket Installed](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/osTcket.jpeg?raw=true)  
![Connecting oSTicket](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/ConnOSTicket.jpeg?raw=true)

**Viewing and Assigning Tickets**  
After integrating **oSTicket**, I was able to view and manage incoming tickets for incidents such as **SSH Brute Force Attempts** and **Mythic C2 Apollo Agent Detected**. I assigned these tickets to myself for investigation.  
![Open Tickets](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/OpenTickets.jpeg?raw=true)  
![Assigned Tickets](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/AssignedTicket.jpeg?raw=true)

### 10. Isolating a Compromised Machine with Elastic Defend (EDR)

**Configuring and Managing Endpoints**  
I configured **Elastic Defend (EDR)** integration and applied security policies to all endpoints. This allowed for centralized endpoint management, with the ability to isolate compromised machines.  
![Elastic Defend Integration Policies](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/EDR.jpeg?raw=true)  
![Managing Endpoints](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/IsolateWin.jpeg?raw=true)

**Isolating and Releasing Hosts**  
Upon detection of a compromised host, I triggered the **Isolate Host** action to contain the threat. Later, I released the host from isolation after the issue was resolved.  
![Isolated Host Action](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/IsolatedHost.jpeg?raw=true)  
![Release Host Action](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/ReleaseHost.jpeg?raw=true)

### 11. Monitoring and Analyzing Attack Telemetry

Using the **Kibana Dashboard**, I monitored **RDP** and **SSH brute-force attempts** and visualized the attack telemetry, helping me track the sources and success rates of these attacks across different regions.  
![RDP Dashboard](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/RDP%20DashBoard.jpeg?raw=true)  
![SSH Dashboard](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/SSH%20DashBoard.jpeg?raw=true)

### 12. Cloud Infrastructure Overview

A visual overview of the **cloud infrastructure** on **Vultr** was provided, showcasing the server layout and network configuration across multiple instances. This setup allowed for efficient monitoring, incident detection, and automation.  
![Vultr Server Overview](https://github.com/sufani/End-to-End-Cybersecurity-Monitoring-and-Incident-Response-/blob/main/images/all%20Vultr%20Servers.jpeg?raw=true)


