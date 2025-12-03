# Azure Security Monitoring Lab
---
## Overview
This lab demonstrates how to deploy a production-style security monitoring environment in Microsoft Azure.  
It includes a segmented virtual network, Windows Server and Windows 10 virtual machines, centralized log ingestion, and Microsoft Sentinel for SIEM capabilities.  
The goal is to simulate a customer onboarding workflow similar to what a SOC or MSSP performs daily.

**Key Components**
- Windows Server 2022 (Domainless server)
- Windows 10 Pro client
- Azure Virtual Network with isolated subnets
- Log Analytics Workspace
- Microsoft Sentinel
- Data Collection Rules (DCR)
- Azure Monitor Agent (AMA)
- Simulated attack traffic for testing visibility

---
## Learning Objectives
- Understand how Azure Monitor Agents forward logs to a workspace  
- Learn how Sentinel ingests security events and produces alerts  
- Deploy a minimal, cost-effective security environment  
- Practice onboarding, troubleshooting, and validating log ingestion  
- Simulate malicious activity to generate realistic alerts  

---
## Core Lab Setup
| Component | Purpose | Notes |
|----------|----------|-------|
| **Resource Group** | Container for all assets | Deleted at the end to avoid charges |
| **Virtual Network** | Network segmentation | Two subnets: servers and workstations |
| **vm-c01-srv01** | Windows Server 2022 | Generates logs and serves as test target |
| **vm-c01-win10-01** | Windows 10 Pro | Used for RDP attempts and simulations |
| **Log Analytics Workspace** | Centralized log store | Required for Sentinel |
| **Microsoft Sentinel** | SIEM and alerting | Enabled on workspace |
| **Data Collection Rule** | AMA configuration | Collects security events |

---
## Security Event Collection
| Step | Description |
|------|-------------|
| AMA installed | Agent deployed to both VMs |
| DCR applied | SecurityEvent logs collected |
| Workspace connected | Heartbeat confirming ingestion |
| Sentinel enabled | Workspace available for analytics |
| Simulated incidents | RDP brute force, PowerShell misuse, registry persistence |

---
## Simulated Attack Scenarios
| Scenario | Purpose | Result |
|----------|----------|--------|
| RDP brute force | Generate repeated 4625 failures | Sentinel alerts trigger |
| Suspicious PowerShell | Web requests and downloads | PowerShell logs ingested |
| Registry persistence | Startup persistence key | Event ID 4657 logged |
| Successful authentication | Logon 4624 | Confirms visibility |

---
## Screenshots
(Add your images here)
| Image | Description |
|--------|-------------|
| *(insert screenshot)* | Resource group for Customer01 |
| *(insert screenshot)* | vnet-customer01 with two subnets |
| *(insert screenshot)* | vm-c01-srv01 deployed |
| *(insert screenshot)* | vm-c01-win10-01 deployed |
| *(insert screenshot)* | AMA connected to workspace |
| *(insert screenshot)* | Sentinel-enabled workspace |
| *(insert screenshot)* | Security events flowing |
| *(insert screenshot)* | Failed RDP attempts visible in logs |
| *(insert screenshot)* | Active incidents in Sentinel |

---
## Technical Highlights
- Azure Monitor Agent onboarding for both VMs  
- Data Collection Rules for Windows Security Logs  
- Sentinel analytics for detecting authentication anomalies  
- KQL queries for log review and filtering  
- Incident validation through simulated malicious behavior  
- End-to-end visibility across both server and workstation  

---
## Estimated Cost
| Resource | Type | Cost/hr |
|----------|------|---------|
| vm-c01-srv01 | B1s VM | ≈ $0.01–0.02 |
| vm-c01-win10-01 | B1s VM | ≈ $0.01–0.02 |
| Sentinel | Per-GB model | Low usage in small labs |
| **Total** | | **$0.02–0.05/hr** |

---
## Results
| Checklist |
|-----------|
| VMs deployed with network segmentation |
| AMA successfully installed |
| Security events collected in workspace |
| Sentinel analytics enabled |
| Simulated attacks detected |
| Workspace and DCR validated |
| All resources cleaned up after lab |

---
