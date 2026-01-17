# Architecture Documentation

## Overview
This repository contains the architecture design for a secure, multi-tenant payment platform consisting of an **Admin System** and **Merchant System** with integrated blockchain payment processing.

The design implements a production-ready architecture based on the provided requirements, featuring:
- **Separation of admin and merchant concerns**
- **Multi-tenant merchant portal with data isolation**
- **Private blockchain infrastructure with controlled access**
- **Four-tier network architecture with defense-in-depth security**

---

## Repository Structure

📁 **Root**
├── [`README.md`](README.md)  
│   └── *Repository overview, navigation guide, and quick start instructions*

📁 **docs/**  
├── [`c4_context.png`](docs/c4_context.png)  
│   └── 🖼️ **C4 Context Diagram** – High-level system view with external actors and core systems  
├── [`c4_container.png`](docs/c4_container.png)  
│   └── 🖼️ **C4 Container Diagram** – Internal component breakdown (9 containers, protocols, data flow)  
├── [`network_topology.png`](docs/network_topology.png)  
│   └── 🖼️ **Network Topology** – VPC layout, four-tier subnets, security groups, and isolation zones  
└── [`summary.md`](docs/summary.md)  
    └── 📄 **Complete Architecture Documentation** – Design rationale, workflows, security model, and compliance checklist

---

## Quick Start
For reviewers and stakeholders:

1. **Start here**: Read [`docs/summary.md`](docs/summary.md) for the complete architecture documentation  
   - Contains detailed explanations of all design decisions  
   - Includes references to original architecture requirements  
   - Covers security model, authentication strategy, and compliance  

2. **Then view diagrams in the following order**:  
   - [`docs/c4_context.png`](docs/c4_context.png) – High-level system view (external actors and core systems)  
   - [`docs/c4_container.png`](docs/c4_container.png) – Internal component structure (9 containers with protocols)  
   - [`docs/network_topology.png`](docs/network_topology.png) – Infrastructure layout (VPC, subnets, security groups)  

3. **Cross-reference**: Each diagram is explained in detail within `summary.md` with architecture rationale.

>  **Estimated review time**: 15–20 minutes for complete understanding.

---

## Key Architecture Decisions
- **Database Strategy**: Separate `AdminDB` and `MerchantDB` with a single physical database for merchants using row-level security (`merchant_id` isolation).

- **Blockchain Access**: Fixed routing path (**Merchant API → Payment Processor → Indexer → Bitcoin Node**) with no direct UI or Admin access.

- **Network Segmentation**: Four-tier subnet architecture (**Public**, **API**, **DB**, **Blockchain**) for defense-in-depth security.

- **Authentication**: Multi-layer approach:
  - JWT for UI ↔ API communication
  - OAuth2 + mTLS for inter-system (Admin ↔ Merchant) provisioning
  - Host-based verification for merchant subdomains

- **Containerization Strategy**: 9 Docker containers with separate processes, isolated secrets, and independent deployment units to enable failure isolation and scaling.

---

## Documentation

### Primary Documentation
 **File**: [`docs/summary.md`](docs/summary.md)  
- Complete architecture documentation  
- Design rationale for each component  
- Security model and authentication strategies  
- End-to-end system workflows (merchant onboarding, payment processing)  
- Compliance checklist against “Architecture.pdf” requirements  

### Visual Diagrams
 **Location**: [`docs/`](docs/) folder  
- Follows **C4 model standards** (Context and Container levels)  
- Network topology adheres to cloud infrastructure best practices  
- Every diagram is fully explained in `summary.md` with security and operational rationale  

>  **Note**: This architecture design was created as part of a technical assessment. All diagrams follow C4 model standards and cloud network security best practices.



