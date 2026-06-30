# Generating & Investigating Security Telemetry

## Overview

After completing the lab setup and monitoring configuration, the final step was to generate Windows activity and observe how it was recorded by Sysmon and collected in Splunk.

The purpose of this exercise was to understand how common attacker actions create endpoint telemetry that can later be investigated by a SOC analyst.

---

## Step 1 - Verify Connectivity

Before beginning the simulation, I verified communication between the Kali Linux and Windows virtual machines.

An Nmap scan was performed against the Windows machine to confirm connectivity and identify available services.

> **Screenshot:** Nmap scan results
![Nmap scan](/screenshots/nmapscan.png)

---

## Step 2 - Generate a Test Payload

A test payload was generated using **msfvenom**. The payload was configured to communicate back to the Kali Linux virtual machine, allowing activity to be generated for monitoring purposes.

The generated executable was then prepared for delivery to the Windows virtual machine.

> **Screenshot:** msfvenom payload generation
![msfvenom payload generation](/screenshots/msfvenom.png)

---

## Step 3 - Configure the Listener

A Metasploit handler was configured on the Kali Linux machine to receive the incoming connection from the payload.

A temporary Python HTTP server was also started to host the executable for download.

> **Screenshot:** Metasploit handler
![Metasploit handler](/screenshots/handler.png)

> **Screenshot:** Python HTTP server
![Python HTTP server](/screenshots/pythonserver.png)

---

## Step 4 - Execute the Payload

On the Windows virtual machine, the payload was downloaded and executed inside the isolated lab environment.

After execution, a reverse connection was successfully established with the Kali Linux machine.

The connection was verified using:

* Meterpreter
* `netstat`
* Task Manager

> **Screenshot:** Downloading the payload
![Downloading the payload](/screenshots/downloadpayload.png)

> **Screenshot:** Meterpreter session
![Meterpreter session](/screenshots/meterpretersession.png)

> **Screenshot:** Netstat output
![Netstat output](/screenshots/netstatoutput.png)

---

## Step 5 - Investigate the Generated Telemetry

After establishing the Meterpreter session, I used the `shell` command to open a Windows command prompt on the target machine. From there, I executed several built-in Windows commands to generate additional endpoint telemetry:

* `net user`
* `net localgroup`
* `ipconfig`

These commands were recorded by Sysmon as process creation events and forwarded to Splunk.

To investigate the activity, I first identified the process associated with the executed payload (`Resume.pdf.exe`) and obtained its **Process GUID** from the Sysmon logs. I then used that Process GUID to filter related events and displayed the **ParentImage** and **CommandLine** fields to reconstruct the process execution chain.

This allowed me to observe how the initial payload spawned `cmd.exe`, which subsequently executed commands such as `net user`, `net localgroup`, and `ipconfig`. By following the process relationship rather than searching for individual commands, I was able to trace the sequence of events generated during the simulation.

> **Screenshot:** Meterpreter session
![Meterpreter session](/screenshots/meterpretersession2.png)

> **Screenshot:** Splunk search using Process GUID
![Splunk search using Process GUID](/screenshots/guid.png)

> **Screenshot:** Process creation events showing `cmd.exe`, `net user`, `net localgroup`, and `ipconfig`
![Process creation events](/screenshots/processcreations.png)

---

## What I Learned

This exercise demonstrated how endpoint telemetry is generated, collected, and investigated within a SOC environment.

Some key takeaways include:

* Sysmon provides detailed visibility into endpoint activity.
* Splunk can centralize and search Windows event logs.
* Process creation events can be used to trace executed programs.
* Multiple tools work together to provide visibility into endpoint behavior.
