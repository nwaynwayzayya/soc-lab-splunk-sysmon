# Building the Lab

## Overview

The first step in building the SOC home lab was creating two virtual machines using VirtualBox.

The lab consists of:

* One Windows 10 virtual machine
* One Kali Linux virtual machine

These systems provide an isolated environment for generating and monitoring security events.

---

# Installing VirtualBox

VirtualBox was installed on the host machine to provide virtualization capabilities.

After installation, it was used to create and manage both virtual machines.

![VirtualBox](/screenshots/virtualbox.png)

---

# Creating the Windows Virtual Machine

A Windows 10 virtual machine was created to act as the monitored endpoint.

Configuration included:

* Virtual hard disk
* Memory allocation
* CPU allocation
* Windows installation
* Initial operating system setup

![Windows](/screenshots/windows.png)
![Windows2](/screenshots/windows2.png)

---

# Creating the Kali Linux Virtual Machine

A Kali Linux virtual machine was created to simulate attacker activity.

Configuration included:

* Virtual hard disk
* Memory allocation
* CPU allocation
* Kali Linux installation

![Kali](/screenshots/kali.png)
![Kali2](/screenshots/kali2.png)

---

# Guest Additions

VirtualBox Guest Additions were installed to improve usability.

Benefits include:

* Improved display resolution
* Clipboard sharing
* Better mouse integration
* Enhanced performance

---

# Virtual Machine Snapshots

Snapshots were created after completing major milestones.

This allows the environment to be restored quickly if something breaks during testing.

---

# Lab Environment Summary

| Component  | Purpose                 |
| ---------- | ----------------------- |
| Windows 10 | Monitored endpoint      |
| Kali Linux | Attack simulation       |
| VirtualBox | Virtualization platform |

---

# What I Learned

Building the environment provided practical experience with virtualization and highlighted the importance of creating isolated environments for cybersecurity testing.
