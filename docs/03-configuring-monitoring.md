# Configuring Monitoring

## Overview

After creating the virtual machines, the next step was configuring communication between them and enabling Windows monitoring.

This involved:

* Configuring the virtual network
* Verifying connectivity
* Installing Sysmon
* Installing Splunk
* Configuring Splunk to ingest Sysmon events

---

# Configuring the Internal Network

Both virtual machines were connected using VirtualBox's Internal Network mode.

This allowed direct communication while keeping the lab isolated from external systems.

> **Screenshot:** VirtualBox network settings
![Windows2](/screenshots/windows2.png)
![Kali2](/screenshots/kali2.png)

---

# Assigning Static IP Addresses

Static IP addresses were configured on both virtual machines to ensure reliable communication.

Connectivity was verified using ping.

> **Screenshot:** Windows IP configuration
![WindowsIP](/screenshots/windowsIP.png)

> **Screenshot:** Kali IP configuration
![Kali2IP](/screenshots/kaliIP.png)

> **Screenshot:** Successful ping
![Ping](/screenshots/ping.png)

---

# Installing Sysmon

Sysmon was installed on the Windows virtual machine using a Sysmon configuration file.

Installation was verified by checking:

* Windows Services
* Event Viewer

> **Screenshot:** Sysmon service
![Sysmon Service](/screenshots/sysmonservice.png)

> **Screenshot:** Sysmon operational log
![Sysmon Operational](/screenshots/sysmonoperational.png)

---

# Installing Splunk Enterprise

Splunk Enterprise was installed on the Windows virtual machine.

After installation, the web interface was used to configure log collection.

> **Screenshot:** Splunk dashboard
![Splunk dashboard](/screenshots/splunkdashboard.png)

---

# Configuring Log Collection

To collect Sysmon events:

* `inputs.conf` was configured.
* An `endpoint` index was created.
* The Splunk service was restarted.
* The Splunk Add-on for Sysmon was installed.

These steps allowed Sysmon events to be parsed correctly within Splunk.

> **Screenshot:** inputs.conf

![inputs.conf](/screenshots/inputs.png)

> **Screenshot:** Endpoint index
![Endpoint index](/screenshots/endpointindex.png)

> **Screenshot:** Sysmon Add-on
![Sysmon Add-on](/screenshots/sysmonaddon.png)

---

# Verifying Data Ingestion

A search was performed using:

```spl
index=endpoint
```

Successful search results confirmed that Sysmon events were being ingested into Splunk.

> **Screenshot:** Search results
![Search results](/screenshots/searchresults.png)

---

# What I Learned

This stage demonstrated how endpoint telemetry moves from Windows into a SIEM, providing the visibility needed for security monitoring and investigation.
