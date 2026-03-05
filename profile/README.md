<div align="center">

# 🌌 Orion

### Holistic Infrastructure Defense

[![License: GPLv2](https://img.shields.io/badge/Bellatrix-GPLv2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)
[![License](https://img.shields.io/badge/Platform-Proprietary-red.svg)](#-license)

**Bridging Linux Cloud Infrastructure and Windows Identity Management into a unified, autonomous security platform.**

[Getting Started](#-getting-started) · [Architecture](#-the-ecosystem) · [Roadmap](#-roadmap) · [Team](#-the-team)

</div>

---

## 📖 Overview

Modern cybersecurity suffers from critical fragmentation — **Linux-dominated cloud infrastructures** and **Windows-based identity management** are monitored in isolation, leaving dangerous blind spots for attackers to exploit.

**Orion** acts as a central nervous system for the enterprise, deploying an ultra-lightweight hybrid agent that operates at the lowest levels of the operating system to provide **total visibility** and **autonomous remediation**.

### Why Orion?

| Challenge | Orion's Answer |
|---|---|
| Siloed monitoring tools | Unified cross-platform agent covering Linux & Windows |
| Slow incident response | Detect, correlate, and block anomalies in under **30 seconds** |
| Limited kernel visibility | **eBPF** (Linux) and **ETW** (Windows) for deep OS-level telemetry |
| Missed lateral movement | Identity-aware correlation linking auth events to system activity |

---

## 🌠 The Ecosystem

Our architecture is organized into six modules, each named after a star in the Orion constellation:

| Repository | Star Role | Description | License |
|---|---|---|---|
| ⚔️ **Bellatrix** | Protection & Runtime | The *warrior* — Linux (eBPF) and Windows (ETW) agents built in Go | GPLv2 (Open Source) |
| 🔴 **Betelgeuse** | Data Hub & Encryption | The *heart* — Agent hub centralizing data flows, encrypting payloads and relaying via mTLS | Proprietary |
| 🧠 **Meissa** | Intelligence & Detection | The *brain* — Sigma rules engine and AI-driven behavioral models, deployed in a secure enclave | Proprietary |
| 🔗 **Mintaka** | API Gateway | The *gateway* — Dual API layer: ingestion (Betelgeuse → ClickHouse) and output (ClickHouse → Rigel) | Proprietary |
| 🖥️ **Rigel** | Interface & Business | The *eye* — React/Next.js dashboard with D3.js threat graph visualization | Proprietary |
| 🏗️ **Alnilam** | Infrastructure & Cloud | The *backbone* — Terraform/Ansible IaC, CI/CD pipelines, and ClickHouse orchestration | Proprietary |

```
    ┌──────────────────────────────────────────────────────────────────────┐
    │              ┌──────────────┐        ╔════════════════════╗          │
    │              │    Rigel     │        ║  Secure Enclave    ║          │
    │              │  (Next.js)   │        ║ ┌──────────────┐   ║          │
    │              └──────┬───────┘        ║ │    Meissa    │   ║          │
    │                     │ REST / WS      ║ │   (Go/ML)    │   ║          │
    │              ┌──────┴───────┐  gRPC  ║ └──────────────┘   ║          │
    │              │   Mintaka    ├───────►║                    ║          │
    │              │  (APIs/Go)   │        ╚════════════════════╝          │
    │              └──┬───────┬───┘                                        │
    │         Output  │       │  Ingestion                                 │
    │                 │       │                                            │
    │         ┌───────┘       └───────┐                                    │
    │   ┌─────┴────────┐       ┌──────┴───────┐                            │
    │   │  ClickHouse  │◄──────│  Betelgeuse  │  Agent Hub                 │
    │   │   (OLAP)     │       │  (Go/mTLS)   │  Encrypt & Relay           │
    │   └──────────────┘       └──────┬───────┘                            │
    │                                 │ mTLS                               │
    │                    ┌────────────┼───────────┐                        │
    │                    │                        │                        │
    │             ┌──────┴───────┐         ┌──────┴───────┐                │
    │             │  Bellatrix   │         │  Bellatrix   │  Agents        │
    │             │ (Linux/eBPF) │         │ (Windows/ETW)│                │
    │             └──────────────┘         └──────────────┘                │
    └──────────────────────────────────────────────────────────────────────┘
                           │
                    ┌──────┴───────┐
                    │   Alnilam    │  Infrastructure & IaC
                    └──────────────┘
```

---

## 🛠️ Technical Stack

| Layer | Technology |
|---|---|
| **Agents & API** | Go |
| **Kernel Probes** | C / Rust (eBPF programs) |
| **Frontend** | TypeScript, React, Next.js, D3.js, Wails, Go|
| **Data Store** | ClickHouse (OLAP) — sub-second log analysis at scale |
| **Communication** | gRPC secured via mTLS (end-to-end encryption) |
| **Detection** | Sigma Rules engine + AI-powered risk scoring |
| **Infrastructure** | Terraform, Ansible, Docker, GitHub Actions |

---

## 🚀 Getting Started

> **Bellatrix** is the only open-source component. The other modules (Betelgeuse, Meissa, Mintaka, Rigel, Alnilam) are proprietary and available to authorized contributors only.

```bash
# Clone the open-source agent
git clone https://github.com/orion-music/Bellatrix.git
cd Bellatrix

# Build & run the agent
go build ./cmd/agent
./agent --config config.yaml
```

> Refer to the [Bellatrix README](https://github.com/orion-music/Bellatrix) for full setup instructions and contribution guidelines.

---

## 📈 Roadmap

Deployment is structured across four milestones for a controlled, scalable roll-out:

```
  M1                M2                 M3                 M4
  ●─────────────────●──────────────────●──────────────────●
  Mar 2026          Oct 2026           Mar 2027           Jun 2027
```

| Milestone | Codename | Objective | Status |
|---|---|---|---|
| **M1** | The Pulse | POC — Linux agent with file & process monitoring | 🟢 In Progress |
| **M2** | Identity Shield | Windows agent + Active Directory integration | ⬚ Planned |
| **M3** | The Enforcer | Autonomous remediation via Sigma engine | ⬚ Planned |
| **M4** | Global Insight | Multi-tenant SaaS platform & attack graph visualization | ⬚ Planned |

---

## 👥 The Team

| Name | Role | Email |
|---|---|---|
| **Samuel** | Co-Founder · CEO & CISO | samuel.tesson@epitech.eu |
| **Clément** | Co-Founder · CTO & Head of DevOps | clement.talneau@epitech.eu |
| **Matthieu** | AI Engineer | matthieu.guillet-arnaud@epitech.eu |
| **Jocelyn** | Software Engineer | jocelyn.jean-elie@epitech.eu |
| **Ester** | Software Engineer | ester.ngindu-mubiala@epitech.eu |

---

## ⚖️ License

Orion uses a **hybrid licensing** strategy to balance open-source contribution with product protection:

| Component | License |
|---|---|
| **Bellatrix** (Agents & eBPF) | [GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) — Open Source |
| **Betelgeuse** (Agent Hub) | Proprietary |
| **Meissa** (Detection Engine) | Proprietary |
| **Mintaka** (API Gateway) | Proprietary |
| **Rigel** (Dashboard) | Proprietary |
| **Alnilam** (Infrastructure) | Proprietary |

---

<div align="center">

*Built with purpose at [Epitech](https://www.epitech.eu/).*

</div>