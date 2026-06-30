# Beginner SOC Home Lab

> A hands-on Security Operations Center (SOC) home lab built using VirtualBox, Windows 10, Kali Linux, Sysmon, and Splunk to learn security monitoring, endpoint telemetry, and basic log analysis.

---

## Overview

This project documents the creation of my first SOC home lab. The lab was built to gain practical experience with security monitoring by creating an isolated environment where Windows endpoint activity can be generated, collected, and investigated safely.

The project follows the complete workflow of:

* Building a virtual lab environment
* Configuring Windows monitoring with Sysmon
* Collecting logs using Splunk
* Generating security telemetry through controlled attack simulations
* Investigating the resulting events

Rather than focusing on offensive security techniques, this lab focuses on understanding how attacker activity appears from a defender's perspective.

---

## Lab Architecture

> *(Insert architecture diagram here)*

```text
                +-----------------------+
                |      Kali Linux       |
                |    (Attacker VM)      |
                +-----------+-----------+
                            |
                    Internal Network
                            |
                +-----------+-----------+
                |      Windows 10       |
                |     (Target VM)       |
                +-----------+-----------+
                            |
                         Sysmon
                            |
                   Windows Event Logs
                            |
                    Splunk Enterprise
                            |
                 Search & Investigation
```

---

## Technologies Used

| Technology           | Purpose                       |
| -------------------- | ----------------------------- |
| VirtualBox           | Virtualization platform       |
| Windows 10           | Target endpoint               |
| Kali Linux           | Attack simulation             |
| Sysmon               | Endpoint telemetry collection |
| Splunk Enterprise    | Log ingestion and analysis    |
| Nmap                 | Network reconnaissance        |
| msfvenom             | Test payload generation       |
| Metasploit Framework | Reverse shell handler         |
| Python HTTP Server   | Payload hosting               |

---

## Learning Objectives

This project was created to gain hands-on experience with:

* Building a virtual SOC lab
* Configuring isolated virtual networks
* Installing and configuring Sysmon
* Collecting Windows Event Logs
* Configuring Splunk for endpoint monitoring
* Generating Windows security telemetry
* Investigating endpoint activity using Splunk

---

## Documentation

| Document                                  | Description                                                 |
| ----------------------------------------- | ----------------------------------------------------------- |
| 01 - Overview & Architecture              | Lab purpose, architecture, and components                   |
| 02 - Building the Lab                     | Creating the virtual machines and preparing the environment |
| 03 - Configuring Monitoring               | Networking, Sysmon, and Splunk configuration                |
| 04 - Generating & Investigating Telemetry | Creating endpoint activity and analyzing the resulting logs |

---

## Project Highlights

* Built a two-machine virtual SOC lab using VirtualBox.
* Configured an isolated internal network between Windows and Kali Linux.
* Installed and configured Sysmon for enhanced Windows event logging.
* Configured Splunk Enterprise to ingest Windows and Sysmon logs.
* Generated endpoint telemetry through controlled attack simulations.
* Investigated process creation and network events using Splunk.

---

## Acknowledgements

This project was built as part of my cybersecurity learning journey using publicly available educational resources. While the initial lab setup follows a guided learning approach, the documentation, organization, screenshots, and explanations in this repository have been written to reinforce my understanding of SOC concepts and security monitoring.

---

## Disclaimer

This project was created for educational purposes only.

All attack simulations were performed exclusively inside an isolated virtual lab environment using systems that I own and control. No testing was performed against unauthorized systems or networks.
