# JFXOSMS — Open-Source Alternative Integration Architecture

> **Project focus:** AI-Powered Microfactory Simulation Platform  
> **Architecture goal:** reorganize the software alternatives listed in the source project into interoperable building blocks for microfactory design, additive/subtractive manufacturing, robotics, process simulation, digital twins, IIoT, MES/OEE/CMMS, scheduling, and AI-assisted engineering.

---

## 1. Source Project Direction

The source repository defines **JFXOSMS** as an **AI-Powered Microfactory Simulation Platform**.

Its software list covers a broad microfactory lifecycle:

- drone / robotic platform concepts;
- CNC simulation and computer-aided machining;
- additive-manufacturing slicing and toolpath planning;
- hybrid additive/subtractive manufacturing;
- G-code visualization;
- additive-manufacturing simulation;
- alloy solidification and microstructure simulation;
- peridynamics;
- selective-laser-melting integration;
- welding / additive-manufacturing modelling;
- EAM / CMMS / OEE;
- Digital Twin as a Service;
- FMU-based digital twins;
- discrete-event factory simulation;
- IIoT connectivity and process-data twins;
- physical-world deployment and coordination;
- production/logistics twins;
- warehouse/manufacturing development frameworks;
- factory automation simulation;
- robotic microfactory cells;
- manufacturing execution and performance monitoring.

The source repository also maintains the engineering lifecycle:

```text
MBSE → CAD → CAM → CAS
```

with Arcadia/Capella-oriented MBSE, CAD for computer-aided design, CAM for manufacturing/assembly, and CAS for end-to-end simulation and performance analysis.

---

# 2. Integration Strategy

The software list should not be deployed as a monolithic stack.

The preferred approach is to organize it into **replaceable building blocks** connected by stable interfaces:

```text
Product / Production Requirements
              ↓
        MBSE / Architecture
              ↓
       CAD / Part Definition
              ↓
     Manufacturing Planning
              ↓
 ┌────────────┼─────────────┐
 ↓            ↓             ↓
Additive    CNC/Milling   Robotic Assembly
 ↓            ↓             ↓
Toolpaths   G-code        Robot Tasks
 └────────────┼─────────────┘
              ↓
      Process Simulation
              ↓
      Factory Simulation
              ↓
      Digital Twin / IIoT
              ↓
 MES / OEE / CMMS / Maintenance
              ↓
      AI Optimization Layer
              ↓
    Physical Microfactory
```

The core principle is:

> **Simulate first, validate digitally, deploy through controlled industrial interfaces, and use AI as an optimization and engineering-assistance layer rather than as an unrestricted machine controller.**

---

# 3. Alternative Building-Block Architecture

```text
┌─────────────────────────────────────────────────────────────────────────┐
│                    PRODUCT & SYSTEM ENGINEERING                         │
│ Requirements | Arcadia/Capella | MBSE | CAD Models | Process Plans    │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                  AI ENGINEERING / PLANNING LAYER                        │
│ Design Copilot | RAG | Agent Workflows | Optimization | Scheduling    │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
             ┌──────────────────┼───────────────────┐
             │                  │                   │
             v                  v                   v
┌───────────────────┐ ┌────────────────────┐ ┌───────────────────────────┐
│ ADDITIVE / SLICER │ │ CNC / SUBTRACTIVE  │ │ ROBOTIC MICROFACTORY     │
│ ORNLSlicer        │ │ CAMotics           │ │ open-microfactory         │
│ IceSL-vrprinter   │ │ CAM / G-code       │ │ Open Drone project       │
│ libSLM            │ │ ASMBL milling      │ │ manipulation / mobility  │
└─────────┬─────────┘ └─────────┬──────────┘ └────────────┬──────────────┘
          │                     │                         │
          └─────────────────────┼─────────────────────────┘
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                MANUFACTURING PROCESS PHYSICS / V&V                      │
│ JAX AM Simulation | ExaCA | PeriLab | SLM/Weld Models                 │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                   FACTORY / LOGISTICS SIMULATION                        │
│ FactorySimPy | DES | Open Factory Twin | Factory I/O*                 │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                   DIGITAL TWIN & CO-SIMULATION                          │
│ OpenTwin | CoFmuPy | DTaaS | FMU/FMI | Process Data Twin             │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                       IIoT / EDGE PLATFORM                              │
│ IndustryFusion | OpenFactory | Open Industry Project                  │
│ Asset APIs | Telemetry | Event Streams | Device Coordination          │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                 PRODUCTION OPERATIONS / ASSET MGMT                      │
│ Libre | BaseEAM | OEE/CMMS | Maintenance & Efficiency Platforms       │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                 DATA / AI / OBSERVABILITY / OPTIMIZATION                │
│ RAG | Local AI | Forecasting | Anomaly Detection | Scheduling         │
│ PostgreSQL | Time-Series | Grafana | MLflow | OpenTelemetry           │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
                                v
┌─────────────────────────────────────────────────────────────────────────┐
│                  DEPLOYMENT / INDUSTRIAL DEVOPS                         │
│ Linux | Docker | Kubernetes/k3s | GitOps | Edge Nodes | CI/CD         │
└─────────────────────────────────────────────────────────────────────────┘
```

