# Product Requirements Document
## NeurIPS 2025 Best Papers Explorer & Simulator

---

## 1. Executive Summary

**Product Name:** NeurIPS 2025 Best Papers Explorer
**Version:** 1.0
**Date:** December 2025

Create an interactive educational platform that provides comprehensive deep-dives into each of the 7 NeurIPS 2025 Best Paper topics, with interactive simulators demonstrating core concepts.

---

## 2. Problem Statement

The existing `2025_winners.html` provides a summary dashboard of NeurIPS 2025 Best Papers but lacks:
- In-depth explanations of each research area
- Interactive demonstrations of core concepts
- Educational value for understanding the underlying principles
- Hands-on experimentation capabilities

---

## 3. Goals & Success Metrics

### Goals
1. **Educational Depth:** Comprehensive explanations of each paper's domain
2. **Interactivity:** Hands-on simulators for key concepts
3. **Accessibility:** Make complex ML concepts approachable
4. **Engagement:** Visual, interactive learning experience

### Success Metrics
- All 7 paper topics covered with detailed explanations
- At least 5 interactive simulators functional
- Single-page application with smooth navigation
- Mobile-responsive design

---

## 4. Scope & Features

### 4.1 Seven Deep-Dive Topics

| # | Paper | Topic Page | Simulator |
|---|-------|------------|-----------|
| 1 | Artificial Hivemind | LLM Diversity & Homogeneity | Text diversity analyzer |
| 2 | Gated Attention | Attention Mechanisms | Attention visualization |
| 3 | 1000 Layer Networks | Deep RL & Self-Supervision | Goal-reaching agent sim |
| 4 | Why Diffusion Models Don't Memorize | Diffusion Training Dynamics | Diffusion process visualizer |
| 5 | Does RL Incentivize Reasoning? | RLVR & LLM Reasoning | Sampling exploration demo |
| 6 | Optimal Mistake Bounds | Online Learning Theory | Mistake bound visualizer |
| 7 | Superposition & Scaling | Neural Scaling Laws | Superposition feature demo |

### 4.2 Feature Details

#### A. Topic Deep-Dive Pages
Each topic page includes:
- **Concept Overview:** Plain-language explanation
- **Technical Deep-Dive:** Mathematical foundations
- **Visual Diagrams:** Animated/interactive illustrations
- **Key Insights:** Paper contributions
- **Related Concepts:** Links to related topics
- **Further Reading:** Resources and references

#### B. Interactive Simulators

1. **LLM Diversity Analyzer**
   - Input: Multiple text samples
   - Output: Diversity metrics (lexical, semantic similarity)
   - Visualization: Clustering of responses

2. **Attention Mechanism Visualizer**
   - Interactive attention matrix
   - Compare standard vs gated attention
   - See attention sink phenomenon

3. **Goal-Reaching RL Agent**
   - 2D grid environment
   - Watch agent learn to reach goals
   - Adjust network depth, observe performance

4. **Diffusion Process Visualizer**
   - Forward diffusion (add noise)
   - Reverse diffusion (denoise)
   - Visualize generalization vs memorization window

5. **RLVR Exploration Demo**
   - Sampling tree visualization
   - Show how RL narrows exploration
   - Compare base model vs RLVR distributions

6. **Mistake Bound Tracker**
   - Online learning simulation
   - Track mistakes over sequence
   - Compare transductive vs standard bounds

7. **Feature Superposition Demo**
   - Low-dimensional embedding space
   - Visualize feature interference
   - Show scaling law emergence

---

## 5. Technical Architecture

### 5.1 Technology Stack
- **Frontend:** Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Visualization:** Canvas API, CSS animations
- **No build tools:** Single HTML file, self-contained
- **Styling:** CSS custom properties, consistent with existing design

### 5.2 File Structure
```
/Users/adrian/work/ips/
├── 2025_winners.html          # Original dashboard (unchanged)
├── neurips_explorer.html      # Main explorer application
├── PRD_NeurIPS_2025_Explorer.md  # This document
```

