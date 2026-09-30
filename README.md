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

Evidence:

<img width="1217" height="611" alt="Screenshot (372)" src="https://github.com/user-attachments/assets/d90bb9a6-ae51-4ce6-9186-b22d07f91470" />


### Sysmon

Installed and configured Microsoft Sysmon on the Windows endpoint.

Sysmon was verified to generate Windows process telemetry through:

Evidence

<img width="1019" height="714" alt="Screenshot (374)" src="https://github.com/user-attachments/assets/bb5f3138-5263-4907-8ea0-e89ee6a8b02c" />


`Microsoft-Windows-Sysmon/Operational`

### Sysmon → Wazuh

Configured the Wazuh Windows agent to collect the Sysmon Operational event channel using the Windows Event Channel format.

A Wazuh detection was observed for Windows process activity associated with **Sysmon Event ID 1 (Process Create)**.

Evidence

<img width="1211" height="682" alt="Screenshot (368)" src="https://github.com/user-attachments/assets/7db9fffc-8956-41e3-bb8a-e8c4063f35e7" />


One observed detection identified a `net.exe` account discovery command.

### VirusTotal

Integrated VirusTotal into the Wazuh lab and worked through the API configuration and file monitoring requirements.

## Atomic Red Team

# Atomic Red Team Detection Validation

### Test 1 — Local Account Discovery

**Technique:** T1087.001 - Account Discovery: Local Account
**Atomic Test:** Test 9
**Activity:** Local account discovery using Windows built-in commands
**Telemetry:** Sysmon Event ID 1 - Process Creation
**SIEM:** Wazuh
**Detection Rule:** 92031 - Discovery activity executed
**Result:** Successfully detected

Atomic Test Execution

The Atomic Red Team test was executed on the Windows 11 endpoint using Invoke-AtomicTest.

Evidence:

<img width="1022" height="725" alt="Screenshot (373)" src="https://github.com/user-attachments/assets/87d236dd-c9c8-4aeb-b82e-2661e7ee01f6" />


#### Detection Evidence

The Atomic Red Team test generated discovery activity on the Windows 11 endpoint. Sysmon captured the process creation event, and the Wazuh agent forwarded the telemetry to the Wazuh manager.

Wazuh successfully matched the activity with rule **92031**, producing the alert **“Discovery activity executed.”**

**Detection chain:**

`Atomic Red Team → Windows 11 → Sysmon → Wazuh Agent → Wazuh Manager → Rule 92031`

**Evidence screenshot:**

<img width="1201" height="669" alt="Screenshot (371)" src="https://github.com/user-attachments/assets/e26a8cde-2785-49e9-afa7-af5da473373c" />



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
