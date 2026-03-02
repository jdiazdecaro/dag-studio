# DAG Studio

**A browser-based directed acyclic graph (DAG) editor with an integrated d-separation engine and training library for pharmacoepidemiology and real-world evidence research.**

> ⚠️ **Prototype** — actively under development. Feedback and contributions welcome.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Black Swan Causal Labs](https://img.shields.io/badge/Black%20Swan-Causal%20Labs-1e2a40)](https://blackswancausallabs.com)

---

## Overview

DAG Studio is a purpose-built tool for epidemiologists, pharmacoepidemiologists, and real-world evidence (RWE) researchers who work with causal diagrams. It combines an interactive graph editor with a working causal inference engine and a curated pedagogical library — making it useful for both designing study-specific DAGs and learning causal structure.

Existing tools like [DAGitty](https://dagitty.net) were built for researchers who already understand d-separation. DAG Studio is designed to bridge the gap between learning and doing, particularly for multidisciplinary RWE teams where causal literacy varies across statisticians, clinicians, and regulatory scientists.

---

## Features

### Interactive Canvas
- Drag-and-drop node placement
- Four node types: **Exposure**, **Outcome**, **Confounder**, **Latent** (unmeasured)
- Directed edge drawing with arrowheads
- Node selection and deletion
- Click-to-set exposure and outcome

### Causal Inference Engine
- **Backdoor path detection** — finds all open paths into the exposure node using Pearl's d-separation rules
- **Adjustment set computation** — enumerates all minimal sufficient adjustment sets via backdoor criterion
- **Collider handling** — correctly treats unconditioned colliders as path-blockers (validated against M-bias)
- **Visual feedback** — backdoor paths rendered in red dashed lines on the canvas

### AI-Powered Summary
- One-click plain-language summary of the current DAG's causal assumptions
- Powered by the Anthropic API

### Training Library
Eight canonical DAG archetypes with descriptions and curated primary references:

| Archetype | Key Concept |
|---|---|
| Classic Confounding | Backdoor paths via common causes |
| M-Bias | Colliders as pre-exposure covariates |
| Collider Bias | Berkson's bias, index event bias |
| Selection Bias | Conditioning on selection nodes |
| Mediation | Direct vs. total effects |
| Instrumental Variable | Mendelian randomization |
| Time-Varying Confounding | G-methods, treatment-confounder feedback |
| Over-adjustment | Table 2 fallacy, mediator adjustment |

### Export
Export the current DAG canvas as **PNG**, **JPG**, **PDF**, or **PowerPoint** for use in manuscripts, protocols, and presentations.

---

## Validation

The d-separation engine is validated against 15 canonical test cases drawn from the dagitty reference paper (Textor et al., 2016), covering:

- Simple confounding and adjustment
- M-bias (collider in empty conditioning set)
- Collider opening upon conditioning
- Competing adjustment sets
- Time-varying confounding with treatment-confounder feedback
- Instrumental variables
- Mediator identification

All 15 tests pass. See [`src/engine/index.js`](src/engine/index.js) for the engine implementation and the companion validation suite for test details.

---

## Getting Started

### Prerequisites
- Node.js ≥ 18
- npm ≥ 9

### Install and run locally

```bash
git clone https://github.com/jdiazdecaro/dag-studio.git
cd dag-studio
npm install
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for production

```bash
npm run build
```

Output goes to `dist/`. Deploy to GitHub Pages, Netlify, or any static host.

---

## Project Structure

```
dag-studio/
├── src/
│   ├── engine/
│   │   └── index.js        # d-separation engine (descendants, allPaths, backdoorPaths, computeAdjustmentSets)
│   ├── data/
│   │   └── library.js      # Training library — 8 canonical DAG archetypes with references
│   ├── constants.js         # Node colors, initial graph state, ID generators
│   ├── App.jsx              # Main application component
│   └── main.jsx             # React entry point
├── index.html
├── vite.config.js
├── package.json
└── LICENSE
```

---

## Scientific Basis

The engine implements d-separation as defined in:

- Pearl, J. (2009). *Causality: Models, Reasoning and Inference* (2nd ed.). Cambridge University Press.
- Greenland, S., Pearl, J., & Robins, J. M. (1999). Causal diagrams for epidemiologic research. *Epidemiology*, 10(1), 37–48. https://doi.org/10.1097/00001648-199901000-00008

The adjustment set algorithm applies the backdoor criterion:

- Pearl, J. (1993). Aspects of graphical models connected with causality. *Proceedings of the 49th Session of the International Statistical Institute*.

Validation cases reference:

- Textor, J., van der Zander, B., Gilthorpe, M. S., Liśkiewicz, M., & Ellison, G. T. H. (2016). Robust causal inference using directed acyclic graphs: the R package 'dagitty'. *International Journal of Epidemiology*, 45(6), 1887–1894. https://doi.org/10.1093/ije/dyw341

---

## Roadmap

- [ ] DAG export to dagitty-compatible format
- [ ] Testable implications and overidentification constraints
- [ ] Front-door criterion support
- [ ] SWIG (Single World Intervention Graph) mode
- [ ] Collaborative editing
- [ ] Formal test suite (Vitest)

---

## Citation

If you use DAG Studio in your research or teaching, please cite:

> Diaz-Decaro, J. D. (2026). *DAG Studio: A browser-based causal diagram editor for pharmacoepidemiology and real-world evidence research* [Software]. Black Swan Causal Labs, LLC. https://github.com/jdiazdecaro/dag-studio

A preprint describing the tool, its validation, and its pedagogical design rationale is forthcoming.

---

## Author

**John D. Diaz-Decaro, PhD, MS**  
Founder, [Black Swan Causal Labs, LLC](https://blackswancausallabs.com)  
Chair, ISPE Digital Technology & AI Special Interest Group

---

## License

MIT © 2026 John D. Diaz-Decaro, Black Swan Causal Labs, LLC. See [LICENSE](LICENSE).
