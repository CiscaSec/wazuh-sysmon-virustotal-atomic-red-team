# wazuh-sysmon-virustotal-atomic-red-team
A hands-on SIEM and threat detection lab integrating Wazuh, Sysmon, VirusTotal, and Atomic Red Team.
# Wazuh + Sysmon + VirusTotal + Atomic Red Team Lab

> 🚧 **Status: Work in Progress**

A hands-on cybersecurity lab focused on endpoint visibility, SIEM detection, threat intelligence, and controlled adversary simulation using **Wazuh, Microsoft Sysmon, VirusTotal, and Atomic Red Team**.

The objective is to build and document an end-to-end detection workflow from simulated adversary activity to endpoint telemetry, SIEM detection, and investigation.

## Lab Architecture

```text
Atomic Red Team
       ↓
Windows 11 Endpoint
       ↓
     Sysmon
       ↓
  Wazuh Agent
       ↓
 Wazuh Manager
       ↓
Detection & Investigation
       ↓
 VirusTotal Enrichment
```

## Environment

* **Wazuh Manager:** Ubuntu
* **Endpoint:** Windows 11
* **Endpoint Telemetry:** Microsoft Sysmon
* **SIEM:** Wazuh
* **Threat Intelligence:** VirusTotal
* **Adversary Simulation:** Atomic Red Team
* **Testing Machine:** Kali Linux
* **Virtualization:** VMware Workstation

## Project Objectives

* Deploy and configure Wazuh SIEM
* Deploy a Windows 11 Wazuh agent
* Configure Sysmon for detailed Windows endpoint telemetry
* Integrate Sysmon events with Wazuh
* Integrate VirusTotal for file/hash reputation enrichment
* Use Atomic Red Team to simulate controlled adversary techniques
* Observe the resulting endpoint telemetry
* Validate Wazuh detections
* Investigate security events
* Document the attack-to-detection workflow

## Completed Work

### Wazuh Deployment

Deployed the Wazuh Manager on an Ubuntu virtual machine and verified that the service is operational.

### Windows 11 Wazuh Agent

Deployed the Wazuh agent on a Windows 11 virtual machine.

The agent was verified as **Active** and communicating with the Wazuh Manager.

### Sysmon

Installed and configured Microsoft Sysmon on the Windows endpoint.

Sysmon was verified to generate Windows process telemetry through:

`Microsoft-Windows-Sysmon/Operational`

### Sysmon → Wazuh

Configured the Wazuh Windows agent to collect the Sysmon Operational event channel using the Windows Event Channel format.

A Wazuh detection was observed for Windows process activity associated with **Sysmon Event ID 1 (Process Create)**.

One observed detection identified a `net.exe` account discovery command.

### VirusTotal

Integrated VirusTotal into the Wazuh lab and worked through the API configuration and file monitoring requirements.

## Atomic Red Team

**Status: Planned / In Progress**

Atomic Red Team will be used to generate controlled ATT&CK-aligned adversary activity against the Windows 11 lab endpoint.

The planned workflow is:

```text
Atomic Red Team Test
        ↓
Windows Endpoint Activity
        ↓
Sysmon Telemetry
        ↓
Wazuh Agent
        ↓
Wazuh Detection
        ↓
Investigation
        ↓
VirusTotal Enrichment where applicable
```

Individual Atomic Red Team techniques will be documented after they are executed and validated in the lab.

## Evidence

Screenshots and investigation evidence will be added as the project progresses.

Planned evidence includes:

* Wazuh Manager status
* Windows Wazuh Agent status
* Sysmon configuration
* Sysmon process events
* Wazuh Sysmon detections
* VirusTotal enrichment
* Atomic Red Team execution
* Detection and investigation results

## Skills Demonstrated

* SIEM deployment and administration
* Windows endpoint monitoring
* Sysmon
* Security event analysis
* Detection engineering
* Threat investigation
* Threat intelligence
* MITRE ATT&CK
* Adversary simulation
* Linux administration
* Windows administration

## Project Status

| Component                         | Status         |
| --------------------------------- | -------------- |
| Wazuh Manager                     | ✅ Completed    |
| Windows Wazuh Agent               | ✅ Completed    |
| Sysmon                            | ✅ Completed    |
| Sysmon → Wazuh                    | ✅ Validated    |
| VirusTotal                        | ✅ Integrated   |
| Atomic Red Team                   | 🔄 In Progress |
| Detection validation              | 🔄 In Progress |
| Final investigation documentation | 🔄 In Progress |

## Disclaimer

This project is conducted in an isolated laboratory environment using virtual machines and systems authorized for testing. Security testing is performed only against systems owned or explicitly authorized for testing.
