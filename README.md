# Multi-Protocol Command & Control (C2) Detection

## Overview

Identified concurrent SSL/TLS encrypted sessions operating alongside FTP data exfiltration, indicating sophisticated command and control (C2) infrastructure. Demonstrated advanced protocol correlation skills to detect attacker operational security techniques.

## Scenario

During investigation of FTP data exfiltration between two hosts (172.16.100.3 and 85.93.20.10), additional protocol analysis revealed simultaneous encrypted communication channel, suggesting coordinated attack infrastructure.

## Tools Used

- **Elastic SIEM** - Multi-protocol correlation and analysis
- **Zeek** - Network traffic protocol identification
- **Zeek-FTP Dashboard** - Service field analysis

## Investigation Process

### 1. Initial FTP Analysis
- Started with Zeek-FTP Dashboard investigation
- Identified FTP traffic between source (172.16.100.3) and destination (85.93.20.10)

### 2. Protocol Expansion
- Removed FTP-only filter to view all traffic between hosts
- Query: `source.ip: 172.16.100.3 AND destination.ip: 85.93.20.10`
- Analyzed service field for additional protocols

### 3. C2 Channel Discovery
- **Finding:** SSL/TLS protocol detected alongside FTP traffic
- **Implication:** Encrypted command channel coordinating data exfiltration
- **Attack Sophistication:** Attacker used separate encrypted channel for C2 communications

### 4. Timeline Correlation
- SSL session established: Persistent long-duration connection
- FTP transfers: Intermittent data exfiltration events
- Pattern indicates SSL was controlling when/what to exfiltrate via FTP

## MITRE ATT&CK Mapping

- **T1071.001** - Application Layer Protocol: Web Protocols (SSL/TLS for C2)
- **T1041** - Exfiltration Over C2 Channel
- **T1048** - Exfiltration Over Alternative Protocol (FTP)
- **T1573** - Encrypted Channel (SSL/TLS)

## Skills Demonstrated

- Multi-protocol traffic correlation
- C2 infrastructure identification
- Understanding attacker operational security (OPSEC)
- Advanced filtering and query modification
- Behavioral analysis of coordinated attack techniques
- Recognizing encrypted command channels

## Threat Intelligence Insights

**Why SSL + FTP?**
- **SSL:** Encrypted C2 channel hides commands from detection
- **FTP:** Unencrypted data transfer (sometimes easier to establish)
- **Coordination:** SSL tells FTP what/when to exfiltrate
- **Defense Evasion:** Separating control and data channels complicates detection

## Conclusions

Successfully identified sophisticated multi-protocol attack infrastructure where SSL/TLS was used as an encrypted command and control channel to coordinate FTP data exfiltration. This investigation demonstrates ability to perform advanced protocol correlation, recognize attacker OPSEC techniques, and understand complex threat actor behavior beyond basic detection.

---

**Portfolio:** [github.com/paigealfred](https://github.com/paigealfred)
