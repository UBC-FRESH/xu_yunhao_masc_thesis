This document shows a few examples of creating mermaid diagrams.

The example markdown code blocks below should render from VSCode (or codeserver) development environment if the VSCode preview mermaid extension is installed correctly.

You can also save mermaid code into stand-alone `*.mmd` source code (plain text) files, and render these to LaTeX-compatible formats (e.g., PDF) using the `mmdc` command (provided by the `mermaid-cli` package).

```bash
npm install -g @mermaid-js/mermaid-cli
```

# Example 1: flowcharts

```mermaid
flowchart LR
  subgraph "Trivial Flowchart Example"
    direction TB
    A --> B
  end
```

```mermaid
flowchart LR
  A["Inventory & Roads"] --> S["State Assembler S_t"]
  B["Fire Perimeters & Severity"] --> S
  C["Salvageability & Grade Transitions"] --> S
  D["Prices/Costs & Stumpage"] --> S

  subgraph RH["Rolling Horizon (per t)"]
    direction TB
    S --> P1["ws3 Pre-fire Plan"]
    P1 --> F["Fire Realization in t..t+Delta"]
    F --> P2["Optional ws3 Post-fire (Problem)"]
    F --> K["Contract Design (Stage 1)"]
    P2 --> K
    K --> R["Agent Executes (Rule-based Stage 2)"]
    R --> P3["Optional ws3 Post-salvage (Mitigation)"]
    P3 --> Snext["Roll Horizon to S_{t+1}"]
  end
```

# Example 2: Gantt chart

```mermaid
gantt
  title 16-week Chapter 3 Launch Plan
  dateFormat  YYYY-MM-DD
  excludes    weekends
  section Setup & Data
  Repo & env              :a1, 2025-09-01, 7d
  Data intake             :a2, after a1, 7d
  Fire realization        :a3, after a2, 7d
  Salvage/grade curves    :a4, after a3, 7d
  KPI backbone            :a5, after a4, 7d
  section Planning & Contracts
  ws3 pre/post + memo     :b1, after a5, 7d
  Contract schema         :b2, after b1, 7d
  Agent rules             :b3, after b2, 7d
  Policy levers           :b4, after b3, 7d
  section Integration
  MVP end-to-end (Week 10):c1, after b4, 7d
  Back-cast validation    :c2, after c1, 7d
  Sensitivity screening   :c3, after c2, 7d
  section Write-up & Repro
  Results pass #1         :d1, after c3, 7d
  Reproducibility         :d2, after d1, 7d
  Ch.4 bridge             :d3, after d2, 7d
  Polish & sign-off       :d4, after d3, 7d
  ```
