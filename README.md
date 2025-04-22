# OPS305-Email-NFS-Server-Setup
Multi-server email infrastructure using Postfix MTAs, NFS storage, and nftables-based firewall rules. Completed for OPS305 at Seneca Polytechnic.
# Multi-Server Email + NFS Deployment – OPS305 Assignment 2

**Course:** OPS305 – Linux Server Administration  
**Date:** November 2024  
**Institution:** Seneca Polytechnic

---

## 🧠 Overview
This project simulates an enterprise email infrastructure using two mail servers and an NFS-based message store. The incoming and outgoing MTAs were configured using Postfix, while shared mail storage and user home directories were managed via NFS. Security was enforced through nftables firewalls and AWS subnet-level controls.

---

## 🛠️ System Setup
- **mintaka (Incoming MTA):**  
  - Accepts domain mail and routes root messages to student account  
  - Stores emails in Maildir format under `/mail`  
  - Forwards outbound mail to the outgoing server  
  - Mounts shared `/mail` and home directories from NFS

- **meissa (Outgoing MTA):**  
  - Routes external mail to destination servers  
  - Forwards domain-addressed mail to `mintaka`  
  - Mounts user directories from NFS via `autofs`

- **saiph (NFS Server):**  
  - Serves `/mail` and `/home` directories to mail servers  
  - Configured for NFSv4 access control

---

## 🔐 Firewall Setup
- `nftables` used with `drop` default policy  
- ICMP, DNS, SMTP, SSH, and NFS selectively allowed  
- AWS Security Groups and internal firewall rules applied

---

## 🧠 Skills Demonstrated
- Postfix configuration for incoming/outgoing mail  
- NFS setup and `autofs` integration  
- Linux firewall configuration using `nftables`

---

## 📂 Notes
This project was completed and tested in a live AWS lab environment. Screenshots and test logs were reviewed and submitted separately at the time of assignment.

---

## ✅ Project Status
- ✔️ Mail flow and storage configured successfully  
- ✔️ NFS directories mounted and secured  
- ✔️ Traffic restrictions enforced via firewall rules
