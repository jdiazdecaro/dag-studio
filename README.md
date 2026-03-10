# DAG Studio

**A browser-based directed acyclic graph (DAG) editor with causal inference engine, data simulation, and training library for pharmacoepidemiology and real-world evidence research.**

👉 **[Launch DAG Studio](https://jdiazdecaro.github.io/dag-studio/)**

> ⚠️ **Prototype** — actively under development. Feedback welcome.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Black Swan Causal Labs](https://img.shields.io/badge/Black%20Swan-Causal%20Labs-1e2a40)](https://blackswancausallabs.com)

---

## Overview

DAG Studio is a purpose-built tool for epidemiologists, pharmacoepidemiologists, and real-world evidence (RWE) researchers who work with causal diagrams. It combines an interactive graph editor with a working causal inference engine, data simulation, and a curated pedagogical library.

Existing tools like [DAGitty](https://dagitty.net) were built for researchers who already understand d-separation. DAG Studio bridges the gap between learning and doing, particularly for multidisciplinary RWE teams where causal literacy varies across statisticians, clinicians, and regulatory scientists.

---

## Features

### Interactive Canvas
- Drag-and-drop node placement with pan and zoom
- Four node types: **Exposure**, **Outcome**, **Confounder**, **Unclassified**
- Directed edge drawing with visual path highlighting
- Mobile-responsive design with touch support

### Causal Inference Engine
- **Backdoor path detection** — finds all open paths using Pearl's d-separation rules
- **Adjustment set computation** — enumerates minimal sufficient adjustment sets via backdoor criterion
- **Collider handling** — correctly treats unconditioned colliders as path-blockers
- **Visual feedback** — causal paths (green), backdoor paths (red dashed), blocked paths (gray)

### Data Simulation
- Generate synthetic datasets consistent with your DAG structure
- Configurable sample size and random seed
- Export simulated data as CSV
- Preview with summary statistics

### AI-Powered Analysis
- Plain-language summary of causal assumptions
- Adjustment guidance and identification status
- Powered by Anthropic Claude API

### Training Library
Eight canonical DAG archetypes with descriptions and primary references:

| Archetype | Key Concept |
|-----------|-------------|
| Classic Confounding | Backdoor paths via common causes |
| M-Bias | Colliders as pre-exposure covariates |
| Collider Bias | Berkson's bias, index event bias |
| Selection Bias | Conditioning on selection nodes |
| Mediation | Direct vs. total effects |
| Instrumental Variable | Mendelian randomization |
| Time-Varying Confounding | G-methods, treatment-confounder feedback |
| Over-adjustment | Table 2 fallacy, mediator adjustment |

### Export
Export your DAG as **PNG**, **JPG**, **PDF**, or **PowerPoint** with optional legend and black & white mode.

---

## Getting Started

### Use Online (Recommended)
Just open **[jdiazdecaro.github.io/dag-studio](https://jdiazdecaro.github.io/dag-studio/)** in any modern browser. Works on desktop, tablet, and mobile.

### Run Locally
```bash
git clone https://github.com/jdiazdecaro/dag-studio.git
cd dag-studio
```

Option A — Open `index.html` directly in your browser.

Option B — Use the dev server:
```bash
npm install
npm run dev
```
Then open [http://localhost:5173](http://localhost:5173).

---

## Validation

The d-separation engine is validated against 15 canonical test cases from Textor et al. (2016), covering:

- Simple confounding and adjustment
- M-bias (collider in empty conditioning set)
- Collider opening upon conditioning
- Competing adjustment sets
- Time-varying confounding with treatment-confounder feedback
- Instrumental variables
- Mediator identification

All 15 tests pass. See the [Validation tab](https://jdiazdecaro.github.io/dag-studio/) within the app for details.

---

## Scientific Basis

The engine implements d-separation as defined in:

- Pearl, J. (2009). *Causality: Models, Reasoning and Inference* (2nd ed.). Cambridge University Press.
- Greenland, S., Pearl, J., & Robins, J. M. (1999). Causal diagrams for epidemiologic research. *Epidemiology*, 10(1), 37–48.

Validation cases reference:

- Textor, J., et al. (2016). Robust causal inference using directed acyclic graphs: the R package 'dagitty'. *International Journal of Epidemiology*, 45(6), 1887–1894.

---

## Roadmap

- [ ] DAG export to dagitty-compatible format
- [ ] Testable implications and overidentification constraints
- [ ] Front-door criterion support
- [ ] SWIG (Single World Intervention Graph) mode
- [ ] Collaborative editing

---

## Citation

If you use DAG Studio in your research or teaching, please cite:

> Diaz-Decaro, J. D. (2026). *DAG Studio: A browser-based causal diagram editor for pharmacoepidemiology and real-world evidence research* [Software]. Black Swan Causal Labs, LLC. https://github.com/jdiazdecaro/dag-studio

---

## Author

**John D. Diaz-Decaro, PhD, MS**  
Founder, [Black Swan Causal Labs, LLC](https://blackswancausallabs.com)  
Chair, ISPE Digital Technology & AI Special Interest Group  
[LinkedIn](https://www.linkedin.com/in/jdiazdecaro/)

---

## License

MIT © 2026 John D. Diaz-Decaro, Black Swan Causal Labs, LLC. See [LICENSE](LICENSE).