`* Factory I/O is useful as an external industrial-automation simulation reference, but should not be classified as part of the open-source core without appropriate licensing.`

---

# 4. Category A — Additive Manufacturing Toolpath Planning

## ORNLSlicer

**Source role:** open-source slicing and toolpath planning framework.

### Recommended position

```text
CAD / Mesh
    ↓
ORNLSlicer
    ↓
Toolpath
    ↓
AM Simulation
    ↓
Machine Adapter
```

### Strategic value

**5/5 — Core candidate**

Why it matters:

- directly supports additive toolpath generation;
- bridges CAD and CAM;
- suitable for modular machine exporters;
- useful for FDM/DED-oriented research and production workflows.

### Architectural classification

**Primary Open-Source Additive Toolpath Engine**

---

## IceSL-vrprinter

**Source role:** G-code visualizer and simulator.

### Strategic value

**3/5 — Validation / visualization candidate**

Best for:

- G-code visualization;
- toolpath inspection;
- pre-deployment verification;
- operator training.

Recommended as a complementary viewer rather than the main manufacturing kernel.

---

## libSLM

**Source role:** C++ library for generating and transferring data to SLM machine systems.

### Strategic value

**4/5 — Specialized metal-AM integration candidate**

Best fit:

```text
Part / Process Definition
        ↓
SLM Toolpath/Data
        ↓
libSLM
        ↓
Machine Adapter
```

Use behind a machine-neutral interface because SLM hardware integration can vary substantially between vendors.

---

# 5. Category B — CNC / Subtractive Manufacturing

## CAMotics

**Source role:** open-source CNC simulation and computer-aided machining reference.

### Strategic value

**5/5 — Core CNC simulation candidate**

Best for:

- 3-axis G-code simulation;
- toolpath visualization;
- CNC verification;
- manufacturing education;
- digital validation before machining.

Recommended role:

```text
CAM / G-code
      ↓
CAMotics
      ↓
Virtual Machining
      ↓
Validated NC Program
```

CAMotics should be treated principally as a **simulation/verification engine**, not as the sole production CAM engine.

---

# 6. Category C — Hybrid Additive + Subtractive Manufacturing

## ASMBL

**Source role:** manufacturing technique combining FDM 3D printing with traditional milling.

### Strategic value

**4/5 — Strategic hybrid-manufacturing research block**

Architecture:

```text
Additive Build
      ↓
Intermediate Geometry
      ↓
Milling / Finishing
      ↓
Inspection
```

JFXOSMS can use ASMBL concepts to model hybrid cells in which additive and subtractive processes are coordinated by one manufacturing plan.

---

# 7. Category D — Additive-Manufacturing Physics

## Additive Manufacturing Simulation with JAX

**Source role:** JAX-based additive-manufacturing simulation.

### Strategic value

**4/5 — AI/HPC simulation candidate**

Potential advantages:

- differentiable numerical workflows;
- GPU/accelerator execution;
- integration with optimization;
- surrogate-model development;
- parameter estimation.

Recommended role:

```text
Process Parameters
       ↓
JAX Simulation
       ↓
Thermal / Process Response
       ↓
Optimization / Calibration
```

Exact upstream project and licensing should be documented before promotion to a production dependency.

---

## ExaCA

**Source role:** cellular-automata code for alloy nucleation and solidification.

### Strategic value

**5/5 — High-value materials/process simulation**

Best for:

- microstructure evolution;
- alloy solidification;
- additive-manufacturing materials research;
- multiscale process validation.

Suggested integration:

```text
AM Thermal History
       ↓
ExaCA
       ↓
Microstructure Prediction
       ↓
Quality / Property Model
```

---

## PeriLab

**Source role:** peridynamics software.

### Strategic value

**4/5 — Structural/failure simulation candidate**

Potential use:

- damage;
- fracture;
- material failure;
- nonlocal mechanics;
- manufacturing-induced defects.

It complements conventional FEM rather than replacing all structural simulation.

---

# 8. Category E — Welding / AM Modelling

## Abaqus WeldToolkit

The source repository lists **Abaqus WeldToolkit** for welding and additive-manufacturing modelling.

Because it depends on the Abaqus ecosystem, it should be kept outside the open-source core.

### Classification

**External Commercial / Validation Reference**

Recommended open architecture:

```text
Common Process Model
        |
        +---- Open Solver / Research Model
        |
        +---- Optional Abaqus Validation Adapter
```

This preserves reproducibility without making a commercial solver mandatory.

---

# 9. Category F — Robotics & Physical Microfactory

## open-microfactory

**Source role:** open-source robotic assembly cell for dexterous manipulation.

### Strategic value

**5/5 — Primary robotic microfactory candidate**

Recommended use:

- robotic assembly;
- manipulation;
- autonomous cell experimentation;
- task execution;
- physical validation of digital manufacturing workflows.

Architecture:

```text
Manufacturing Order
       ↓
Task Planner
       ↓
Robot Skill
       ↓
open-microfactory
       ↓
Sensors / Actuators
```

---

## Open Drone Project

The repository lists **The Open Drone project** without enough source detail to uniquely identify its upstream implementation.

### Classification

**Research / Mobility / Inspection Candidate — upstream verification required**

Possible architectural role, if confirmed:

- indoor logistics;
- inspection;
- inventory;
- visual monitoring;
- mobile sensing.

Do not hard-code this block until the exact project and license are identified.

---

# 10. Category G — Factory Discrete-Event Simulation

## FactorySimPy

**Source role:** Python library for manufacturing-system discrete-event simulation.

### Strategic value

**5/5 — Primary open factory-flow simulator**

Recommended for:

- machines;
- buffers;
- conveyors;
- fleets;
- production throughput;
- bottleneck analysis;
- resource utilization;
- line balancing;
- digital-twin experimentation.

Architecture:

```text
Production Configuration
        ↓
FactorySimPy
        ↓
Events / KPI / State
        ↓
Optimization
        ↓
Candidate Production Plan
```

It is an excellent bridge between microfactory topology and AI optimization.

---

## Generic Discrete-Event Simulation

The source also references simulation of manufacturing or service processes using DES.

### Classification

**Core Methodology**

The architecture should expose a generic DES interface so FactorySimPy can be replaced or complemented by another compatible engine.

---

# 11. Category H — Digital Twin

## OpenTwin

**Source role:** open-source platform supporting development and operation of digital twins.

### Strategic value

**5/5 — Strategic Digital Twin Platform Candidate**

Recommended position:

```text
Physical Assets
      ↕
Telemetry / Commands
      ↕
OpenTwin
      ↕
Simulation / Analytics / AI
```

---

## CoFmuPy

**Source role:** Python library for rapid prototyping of digital twins.

### Strategic value

**5/5 — Lightweight FMU/Digital-Twin integration candidate**

Best use:

- FMI/FMU experimentation;
- rapid digital-twin composition;
- simulation service integration;
- Python-driven orchestration.

Recommended as the lightweight **co-simulation adapter layer**.

---

## Digital Twin as a Service (DTaaS)

The source lists a DTaaS project/concept but does not uniquely identify its upstream implementation.

