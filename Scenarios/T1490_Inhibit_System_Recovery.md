# Scenario: Inhibit System Recovery Detection (T1490)

## What is T1490?
Attackers delete Windows backup and recovery files (Shadow Copies) before encrypting data with ransomware. This prevents victims from recovering their files.

## What We Did
We used Atomic Red Team to simulate a ransomware preparation attack, then detected it using Splunk.

## How We Detected It
We monitored Sysmon Event ID 1 & Windows Security Event 4688 for:
- Commands that delete Shadow Copies `vssadmin delete shadows`
- Commands that disable backups `wmic shadowcopy delete`
- Commands that resize shadow storage

---

## Attack Simulation
> <img width="1253" height="447" alt="image" src="https://github.com/user-attachments/assets/df5c1849-73bb-41df-b6d8-c89b4a0193ce" />

> *Screenshot of the command used*

---

## Detection Results
- Successfully detected shadow copy deletion commands
- Identified this as critical pre-ransomware activity
 
> <img width="1022" height="730" alt="image" src="https://github.com/user-attachments/assets/bdd548b1-33c3-4b5d-927e-b5af5096b018" />


> <img width="1025" height="728" alt="image" src="https://github.com/user-attachments/assets/87df0d2a-d970-464b-999a-25197153eb3b" />


> <img width="644" height="564" alt="image" src="https://github.com/user-attachments/assets/23fa7466-cbfe-46f0-a6b8-975075aca5d5" />



*Add an Alert Example*
[here]