### 5.3 Application Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Navigation Header                         │
│  [Dashboard] [Topics ▼] [Simulators ▼] [About]              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌─────────────────────────────────────────────────────────┐│
│  │                    Content Area                          ││
│  │                                                          ││
│  │   - Topic deep-dive pages (7)                           ││
│  │   - Interactive simulators (7)                          ││
│  │   - Smooth SPA transitions                              ││
│  │                                                          ││
│  └─────────────────────────────────────────────────────────┘│
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                    Footer / References                       │
└─────────────────────────────────────────────────────────────┘
```

---

## 6. Implementation Chunks

### Chunk 1: Core Structure & Navigation (Foundation)
**Deliverables:**
- HTML skeleton with SPA routing
- Navigation system with topic/simulator menus
- CSS design system (extending existing dark theme)
- Page transition framework
- Responsive layout grid

**Estimated Components:** ~400 lines

### Chunk 2: Topic Deep-Dive Pages (Content)
**Deliverables:**
- 7 topic pages with full content
- Concept explanations
- Technical sections with diagrams
- CSS-based visual illustrations
- Cross-linking between related topics

**Estimated Components:** ~800 lines (content-heavy)

### Chunk 3: Interactive Simulators (Interactivity)
**Deliverables:**
- Canvas-based visualizations
- Interactive controls (sliders, buttons)
- Real-time animations
- Parameter adjustment panels
- Results/metrics displays

**Estimated Components:** ~1200 lines (JS-heavy)

### Chunk 4: Integration & Polish (Completion)
**Deliverables:**
- Link original dashboard
- Performance optimization
- Accessibility improvements
- Mobile responsiveness
- Final testing & bug fixes

**Estimated Components:** ~200 lines

---

## 7. Detailed Simulator Specifications

### 7.1 Diffusion Process Visualizer
```
┌──────────────────────────────────────────┐
│  [Original Image] ──────► [Noised]       │
│       ▼                        ▲         │
│  [Controls]                    │         │
│  ├─ Noise level: [====○===]   │         │
│  ├─ Step: [◄] [12/50] [►]     │         │
│  └─ Mode: ○ Forward ● Reverse │         │
│                                          │
│  ┌────────────────────────────────────┐  │
│  │   Training Timeline                │  │
│  │   [====|GENERALIZE|====|MEMORIZE|] │  │
│  │        ▲ You are here              │  │
│  └────────────────────────────────────┘  │
└──────────────────────────────────────────┘
```

### 7.2 Attention Mechanism Visualizer
```
┌──────────────────────────────────────────┐
│  Input Tokens: [The] [cat] [sat] [on]    │
│                                          │
│  ┌─ Attention Matrix ─────────────────┐  │
│  │     The  cat  sat  on              │  │
│  │ The [##] [  ] [  ] [  ]            │  │
│  │ cat [##] [##] [  ] [  ]            │  │
│  │ sat [##] [##] [##] [  ]  ← Sink!   │  │
│  │ on  [##] [##] [##] [##]            │  │
│  └────────────────────────────────────┘  │
│                                          │
│  Mode: ○ Standard  ● Gated Attention     │
│  Gate value: 0.73 [========○==]          │
└──────────────────────────────────────────┘
```

### 7.3 RL Goal-Reaching Agent
```
┌──────────────────────────────────────────┐
│  Environment              Stats          │
│  ┌────────────────┐      Episodes: 142   │
│  │ . . . . G . . │      Success: 78%    │
│  │ . ■ ■ . . . . │      Avg steps: 12   │
│  │ . . . A . ■ . │                       │
│  │ . ■ . . . . . │      Network Depth    │
│  └────────────────┘      [64] [256] [1024]│
│                                          │
│  [▶ Play] [⏸ Pause] [↻ Reset]            │
│  Speed: [====○===]                       │
└──────────────────────────────────────────┘
```

### 7.4 Feature Superposition Demo
```
┌──────────────────────────────────────────┐
│  Feature Space (2D projection)           │
│  ┌────────────────────────────────────┐  │
│  │        ★                           │  │
│  │     ●    ▲                         │  │
│  │   ■        ◆                       │  │
│  │      ●  ▲                          │  │
│  │           ■                        │  │
│  └────────────────────────────────────┘  │
│                                          │
│  Features: [3] [10] [50] [100]           │
│  Dimensions: [2] [4] [8]                 │
│                                          │
│  Interference: ████████░░ 82%            │
│  Loss scaling: L ∝ 1/d^0.73              │
└──────────────────────────────────────────┘
```

---

## 8. Content Outline per Topic

### Topic 1: LLM Diversity & The Artificial Hivemind
- What is output diversity?
- Measuring homogeneity: metrics & methods
- Intra-model vs inter-model diversity
- Societal implications of LLM monoculture
- The Infinity-Chat benchmark explained

### Topic 2: Attention Mechanisms & Gating
- Self-attention refresher (Q, K, V)
- The attention sink problem
- Softmax limitations in long contexts
- Gating mechanisms explained
- Head-specific sigmoid gating design

### Topic 3: Deep Networks in Reinforcement Learning
- Why depth was thought incompatible with RL
- Self-supervised RL fundamentals
- Contrastive goal-conditioned learning
- Emergent behaviors from depth scaling
- The 1024-layer architecture

### Topic 4: Diffusion Model Training Dynamics
- Diffusion models 101: forward & reverse
- Over-parameterization paradox
- Implicit regularization in training
- Two timescales: learning vs memorization
- The generalization window

### Topic 5: RL for LLM Reasoning (RLVR)
- What is RLVR?
- Verifiable rewards explained
- Sampling efficiency vs reasoning expansion
- Why RLVR doesn't add new reasoning
- Distillation as the alternative

### Topic 6: Online Learning Theory
- Online learning setup
- Mistake bounds fundamentals
- Transductive vs standard settings
- The value of unlabeled data
- The √d gap explained

### Topic 7: Neural Scaling Laws & Superposition
- Scaling laws refresher (Chinchilla)
- What is feature superposition?
- Interference and dimensionality
- Why superposition enables scaling
- When scaling laws break

---

## 9. Design Guidelines

### Visual Style (extending existing)
```css
/* Inherit from 2025_winners.html */
--bg: #050816;
--bg-elevated: #070c1f;
--card: #0b1229;
--accent: #4f46e5;
--accent-2: #06b6d4;
--text-main: #f9fafb;
--text-muted: #9ca3af;
```

### Typography
- Headers: system-ui, SF Pro Text
- Code: SF Mono, Consolas, monospace
- Body: 16px base, 1.6 line-height

### Interactive Elements
- Smooth transitions (200-300ms)
- Hover states with subtle glow
- Active states with accent color
- Disabled states at 50% opacity

---

## 10. Approval & Next Steps

### Approval Required
- [ ] PRD scope approved
- [ ] Begin Chunk 1 implementation

### Questions for Clarification
1. Should simulators work offline (no external APIs)?
2. Preferred level of mathematical detail in explanations?
3. Any specific paper aspects to emphasize?

---

**Document Status:** Ready for Review
**Next Action:** Await approval, then begin Chunk 1
