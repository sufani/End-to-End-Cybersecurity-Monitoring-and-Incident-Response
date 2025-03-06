# End-to-End Cybersecurity Monitoring and Incident Response

This project is a comprehensive cybersecurity monitoring and incident response solution designed to simulate, detect, and respond to a variety of attack vectors. Utilizing the ELK Stack (Elasticsearch, Logstash, Kibana) for centralized log aggregation and visualization, Mythic C2 for advanced attack simulation, and Elastic Defend (EDR) for endpoint security, this solution provides robust capabilities for real-time threat detection and response.

## Key Features

- **ELK Stack** for log collection and analysis, allowing for efficient aggregation, storage, and visualization of security data. Custom Kibana dashboards provide insights into RDP, SSH, and Mythic C2 activities, while automated alerts detect anomalous behaviors like brute-force attempts and C2 communications.
- **Elastic Defend (EDR)** for endpoint protection, enabling real-time threat prevention and automated isolation of compromised systems. Elastic Defend integrates seamlessly with the ELK Stack to provide a complete picture of both endpoint activity and network-level threats.
- **Mythic C2** for simulating advanced persistent threats (APTs) and generating malicious agents that establish command-and-control (C2) communications, providing a simulated attack environment for training and testing defensive measures.
- **oSTicket** for automating incident response. Alerts from ELK Stack are automatically forwarded to the ticketing system, streamlining the process of assigning, tracking, and resolving security incidents.

## Technologies Used:

- **ELK Stack** (Elasticsearch, Kibana, Logstash) for security data aggregation, analysis, and visualization.
- **Elastic Defend (EDR)** for endpoint detection and response, including automatic containment of compromised machines.
- **Mythic C2** for simulating attacks and testing security defenses.
- **oSTicket** for incident management and alert automation.
- **Vultr** for cloud-based server provisioning and management.

## Project Walk-through:
