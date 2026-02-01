# TCAD-Resources
> A curated collection of TCAD learning resources, tutorials, and references

---

## Table of Contents
- [What is TCAD?](#what-is-tcad)
- [Synopsys Sentaurus Tutorials & Training](#synopsys-sentaurus-tutorials--training)
- [Open-Source TCAD Simulators](#open-source-tcad-simulators)
- [Radiation Hardening with TCAD](#radiation-hardening-with-tcad)
- [Ferroelectric & Oxide Semiconductor Simulation](#ferroelectric--oxide-semiconductor-simulation)
- [Meshing & Material Parameters](#meshing--material-parameters)
- [Key References & Papers](#key-references--papers)
- [Getting Started Checklist](#getting-started-checklist)

---

## What is TCAD?

**Technology Computer-Aided Design (TCAD)** refers to the use of computer simulations to develop and optimize semiconductor processing technologies and devices. TCAD tools solve the fundamental semiconductor physics equations (drift-diffusion, Poisson, continuity) on a mesh to predict device behavior *before* fabrication.

### Core Capabilities
- **Process Simulation** — Model fabrication steps: implantation, diffusion, oxidation, etching, deposition
- **Device Simulation** — Predict electrical, thermal, and optical characteristics of semiconductor devices
- **Radiation Effects Modeling** — Simulate Single Event Effects (SEE) and Total Ionizing Dose (TID) in harsh environments
- **Novel Materials** — Define and simulate custom material parameters for ferroelectrics, wide-bandgap semiconductors, and oxide semiconductors

---

## Synopsys Sentaurus Tutorials & Training

Synopsys Sentaurus is the **industry-standard** TCAD suite. The following resources cover the core tool flow.

### Official Training & Self-Service
| Resource | Description | URL |
|----------|-------------|-----|
| **Sentaurus Self-Training Guide** | Official Synopsys tutorial index and self-training modules | [SolvNetPlus (requires account)](https://solvnetplus.synopsys.com/s/article/TCAD-Sentaurus-Tutorials-and-Self-Training-Guide) |
| **Synopsys TCAD Main Page** | Product suite overview, tool descriptions | [synopsys.com/manufacturing/tcad](https://www.synopsys.com/manufacturing/tcad.html) |
| **Sentaurus Datasheet** | Tool capabilities summary PDF | [sentaurus_ds.pdf](https://www.synopsys.com/content/dam/synopsys/silicon/datasheets/sentaurus_ds.pdf) |

### Sentaurus Tool Suite Breakdown

#### 1. Sentaurus Workbench (SWB)
The **primary GUI front end** that integrates all Sentaurus tools. Manages project flow, preprocesses input files, parameterizes and executes simulations, and visualizes results.

- Set the `STDB` environment variable before launching
- Projects are organized in the Projects Pane
- The **Applications Library** contains bundled example projects (install with Sentaurus binaries)
- Supports TCL and Python scripting via Sentaurus Visual

**Recommended start:** Read Module 1 through Section 6 (Managing Projects) to understand the SWB workflow.

*Reference: [Stanford EE212 SWB Tutorial](https://web.stanford.edu/class/ee212/SWB/swb_a.html)*  
*Reference: [CERN TCAD Guide](https://bilpa.docs.cern.ch/simulation/tcad/guide/)*

#### 2. Sentaurus Process
Advanced **1D/2D/3D process simulator** for semiconductor fabrication modeling.

- Implantation, diffusion, dopant activation
- Thermal oxidation, mechanical stress, epitaxial growth
- Default parameters calibrated with equipment vendor data
- Covers nanoscale CMOS through high-voltage power devices

*Docs: [Sentaurus Process](https://www.synopsys.com/manufacturing/tcad/process-simulation/sentaurus-process.html)*

#### 3. Sentaurus Device
Multidimensional **device simulator** for electrical, thermal, and optical characteristics.

- Simulates silicon-based and compound semiconductor devices
- Explore new device concepts before fabrication
- Fast prototyping and optimization flows
- Full 3D mesh support with advanced solver technology

*Docs: [Sentaurus Device](https://www.synopsys.com/manufacturing/tcad/device-simulation/sentaurus-device.html)*

#### 4. Sentaurus Structure Editor
**Device structure editor** for when process simulation isn't required. Uses geometric primitives (ACIS® kernel) for complex 3D device shapes. Interfaces directly with mesh generation engines.

#### 5. Sentaurus Topography
Models topographical process steps: etching, deposition, CMP, electroplating.

#### 6. Sentaurus Visual
Advanced **visualization tool** for TCAD data. Supports XY plots and interactive 2D/3D structure manipulation. Scriptable via TCL and Python.

#### 7. Additional Tools
- **Sentaurus Process Explorer** — Fast 3D process emulator using GDSII mask data
- **Sentaurus Calibration Workbench** — ML-powered automated model calibration
- **Sentaurus Materials Workbench** — Links QuantumATK output to TCAD models
- **QuantumATK** — Atomistic simulation of novel materials and transport
- **Mystic** — Extracts SPICE / Verilog-A compact models from TCAD output

### Recommended Learning Path
1. **Module 1** — Sentaurus Workbench orientation (up to Section 6)
2. **Module 2** — Sentaurus Process: 1D CMOS flow
3. **Module 3** — Sentaurus Structure Editor: building custom geometries & meshes
4. **Module 4** — Sentaurus Device: I-V simulation, C-V, breakdown
5. **Module 5** — Parametric sweeps and design-of-experiment flows
6. **Advanced** — Radiation effects, ferroelectric materials, 3D flows

*Reference: [Synopsys TCAD Training Slides (CMOS Application)](https://picture.iczhiku.com/resource/eetop/syKGWdWqTusgjnmN.pdf)*

---

## Open-Source TCAD Simulators

For learning without a commercial license, these open-source alternatives cover core TCAD concepts.

### DEVSIM
- **What:** Open-source TCAD device simulator using finite volume methods
- **Language:** C++ backend, Python frontend
- **Capabilities:** 1D/2D/3D, drift-diffusion, user-specified PDEs, ferroelectric capacitor modeling, FeFET simulation
- **License:** Apache 2.0
- **Key feature for this project:** Demonstrated ferroelectric capacitor and FeFET polarization modeling using element edge based (EEB) discretization
- **Install:** `pip install devsim`
- **Links:**
  - [GitHub: devsim/devsim](https://github.com/devsim/devsim)
  - [Documentation: devsim.org](https://devsim.org)
  - [BJT Example](https://github.com/devsim/devsim_bjt_example)
  - [Density Gradient / MOSCAP Example](https://github.com/devsim/devsim_density_gradient)
  - [3D MOSFET Example](https://github.com/devsim/devsim_3dmos)

### Genius (Cogenda)
- **What:** Open-source 2D semiconductor device simulator
- **Capabilities:** Drift-diffusion, energy-balance, impact ionization, band-to-band tunneling, carrier trapping, raytracing optics, mixed device/circuit simulation
- **Links:**
  - [GitHub: cogenda/Genius-TCAD-Open](https://github.com/cogenda/Genius-TCAD-Open)
  - Supports TIF, CGNS, VTK file formats

### Charon (Sandia National Laboratories)
- **What:** Open-source TCAD code for large-scale simulation problems
- **Link:** [charon.sandia.gov](https://charon.sandia.gov)

### WebTCAD (Cogenda)
- **What:** Web-based TCAD for teaching purposes — intuitive GUI, step-by-step workflow
- **Link:** [cogenda.com](https://www.cogenda.com/)

### Other Tools & Utilities
| Tool | Description | Link |
|------|-------------|------|
| **Gmsh** | Open-source 3D mesh generator with CAD engine | [gmsh.info](https://gmsh.info) |
| **TetGen** | Delaunay-based tetrahedral mesh generator | [wias-berlin.de](https://www.wias-berlin.de/software/tetgen/) |
| **openbandparams** | Open-source semiconductor band parameters | [GitHub](https://github.com/scott-maddox/openbandparams) |
| **TCAD Central** | Community resource hub for TCAD software & tools | [tcadcentral.com](https://tcadcentral.com/Software.html) |
| **nanoHUB** | Browser-based simulation tools (Padre, Prophet) | [nanohub.org](https://nanohub.org) |
| **Silvaco Victory** | Commercial (with free academic tiers) — strong radiation effects module | [silvaco.com/tcad](https://silvaco.com/tcad/) |

---

## Radiation Hardening with TCAD

### The Problem
High-energy particles in space and radiation environments generate excess electron-hole pairs in semiconductor devices, disrupting normal operation. Two primary failure mechanisms:

- **Single Event Effects (SEE)** — A single particle strike causes a transient or upset (e.g., bit flip in SRAM). Modeled by simulating charge collection from a Gaussian ion track.
- **Total Ionizing Dose (TID)** — Cumulative radiation exposure degrades oxide interfaces and shifts threshold voltages over time.

### How TCAD Addresses This
1. **3D Structure Generation** — Sentaurus Process generates realistic transistor geometries from process flows
2. **Particle Strike Simulation** — Ion tracks modeled as Gaussian charge deposition along a particle trajectory; LET (Linear Energy Transfer) is the key parameter
3. **Transient Device Simulation** — Sentaurus Device solves time-dependent equations to predict collected charge, transient currents, and potential bit flips
4. **Layout Optimization** — Engineers can test layout-based radiation hardening techniques (guard rings, split active area, well tapping) in simulation before fabrication

### Key Applications
- **SRAM bit-cell hardening** — Simulate SEU and SEMNU (Single Event Multiple Node Upset) in nanoscale CMOS
- **FDSOI and FinFET rad-hard** — Evaluate novel device architectures for radiation resilience
- **Detector design** — Silicon strip detectors for high-energy physics (LHC upgrades)
- **Space electronics** — Validate designs before expensive beam testing

### Key References
- Synopsys: [TCAD-Based Radiation Modeling for Aerospace Chips](https://semiengineering.com/tcad-based-radiation-modeling-technique-for-reliable-aerospace-chips/)
- Aishwarya & Lakshmi (2024): [Heavy Ion Radiation Effects on HJLTFET — Sci. Reports](https://www.nature.com/articles/s41598-024-58371-6)
- Layout-based rad-hard (SAA/GWS): [Microelectronics Reliability, 2022](https://www.sciencedirect.com/science/article/abs/pii/S0026271422000968)
- FDSOI TFET SET simulation: [Taylor & Francis, 2023](https://www.tandfonline.com/doi/full/10.1080/10420150.2023.2191851)
- RHD14 bit-cell (20nm FinFET): [Microelectronics Reliability, 2023](https://www.sciencedirect.com/science/article/abs/pii/S0026271423000252)

---

## Ferroelectric & Oxide Semiconductor Simulation

### Why Ferroelectrics Are Hard to Simulate
Ferroelectric materials (e.g., HfO₂, HZO, PZT) introduce physics that standard TCAD material databases do not handle out of the box:

- **Polarization hysteresis** — P-E curves require specialized switching models (Landau-Khalatnikov, Preisach)
- **Custom material parameters** — Ferroelectric `.par` files must be manually defined (bandgap, permittivity, polarization saturation, coercive field, defect traps)
- **Interface effects** — Electrode depletion, depolarization fields, and interface trap screening dominate device behavior
- **Multi-grain modeling** — Polycrystalline ferroelectric films require statistical grain-size distributions

### Memcapacitor Simulation Challenges
Ferroelectric memcapacitors (nvCap) exhibit state-dependent capacitance driven by remnant polarization. Accurately simulating these requires:

1. **Fine meshing at interfaces** — Electric field discontinuities at ferroelectric/electrode and ferroelectric/dielectric boundaries require high mesh density; coarse meshes introduce significant numerical error
2. **Coupled polarization-transport equations** — The switching current is coupled to carrier transport; element edge based (EEB) discretization methods are needed for vector-field effects
3. **Defect-aware modeling** — Bulk traps in HZO and interface traps at SiO₂ boundaries affect leakage, screening, and memory window
4. **Calibration against experimental data** — TCAD simulations must match measured P-E loops, C-V curves, and switching transients before compact models can be extracted

### Adding Ferroelectric Materials to Sentaurus
- Sentaurus includes a `GettingStarted/Ferroelectric/Hysteresis` example (HfO₂ baseline)
- Custom materials require editing `.par` parameter files (see Germanium.par as template)
- Key parameters to define: `Permittivity`, `Bandgap`, `ElectronAffinity`, `PolarizationSaturation`, `CoerciveField`, defect trap levels and cross-sections
- ResearchGate community thread on adding custom ferroelectrics: [ResearchGate Discussion](https://www.researchgate.net/post/How-to-add-new-Ferroelectric-material-to-Synopsys-sentaurus-TCAD)

### Simulation Resources
- **Global TCAD Solutions** — Ferroelectrics Tutorial (capacitor hysteresis + FeFET gate stack): [globaltcad.com](https://www.globaltcad.com/download/ferroelectrics-tutorial/)
- **DEVSIM** — Demonstrated 3D ferro-capacitor and 2D FeFET polarization via EEB method
- **Hafnia Compact Model** (arxiv 2511.21267) — Physics-based nvCap model from TCAD calibration to circuit co-design: [arxiv.org](https://arxiv.org/html/2511.21267)
- **Computational Study of Hafnia Memories** — Landau-Khalatnikov modeling, multi-grain simulation: [arxiv 1709.06983](https://arxiv.org/pdf/1709.06983)

---

## Meshing & Material Parameters

### Meshing Best Practices for TCAD
Mesh quality directly determines simulation accuracy and runtime. Key principles:

| Region | Mesh Strategy | Why |
|--------|---------------|-----|
| **Bulk semiconductor** | Coarse uniform | Fields are smooth; low gradients |
| **Junctions (p-n, p-i-n)** | High density at interface | Carrier concentration changes rapidly |
| **Gate oxide / ferroelectric interfaces** | Very fine (< 1 nm spacing) | Electric field discontinuity; polarization gradients |
| **Channel region** | Adaptive refinement | Inversion layer is nanometer-scale |
| **Radiation strike path** | Refined along ion trajectory | Charge deposition follows Gaussian profile |

### Common Meshing Tools
- **Sentaurus Process** — Auto-generates mesh from process simulation output
- **Sentaurus Structure Editor** — Manual geometry + mesh control
- **Gmsh** — Open-source, import into DEVSIM or other simulators
- **TetGen** — Delaunay tetrahedral mesh generation

### Material Parameter Tips
- Always start from an existing `.par` file as a template
- Validate parameters against published experimental data (band alignment, permittivity, defect densities)
- For novel materials, iteratively calibrate TCAD against measured device characteristics
- Pay special attention to **interface parameters** — they often dominate behavior more than bulk properties

---

## Key References & Papers

### Textbooks & Books
- Wu, Y.C., Jhan, Y.R. (2018). *Introduction of Synopsys Sentaurus TCAD Simulation*. In: 3D TCAD Simulation for CMOS Nanoelectronic Devices. Springer. [Springer Link](https://link.springer.com/chapter/10.1007/978-981-10-3066-6_1)
- Srivastava, A.K. *Si Detectors and Characterization for HEP and Photon Science Experiment: How to Design Detectors using TCAD Device Simulation*. Springer, ISBN: 978-3-030-19530-4

### Key Papers
- Sanchez, J.E. (2022). "DEVSIM: A TCAD Semiconductor Device Simulator." *JOSS*, 7(70), 3898.
- Sanchez, J.E. & Chen, Q. (2021). "Element Edge Based Discretization for TCAD Device Simulation." *IEEE Trans. Electron Devices*.
- Chen, Q. et al. (2021). "The Impact of Contact Position on the Retention Performance in Thin-Film Ferroelectric Transistors." *Phys. Status Solidi (a)*.

---

## Getting Started Checklist

- [ ] **Access Sentaurus** — Contact your university's Synopsys license administrator (or check if your HPC cluster has TCAD installed)
- [ ] **Set up environment** — Configure `STDB` variable, locate Applications Library
- [ ] **Run Module 1** — Familiarize yourself with Sentaurus Workbench
- [ ] **Try a simple device** — Use Structure Editor to build a MOSFET, run I-V simulation
- [ ] **Install DEVSIM** — `pip install devsim` for open-source practice and learning
- [ ] **Explore ferroelectric examples** — Run the Sentaurus Hysteresis example; try modifying material parameters
- [ ] **Study radiation effects** — Review the SEE simulation methodology in the references above

---
*Contact: [linkedin.com/in/raymond-zhao]*