### Classification

**Architecture Pattern / Candidate Platform — upstream verification required**

Recommended role:

```text
Twin Model
   +
Telemetry
   +
Simulation
   ↓
DTaaS API
   ↓
Applications / AI / Dashboards
```

---

# 12. Category I — Production & Logistics Twin

## Open Factory Twin

**Source role:** digital twin for production and logistics environments.

### Strategic value

**4/5 — Strategic factory/logistics twin candidate**

Best use:

- material flow;
- asset state;
- production operations;
- logistics;
- synchronized factory simulation.

---

## IndustryFusion Process Data Twin Architecture

**Source role:** process-data twin architecture.

### Strategic value

**5/5 — Industrial semantic/data-twin integration candidate**

Recommended as the semantic/data backbone connecting physical assets, IIoT data, and higher-level AI applications.

---

# 13. Category J — IIoT & Smart Factory Connectivity

## IndustryFusion

**Source role:** open-source IIoT connectivity for smart products and smart factories.

### Strategic value

**5/5 — Primary IIoT integration candidate**

Recommended for:

- asset connectivity;
- edge data;
- semantic digital twins;
- industrial interoperability;
- smart-factory integration.

Architecture:

```text
Machine / Robot / Sensor
          ↓
     Edge Connector
          ↓
    IndustryFusion
          ↓
 Process Data Twin
          ↓
 AI / MES / Analytics
```

---

# 14. Category K — Physical-World Deployment

## OpenFactory

**Source role:** deployment and coordination platform for the physical world.

### Strategic value

**5/5 — Strategic Industrial DevOps / Coordination Candidate**

Recommended function:

- declarative asset configuration;
- simulation-before-deployment;
- repeatable deployment;
- coordination of distributed assets;
- GitOps-style traceability.

Architecture:

```text
Git / Configuration
       ↓
Validation / Simulation
       ↓
OpenFactory
       ↓
Industrial Assets
       ↓
Telemetry / Audit
```

This is a strong candidate for the **physical deployment control plane**.

---

# 15. Category L — Manufacturing Application Framework

## Open Industry Project

**Source role:** free/open-source warehouse/manufacturing development framework.

### Strategic value

**4/5 — Business/process application framework candidate**

Potential use:

- warehouse workflows;
- manufacturing applications;
- inventory;
- operations UI;
- integration services.

Exact upstream API and maturity should be validated before selecting it as a core dependency.

---

# 16. Category M — MES / OEE / Operations

## Libre

**Source role:** open-source manufacturing execution and performance monitoring.

### Strategic value

**5/5 — MES / performance candidate**

Best architectural role:

```text
Production Orders
       ↓
MES
       ↓
Machine / Cell Execution
       ↓
Production Events
       ↓
OEE / Analytics
```

---

## Manufacturing Efficiency & Maintenance Management Platform

The source includes this as a platform reference but does not uniquely identify the upstream project.

### Classification

**MES/OEE/CMMS Candidate — exact project verification required**

---

## OEE and CMMS Software for Machine Manufacturers

### Classification

**Maintenance / OEE Candidate — upstream verification required**

Potential functionality:

- availability;
- performance;
- quality;
- downtime;
- maintenance events;
- equipment history.

---

# 17. Category N — Enterprise Asset & Maintenance Management

## BaseEAM

**Source role:** EAM/CMMS.

### Strategic value

**4/5 — EAM / CMMS core candidate**

Use for:

- assets;
- work orders;
- preventive maintenance;
- breakdown history;
- spare parts;
- equipment lifecycle.

Architecture:

```text
Machine Twin
    ↓
Condition / Runtime
    ↓
Maintenance Rule
    ↓
BaseEAM
    ↓
Work Order
```

---

# 18. Factory I/O

The source lists **Factory I/O** as a 3D factory simulator for learning automation technologies.

It is technically valuable, especially for PLC/automation simulation, but its official product model uses commercial editions/licenses.

### Classification

**External Commercial Training / Validation Reference**

It should therefore be integrated only through an optional adapter:

```text
Automation Scenario
        |
        +---- Open Simulation Core
        |
        +---- Factory I/O Adapter (optional)
```

