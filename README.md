# TrapForge

## An Adaptive Multi-Service Deception Framework with a Composite Attack Engagement Index for Cyber Threat Intelligence

TrapForge is an adaptive multi-service cyber-deception and threat-intelligence framework designed to collect, normalize, correlate, and analyze attacker activity across multiple honeypot services.

The framework combines SSH, FTP/Telnet, and HTTP deception surfaces with a centralized logging and analytics pipeline. It introduces the **Attack Engagement Index (AEI)** to quantify attacker engagement using multiple behavioral indicators rather than relying only on connection counts.

---

## 🚀 Overview

Traditional honeypot deployments often operate as isolated services and generate heterogeneous logs. This makes it difficult to:

- Correlate attacker activity across multiple services
- Compare the intensity of different attack sessions
- Reconstruct an attacker's progression over time
- Determine whether an attacker is performing automated scanning or deeper interaction
- Adapt the deception environment according to attacker behavior

TrapForge addresses these challenges through a modular five-layer architecture:

```text
                    Internet
                       │
                       ▼
              ┌─────────────────┐
              │    Attackers    │
              └────────┬────────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       Cowrie      OpenCanary     Flask
        SSH        FTP/Telnet    Fake Admin
          │            │            │
          └────────────┼────────────┘
                       ▼
             Log Collection &
              Normalization
                       │
                       ▼
                  MySQL DB
                       │
                       ▼
        ┌──────────────────────────┐
        │ Intelligence Computation │
        │                          │
        │  AEI  │  AJM  │   DRS    │
        └────────────┬─────────────┘
                     │
                     ▼
             Adaptive Response
                     │
                     ▼
              Flask Dashboard
