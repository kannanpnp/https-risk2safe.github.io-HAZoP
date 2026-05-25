# Risk2Safe HAZoP — AI-Powered HAZOP Study System

A fully browser-based, AI-assisted **Hazard and Operability (HAZOP) Study** application built for process safety professionals. Deployable directly to GitHub Pages — no build step, no server, no dependencies to install.

---

## Features

| Feature | Details |
|---|---|
| **AI Analysis** | Claude (Anthropic) generates Causes, Consequences, Safeguards & Recommendations per deviation |
| **ADNOC 6×6 Risk Matrix** | Interactive matrix picker for Initial and Residual risk ranking (Severity 1–6 × Likelihood A–F) |
| **Full HAZOP Workflow** | Study Setup → Nodes → Worksheet → Risk Matrix → Action Register → Report |
| **Guide Word Engine** | NO/NONE, MORE, LESS, AS WELL AS, PART OF, REVERSE, OTHER THAN, EARLY, LATE |
| **14 Parameters** | Flow, Pressure, Temperature, Level, Composition, Phase, Reaction Rate, Agitation, Sequence, Signal, Utility, Time, Viscosity, Concentration |
| **Auto-Save** | All data persists in browser localStorage |
| **Print Report** | Full HAZOP worksheet report — print to PDF |
| **JSON Export** | Export complete study data as JSON |
| **Team Management** | Add/manage HAZOP team members with roles |

---

## Quick Start — GitHub Pages

### 1. Create a new GitHub repository
```bash
git init risk2safe-hazop
cd risk2safe-hazop
```

### 2. Add the application file
Copy `index.html` into the repository root.

### 3. Push to GitHub
```bash
git add index.html README.md
git commit -m "Initial release — Risk2Safe HAZoP"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/risk2safe-hazop.git
git push -u origin main
```

### 4. Enable GitHub Pages
- Go to repository **Settings → Pages**
- Set Source: **Deploy from a branch → main → / (root)**
- Your app will be live at: `https://YOUR_USERNAME.github.io/risk2safe-hazop`

---

## API Key Setup

This app calls the **Anthropic Claude API** directly from the browser.

1. Get your API key from [console.anthropic.com](https://console.anthropic.com)
2. Open the app → click **⚙ API** in the top-right header
3. Paste your API key (`sk-ant-api03-…`)
4. The key is stored only in your browser's localStorage — never sent anywhere except Anthropic's API

> **Note**: The API uses `anthropic-dangerous-allow-browser: true` header, which is the approved method for browser-based applications. See [Anthropic docs](https://docs.anthropic.com).

---

## HAZOP Methodology Reference

This application implements the **Guide Word HAZOP** method as described in:
- IChemE *HAZOP: Guide to Best Practice* (Crawley, Preston, Tyler)
- CCPS *Guidelines for Hazard Evaluation Procedures*
- IEC 61882: Hazard and Operability Studies — Application Guide

### Workflow

```
1. STUDY SETUP    → Define project, facility, scope, team
2. NODES          → Identify and describe process nodes
3. WORKSHEET      → For each node: apply Guide Word + Parameter = Deviation
                    → AI generates Causes / Consequences / Safeguards / Recommendations
4. RISK MATRIX    → Assign Initial Risk (before safeguards) and Residual Risk
                    → ADNOC 6×6 matrix: Severity (1–6) × Likelihood (A–F)
5. ACTIONS        → Track recommendations, assign owners, set due dates
6. REPORT         → Generate printable HAZOP report or export JSON
```

### Risk Matrix (ADNOC Corporate)

| Category | Level | Management Sign-Off |
|---|---|---|
| Category 1 | HIGH (Red) | Director / GC CEO — Immediate ALARP required |
| Category 2 | HIGH (Orange) | Unit Manager / SVP — ALARP required |
| Category 3 | MEDIUM | Dept Manager / VP — Monitor & control |
| Category 4 | LOW | Line Manager — Monitor current controls |

---

## Pitfalls Avoided (per IChemE Best Practice)

- ✅ Nodes sized by common function (not individual lines)
- ✅ Cause-by-cause methodology (precise, fully auditable)
- ✅ Risk ranking integrated into worksheet (not deferred)
- ✅ Action register with owners, priorities, and due dates
- ✅ Exception-only and action-only methods **not implemented** (not auditable)
- ✅ Team size guidance: 4–6 optimal (noted in app)
- ✅ Design intent captured per node
- ✅ Both initial and residual risk tracked

---

## Technology Stack

- **React 18** (UMD via CDN — no build step)
- **Babel Standalone** (JSX in browser)
- **Anthropic Claude API** (claude-sonnet-4-20250514)
- Pure HTML/CSS/JS — works offline for all features except AI generation

---

## License

MIT License. For professional HAZOP use — results should be reviewed by qualified process safety engineers. This tool is an aid, not a substitute for expert judgment.

---

*Developed for HSE and Process Safety professionals in oil & gas, petrochemical, and industrial operations.*
