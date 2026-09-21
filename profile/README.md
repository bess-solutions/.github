# BESS Solutions

> **Battery Energy Storage Systems (BESS) Orchestration & AI-Augmented Optimization**

BESS Solutions is an open-source engineering ecosystem dedicated to building the future of grid-scale energy storage. We design and implement industrial edge gateways, electrochemical battery simulation models, and predictive dispatch engines that help operators maximize lifecycle economics, ensure regulatory compliance, and stabilize modern grids.

---

## ⚡ Our Core Mission

As renewable energy penetration grows, Battery Energy Storage Systems (BESS) are critical for grid stability. We combine **industrial-grade telemetry** with **physical-informed AI models** to address the major challenges of BESS deployments:
- **Degradation Optimization:** Minimizing cycle-by-cycle aging through electrochemistry-based battery models (LCOS & DCOS).
- **Grid Compliance:** Ensuring rapid frequency response (PFR) and reactive voltage control compliant with Chilean CNE regulations (NTSyCS).
- **Security & Integrity:** Hardening BESS endpoints against cyber attacks under the IEC 62443 standard framework.

---

## 📂 Key Repositories

### 🛠️ [open-bess-edge](https://github.com/bess-solutions/open-bess-edge)
The **BESSAI Edge Gateway** is our flagship industrial passthrough and controller. It bridges substation hardware to dispatch algorithms:
- **Industrial Modbus Engine:** Native high-performance Modbus TCP client with register-level telemetry.
- **Extensible Profile Schema:** Declarative register mapping for multi-vendor hardware. Perfiles con nivel *unverified* (sin certificación en banco físico de pruebas).
- **Standards & Interoperability:** Mapeo de parámetros y requisitos técnicos de la NTSyCS chilena en código comprobable por tests automáticos.
- **Fast-Loop Agents:** Low-latency controllers for active/reactive power ramping and droop responses.
- **Traceability:** Integrated compliance mapping directly from code assertions to regulatory sections.

---

### 🧪 [open-bess-sandbox](https://github.com/bess-solutions/open-bess-sandbox)
Banco de pruebas multicontexto chileno (Utility SSCC, Generación Firme, BTM Peak Shaving, Arbitraje Cliente Libre). Integrado con el motor de `open-bess-edge` para simulación en lazo cerrado y validación regulatoria fail-closed con reglas preliminares clasificadas como SUPUESTO a la espera de auditoría jurídica independiente.

### 📋 [bess-device-profiles](https://github.com/bess-solutions/bess-device-profiles)
Fuente única de verdad (SSOT) de mapas de registros Modbus y CAN en formato JSON Schema abierto, incluyendo bindings canónicos y linters semánticos de longitud de palabra.

### 🕹️ [bess-modbus-simulator](https://github.com/bess-solutions/bess-modbus-simulator)
Servidor Modbus TCP asíncrono para emulación de planta y pruebas Hardware-in-the-Loop (HIL) y CI/CD. Compatible con `pymodbus>=3.9.2`.

### 📚 [awesome-bess](https://github.com/bess-solutions/awesome-bess)
Directorio curado de estándares, papers, herramientas de simulación y código abierto para almacenamiento de energía en baterías.

---

## 🌐 System Integration Architecture

The BESS Solutions edge gateway operates as the central controller on-site, connecting physical assets directly to grid operators and cloud optimization backends:

```mermaid
graph LR
    subgraph Facility ["⚡ BESS Facility (Grid-Connected Storage)"]
        Inverters["🔌 PCS & Inverters (Huawei, SMA, Victron)"]
        Sensors["🌡️ BMS, SoC & Thermal Sensors"]
        Edge["🛡️ open-bess-edge (Local Gateway & SafetyGuard)"]
        
        Inverters --> |Modbus TCP| Edge
        Sensors --> |Modbus TCP| Edge
    end

    subgraph Integration ["☁️ Grid & Cloud Integration"]
        CEN["🏛️ Coordinador Eléctrico Nacional (CEN Telemetry)"]
        Portal["📊 Fleet Management & Dispatch Portal"]
    end

    Edge --> |"IPSec / mTLS Tunnel"| CEN
    Edge --> |"Secure Telemetry (WebSocket/gRPC)"| Portal
```

---

## 📜 Compliance & Safety Focus

We maintain a strict **Zero Mock Data Policy** across our financial and engineering planners. All models are calibrated against real-world grid data, local marginal costs (Cen), and physical battery parameters.
- **IEC 62443 & OT Hardening:** Defense-in-depth architecture, local register bounds validation, rate-limiting, and auditable control logs.
- **NTSyCS (Chile):** Active droop PFR controls (<2s) and ramp constraints (<10%/min) mapped to automated tests.

---

## 🤝 Get Involved & Governance

BESS Solutions is transitioning toward an open, multi-stakeholder governance model:
- **Governance:** Read our [GOVERNANCE.md](https://github.com/bess-solutions/open-bess-edge/blob/main/GOVERNANCE.md) to understand roles, TSC (Technical Steering Committee) composition, and the BEP (BESSAI Enhancement Proposal) process.
- **Security:** To report vulnerabilities safely, consult our [SECURITY.md](https://github.com/bess-solutions/open-bess-edge/blob/main/SECURITY.md).

---
*BESS Solutions SpA — Santiago / Linares, Chile — contacto@bess-solutions.cl*