This keeps the main JFXOSMS architecture open.

---

# 19. Proposed Open-Source AI Integration Layer

The source list is strong in manufacturing and simulation but can benefit from a unifying AI architecture.

The following components are **proposed complementary integrations**, not claims about existing source dependencies:

- LangGraph — agent/workflow orchestration;
- MCP — bounded tool interoperability;
- Qdrant — engineering RAG;
- PostgreSQL — structured operational/state data;
- Open WebUI — optional engineering AI portal;
- FastAPI — model and simulation APIs;
- Ollama / llama.cpp — local inference;
- vLLM — private high-throughput inference;
- gpt-oss-20b — optional local open-weight reasoning model;
- gpt-oss-120b — optional private-server reasoning tier;
- MLflow — AI/optimization experiment tracking;
- OpenTelemetry / Prometheus / Grafana — observability.

---

# 20. AI Engineering Copilot

```text
Engineer / Operator
        |
        v
AI Engineering Copilot
        |
  +-----+----------------+----------------+
  |                      |                |
  v                      v                v
RAG                  Planning Agent   Analytics Agent
  |                      |                |
  +----------------------+----------------+
                         |
                         v
                   Tool Gateway / MCP
                         |
       +-----------------+------------------+
       |                 |                  |
       v                 v                  v
  ORNLSlicer         FactorySimPy       OpenTwin
  CAMotics           CoFmuPy            BaseEAM
  ExaCA              OpenFactory        MES/OEE
```

Recommended AI uses:

- manufacturing-plan assistance;
- retrieval of machine manuals and process specifications;
- toolpath parameter suggestions;
- scenario generation;
- production schedule optimization;
- anomaly explanation;
- predictive-maintenance support;
- root-cause-analysis assistance;
- digital-twin query;
- simulation orchestration;
- engineering report generation.

---

# 21. AI Safety / Control Boundary

Generative AI should **not** directly manipulate raw actuators.

Preferred flow:

```text
AI Agent
   ↓
Validated Manufacturing Intent
   ↓
Policy / Safety Gate
   ↓
Manufacturing Service
   ↓
Robot / CNC / AM Controller
```

Not:

```text
LLM
 ↓
raw spindle / motor / heater command
```

Hard real-time and safety-critical machine control should remain deterministic and independently validated.

---

# 22. Local AI Model Routing

```text
Engineering Request
       |
       v
   Model Router
       |
 +-----+----------------+----------------+
 |                      |                |
 v                      v                v
Local                 Private         Deterministic
gpt-oss-20b           gpt-oss-120b   Solver / Simulator
Ollama/llama.cpp      vLLM           CAMotics / ExaCA /
                                      FactorySimPy / Twin
```

Routing rules:

- use deterministic simulation for manufacturing physics;
- use local LLMs for private documentation/RAG;
- use high-capacity private inference for complex reasoning;
- keep cloud inference optional;
- log all model/tool decisions.

---

# 23. Digital Thread Architecture

A microfactory needs a continuous engineering-to-production information chain.

```text
Requirements
    ↓
MBSE
    ↓
CAD
    ↓
CAM / Slicing
    ↓
Manufacturing Process Model
    ↓
Machine / Robot Program
    ↓
Simulation
    ↓
Deployment
    ↓
Production
    ↓
Telemetry
    ↓
Digital Twin
    ↓
MES / OEE / CMMS
    ↓
AI Optimization
    ↓
Updated Engineering Decision
```

---

# 24. Alternative Architecture Profiles

## Profile A — Additive Microfactory

```text
CAD
 ↓
ORNLSlicer
 ↓
JAX AM Simulation
 ↓
ExaCA
 ↓
libSLM / Machine Adapter
 ↓
OpenTwin
 ↓
IndustryFusion
 ↓
MES / OEE
```

**Best for:** additive and metal-AM research/production cells.

---

## Profile B — Hybrid Additive / CNC

```text
CAD
 ↓
ORNLSlicer
 ↓
Additive Process
 ↓
ASMBL Workflow
 ↓
CNC Program
 ↓
CAMotics Validation
 ↓
Physical Cell
```

