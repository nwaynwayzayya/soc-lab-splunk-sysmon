# Overview & Architecture

## Introduction

A Security Operations Center (SOC) relies on visibility into endpoint and network activity to detect, investigate, and respond to security incidents. To better understand these concepts, I built a small SOC home lab using virtual machines and open-source security tools.

The lab provides an isolated environment where Windows activity can be safely generated, monitored, and analyzed without affecting production systems.

Rather than focusing on offensive security, the objective of this project is to understand how endpoint telemetry is collected and how security analysts investigate suspicious activity.

---

# Lab Objectives

The objectives of this lab are to:

* Build a virtual SOC environment.
* Configure secure communication between virtual machines.
* Collect Windows telemetry using Sysmon.
* Ingest Windows Event Logs into Splunk.
* Generate realistic endpoint activity.
* Investigate security events using Splunk.

---

# Lab Components

## VirtualBox

VirtualBox provides the virtualization platform used to run multiple operating systems simultaneously on a single host computer.

---

## Windows 10 Virtual Machine

The Windows virtual machine serves as the monitored endpoint.

Responsibilities include:

* Running Sysmon
* Generating Windows Event Logs
* Sending telemetry to Splunk
* Executing test activity during simulations

---

## Kali Linux Virtual Machine

Kali Linux acts as the attacker workstation.

Responsibilities include:

* Network reconnaissance
* Test payload generation
* Hosting payloads
* Establishing controlled remote sessions

---

## Sysmon

Sysmon extends Windows logging by recording detailed endpoint activity.

Examples include:

* Process creation
* Network connections
* File creation
* Driver loading
* Process termination

These events provide significantly more visibility than standard Windows logging.

---

## Splunk Enterprise

Splunk collects, indexes, and searches Windows telemetry.

Within this project it is used to:

* Collect Sysmon logs
* Search Windows Event Logs
* Investigate process activity
* Correlate related events

---

# Lab Architecture

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
                Security Investigation
```

---

# Network Layout

Both virtual machines communicate through an isolated VirtualBox Internal Network.

This configuration allows the machines to communicate with each other while remaining separated from external networks, providing a safe environment for security testing.

---

# Project Workflow

The overall workflow of the lab is shown below.

```text
Build Lab
     ↓
Configure Networking
     ↓
Install Sysmon
     ↓
Install Splunk
     ↓
Generate Telemetry
     ↓
Search Logs
     ↓
Investigate Events
```

---

# What I Learned

This project helped me understand:

* How a SOC lab is structured.
* How endpoint telemetry is generated.
* Why Sysmon is widely used by security teams.
* How Splunk collects and searches security logs.
* How Windows events can be investigated during security analysis.