**Best for:** hybrid manufacturing and precision finishing.

---

## Profile C — Robotic Microfactory

```text
Production Order
       ↓
FactorySimPy
       ↓
Task Planning
       ↓
open-microfactory
       ↓
OpenFactory
       ↓
IndustryFusion
       ↓
OpenTwin
```

**Best for:** flexible robotic assembly cells.

---

## Profile D — Digital-Twin Factory

```text
Physical Assets
      ↓
IndustryFusion
      ↓
Process Data Twin
      ↓
OpenTwin / CoFmuPy
      ↓
FactorySimPy
      ↓
AI Analytics
      ↓
MES / BaseEAM
```

**Best for:** operations, predictive maintenance and performance optimization.

---

## Profile E — Fully Open Microfactory Research Stack

```text
Capella
  ↓
CAD Model
  ↓
ORNLSlicer / CAMotics
  ↓
ExaCA / PeriLab
  ↓
FactorySimPy
  ↓
OpenFactory
  ↓
IndustryFusion
  ↓
OpenTwin / CoFmuPy
  ↓
Libre / BaseEAM
  ↓
Open AI Layer
```

**Best for:** research and education with minimal proprietary lock-in.

---

# 25. Strategic Prioritization

## Priority 1 — Core / Highest Value

- ORNLSlicer
- CAMotics
- FactorySimPy
- IndustryFusion
- OpenFactory
- OpenTwin
- CoFmuPy
- open-microfactory

These form the strongest backbone for an open microfactory platform.

---

## Priority 2 — Process / Physics Extensions

- ExaCA
- PeriLab
- JAX additive-manufacturing simulation
- libSLM
- ASMBL
- IceSL-vrprinter

---

## Priority 3 — Operations / Enterprise Extensions

- Libre
- BaseEAM
- Open Factory Twin
- IndustryFusion Process Data Twin
- Open Industry Project
- OEE/CMMS platforms

---

## Priority 4 — Optional / Research / External

- Open Drone project — exact upstream verification
- Digital Twin as a Service — exact upstream verification
- generic Manufacturing Efficiency & Maintenance platform — exact upstream verification
- Factory I/O — commercial external reference
- Abaqus WeldToolkit — commercial external reference

---

# 26. Value Matrix

| Component | Domain | Strategic Value | Preferred Role |
|---|---|---:|---|
| ORNLSlicer | Additive CAM | 5/5 | Primary slicer/toolpath |
| CAMotics | CNC Simulation | 5/5 | CNC verification |
| ASMBL | Hybrid Manufacturing | 4/5 | Additive/subtractive workflow |
| IceSL-vrprinter | G-code | 3/5 | Visualization/verification |
| JAX AM Simulation | AM Physics/AI | 4/5 | Differentiable process simulation |
| ExaCA | Materials | 5/5 | Solidification/microstructure |
| PeriLab | Mechanics | 4/5 | Damage/fracture |
| libSLM | Metal AM | 4/5 | SLM machine integration |
| Abaqus WeldToolkit | Welding/AM | 2/5 open-stack fit | External validation |
| BaseEAM | EAM/CMMS | 4/5 | Asset maintenance |
| OEE/CMMS software | Operations | 4/5 | Performance/maintenance |
| DTaaS | Digital Twin | 4/5 | Service pattern |
| CoFmuPy | Digital Twin/FMU | 5/5 | Lightweight twin integration |
| OpenTwin | Digital Twin | 5/5 | Twin platform |
| FactorySimPy | DES | 5/5 | Production-flow simulation |
| IndustryFusion | IIoT | 5/5 | Connectivity/data twin |
| IndustryFusion PDT | Data Twin | 5/5 | Semantic process-data twin |
| OpenFactory | Industrial DevOps | 5/5 | Deployment/coordination |
| Open Factory Twin | Factory Twin | 4/5 | Production/logistics twin |
| Open Industry Project | Manufacturing Apps | 4/5 | Warehouse/manufacturing framework |
| Factory I/O | Automation Simulation | 2/5 open-stack fit | External training adapter |
| open-microfactory | Robotics | 5/5 | Robotic assembly |
| Libre | MES/OEE | 5/5 | Execution/performance |
| Manufacturing Efficiency Platform | MES/CMMS | 3/5 | Candidate pending upstream |
| Generic DES | Simulation | 5/5 methodology | Replaceable simulation contract |
| Open Drone project | Robotics/Mobility | 3/5 | Research pending upstream |

---

# 27. Recommended MVP

The MVP should integrate only the minimum components needed to demonstrate the complete digital thread.

```text
Product / Part Definition
        ↓
ORNLSlicer OR CNC G-code
        ↓
CAMotics / Toolpath Validation
        ↓
FactorySimPy
        ↓
OpenTwin / CoFmuPy
        ↓
IndustryFusion
        ↓
OpenFactory
        ↓
Libre / BaseEAM
        ↓
AI Engineering Copilot
```

### MVP Capabilities

- define a microfactory process;
- generate or ingest manufacturing toolpaths;
- validate CNC/additive paths;
- simulate production flow;
- model machines, queues, conveyors and robotic fleets;
- expose factory telemetry;
- maintain a synchronized digital-twin representation;
- deploy validated configurations;
- calculate production KPIs;
- track maintenance;
- query the factory through an AI/RAG interface;
- compare alternative schedules/configurations.

---

# 28. MVP Phase 2 — Robotic Cell

Add:

```text
open-microfactory
      +
OpenFactory
      +
IndustryFusion
      +
OpenTwin
```

Capabilities:

- digital robot/cell definition;
- simulation-before-deployment;
- task execution through bounded interfaces;
- telemetry capture;
- twin synchronization;
- performance analysis.

---

# 29. MVP Phase 3 — Advanced Additive Manufacturing

Add:

```text
ORNLSlicer
   +
JAX AM Simulation
   +
ExaCA
   +
PeriLab
   +
libSLM
```

This creates a multi-scale chain:

```text
Geometry
  ↓
Toolpath
  ↓
Thermal / Process Simulation
  ↓
Solidification / Microstructure
  ↓
Damage / Structural Assessment
  ↓
Machine Execution
```

---

# 30. Recommended Interfaces

To preserve replaceability:

| Boundary | Preferred Contract |
|---|---|
| CAD → CAM | STEP/STL/3MF + metadata |
| CAM → machine | G-code / machine adapter |
| Simulation → Twin | FMI/FMU, REST, events |
| Machine → IIoT | MQTT / OPC UA / adapters |
| Twin → AI | REST/OpenAPI/MCP |
| MES → Twin | Events / API |
| CMMS → Asset | Asset IDs / work-order API |
| AI → Tool | MCP / bounded service API |
| Deployment → Asset | Declarative config / GitOps |
| Analytics → Data | SQL / Parquet / time-series API |

Specific protocol choices must be validated against each upstream component.

---

# 31. MBSE → CAD → CAM → CAS Mapping

```text
MBSE
Arcadia / Capella
System, factory and cell architecture
         ↓
CAD
Parts, fixtures, cells and layouts
         ↓
CAM
ORNLSlicer / CNC programs / ASMBL
         ↓
CAS
CAMotics
FactorySimPy
ExaCA / PeriLab
OpenTwin / CoFmuPy
         ↓
Physical Deployment
OpenFactory / IndustryFusion
```

This preserves the project structure while making CAS a true **multi-domain simulation and digital-twin layer**.

---

# 32. Suggested Repository Structure

```text
jfxosms/
├── README.md
├── docs/
│   ├── architecture/
│   ├── compendium/
│   ├── digital-thread/
│   ├── ai/
│   ├── iiot/
│   ├── manufacturing/
│   └── validation/
│
├── MBSE/
│   ├── Capella/
│   ├── CAD/
│   ├── CAM/
│   └── CAS/
│
├── manufacturing/
│   ├── additive/
│   │   ├── ornlslicer/
│   │   ├── exaca/
│   │   ├── perilab/
│   │   └── libslm/
│   ├── cnc/
│   │   └── camotics/
│   └── hybrid/
│       └── asmbl/
│
├── robotics/
│   ├── open-microfactory/
│   └── drone/
│
├── simulation/
│   ├── factorysimpy/
│   ├── des/
│   ├── process-physics/
│   └── validation/
│
├── digital-twin/
│   ├── opentwin/
│   ├── cofmupy/
│   ├── factory-twin/
│   └── dtaas/
│
├── industrial-platform/
│   ├── industryfusion/
│   ├── openfactory/
│   └── open-industry/
│
├── operations/
│   ├── mes/
│   ├── oee/
│   └── cmms/
│
├── ai/
│   ├── agents/
│   ├── rag/
│   ├── model-router/
│   └── optimization/
│
└── tests/
    ├── simulation/
    ├── manufacturing/
    ├── twin/
    └── integration/
```

---

# 33. Roadmap

## Phase 1 — Digital Manufacturing Foundation
- MBSE mapping;
- ORNLSlicer;
- CAMotics;
- common manufacturing data model.

## Phase 2 — Factory Simulation
- FactorySimPy;
- DES abstractions;
- KPI framework.

## Phase 3 — Digital Twin
- OpenTwin;
- CoFmuPy;
- FMI/FMU;
- telemetry model.

## Phase 4 — IIoT
- IndustryFusion;
- Process Data Twin;
- machine/asset adapters.

## Phase 5 — Physical Deployment
- OpenFactory;
- declarative asset configuration;
- simulation-before-deployment.

## Phase 6 — Operations
- Libre;
- BaseEAM;
- OEE/CMMS;
- work-order and maintenance integration.

## Phase 7 — Robotic Microfactory
- open-microfactory;
- task planning;
- bounded physical execution.

## Phase 8 — Advanced AM Physics
- JAX simulation;
- ExaCA;
- PeriLab;
- libSLM.

## Phase 9 — AI Optimization
- RAG;
- agent orchestration;
- local/private inference;
- scheduling;
- anomaly detection;
- predictive maintenance.

---

# 34. Final Alternative Architecture

```text
                      JFXOSMS
                         |
              AI ENGINEERING COPILOT
                         |
                 MBSE / DIGITAL THREAD
                         |
       +-----------------+------------------+
       |                 |                  |
       v                 v                  v
 ADDITIVE CAM         CNC CAM           ROBOTICS
 ORNLSlicer          CAMotics       open-microfactory
       |                 |                  |
       +-----------------+------------------+
                         |
                         v
              PROCESS PHYSICS / V&V
            JAX / ExaCA / PeriLab
                         |
                         v
               FACTORY SIMULATION
                  FactorySimPy
                         |
                         v
                  DIGITAL TWIN
              OpenTwin / CoFmuPy
                         |
                         v
             INDUSTRIAL DATA / IIoT
                 IndustryFusion
                         |
                         v
              PHYSICAL DEPLOYMENT
                   OpenFactory
                         |
                         v
             MES / OEE / MAINTENANCE
               Libre / BaseEAM
                         |
                         v
                AI OPTIMIZATION LOOP
```

---

# 35. Strategic Recommendation

The strongest **open architecture backbone** from the source list is:

```text
ORNLSlicer
    +
CAMotics
    +
FactorySimPy
    +
OpenTwin / CoFmuPy
    +
IndustryFusion
    +
OpenFactory
    +
open-microfactory
    +
Libre / BaseEAM
```

with **ExaCA, PeriLab, JAX AM simulation and libSLM** added when advanced additive-manufacturing physics is required.

**Factory I/O** and **Abaqus WeldToolkit** should remain external validation/training integrations rather than mandatory core components, preserving an architecture that can be independently implemented with open alternatives.

The recommended design principle is:

> **Model the factory as a digital thread of replaceable services: design → manufacture → simulate → twin → deploy → operate → optimize.**

---

# 36. Disclaimer

This document is a proposed engineering integration architecture derived from the alternatives listed in the JFXOSMS source README.

It does not claim that all listed upstream projects are currently integrated, mutually compatible, production-ready, actively maintained, or covered by identical licenses.

For ambiguous source-list entries, the exact upstream repository and license must be identified before implementation.

Manufacturing simulations, toolpaths, robotic workflows, AI recommendations, digital twins, and automated deployments require independent validation before operational or safety-critical use.
