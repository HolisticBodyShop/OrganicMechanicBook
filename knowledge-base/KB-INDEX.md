# Knowledge Base Index

> **Purpose**: Universal routing layer for AI assistants (Claude Code, MCP servers, Claude Projects)
> **Last Regenerated**: 2025-12-23
> **Total Files**: 19 | **Total Size**: ~120 KB | **Total Lines**: ~3,500

---

## Quick Router

| Query Type | Start Here | Then Check |
|------------|------------|------------|
| Book Philosophy | [paradigm/](paradigm/) | [FAQ.md](FAQ.md) |
| Core Concepts | [concepts/](concepts/) | [GLOSSARY.md](GLOSSARY.md) |
| Body Structures | [structures/](structures/) | [GLOSSARY.md](GLOSSARY.md) |
| Terms/Definitions | [GLOSSARY.md](GLOSSARY.md) | Topic folders |
| Common Questions | [FAQ.md](FAQ.md) | Linked detail files |
| Case Studies | [case-studies/](case-studies/) | [concepts/](concepts/) |
| Decision Trees | [reference/](reference/) | [concepts/](concepts/) |

---

## Domain Summary

| Domain | Path | Files | Primary Focus |
|--------|------|-------|---------------|
| **Foundation** | `knowledge-base/` | 5 | Index, navigation, glossary, FAQ, README |
| **Paradigm** | `paradigm/` | 2 | Book philosophy, medical critique |
| **Concepts** | `concepts/` | 2 | Body as system, pain understanding |
| **Structures** | `structures/` | 5 | Tensegrity, fascia, kinetic chain, joints |
| **Case Studies** | `case-studies/` | 5 | Clinical examples from Ch 3 |
| **Reference** | `reference/` | 1 | Pain decision tree |
| **Protocols** | `protocols/` | 0 | Step-by-step methods (future) |
| **Templates** | `templates/` | 0 | Fill-in-the-blank guides (future) |
| **Checklists** | `checklists/` | 0 | Action lists (future) |
| **Data** | `data/` | 0 | Logs, tracking |

---

## Entry Points by Intent

| Intent | Route |
|--------|-------|
| "What is this book about?" | → [you-are-light.md](paradigm/you-are-light.md) |
| "Why doesn't medicine help my pain?" | → [reductionism-limits.md](paradigm/reductionism-limits.md) |
| "How does pain work?" | → [pain-as-signal.md](concepts/pain-as-signal.md) |
| "What does X term mean?" | → [GLOSSARY.md](GLOSSARY.md) |
| "Show me a clinical example" | → [case-studies/](case-studies/) |
| "How do I assess pain?" | → [pain-decision-tree.md](reference/pain-decision-tree.md) |
| "What is fascia/tensegrity/etc?" | → [structures/](structures/) |

---

## Foundation Files

| File | Purpose |
|------|---------|
| [README.md](README.md) | Entry point, AI processing rules |
| [KB-INDEX.md](KB-INDEX.md) | This file - universal router |
| [GLOSSARY.md](GLOSSARY.md) | Term definitions, cross-references |
| [NAVIGATION.md](NAVIGATION.md) | Decision trees, routing |
| [FAQ.md](FAQ.md) | Common questions, quick answers |

---

## Full File Manifest

### paradigm/

| File | Source | Focus |
|------|--------|-------|
| [you-are-light.md](paradigm/you-are-light.md) | Preface | Core philosophy, energy-matter |
| [reductionism-limits.md](paradigm/reductionism-limits.md) | Ch 1 | Medical system critique |

### concepts/

| File | Source | Focus |
|------|--------|-------|
| [body-as-system.md](concepts/body-as-system.md) | Ch 1 | Complex adaptive systems |
| [pain-as-signal.md](concepts/pain-as-signal.md) | Ch 4 | Pain as information |

### structures/

| File | Source | Focus |
|------|--------|-------|
| [tensegrity.md](structures/tensegrity.md) | Ch 2 | Tension-based stability |
| [bones-dont-move.md](structures/bones-dont-move.md) | Ch 2 | Force governs alignment |
| [fascial-bunching.md](structures/fascial-bunching.md) | Ch 3 | Fascia as load-sharing network |
| [kinetic-chain.md](structures/kinetic-chain.md) | Ch 3 | Connected movement chains |
| [joint-centration.md](structures/joint-centration.md) | Ch 3 | Optimal joint positioning |

### case-studies/

| File | Condition | Key Lesson |
|------|-----------|------------|
| [case-perfect-mri-knee.md](case-studies/case-perfect-mri-knee.md) | Knee pain | Pain ≠ damage location |
| [case-frozen-shoulder.md](case-studies/case-frozen-shoulder.md) | Shoulder ROM | Local stiffness = remote binding |
| [case-chronic-neck-pain.md](case-studies/case-chronic-neck-pain.md) | Neck pain | NS sacrifices comfort for movement |
| [case-bone-on-bone-hip.md](case-studies/case-bone-on-bone-hip.md) | Hip degeneration | Degeneration where rotation trapped |
| [case-strong-broken-athlete.md](case-studies/case-strong-broken-athlete.md) | Athletic pain | Control beats capacity |

### reference/

| File | Purpose |
|------|---------|
| [pain-decision-tree.md](reference/pain-decision-tree.md) | Systematic pain assessment |

---

## Chapter Coverage

| Chapter | Status | Primary Files |
|---------|--------|---------------|
| Preface - You Are Light | Complete | paradigm/you-are-light.md |
| Ch 1 - Why the System Can't See You | Complete | paradigm/reductionism-limits.md, concepts/body-as-system.md |
| Ch 2 - Bones Don't Move Themselves | Complete | structures/bones-dont-move.md, structures/tensegrity.md |
| Ch 3 - Fascial Bunching & Kinetic Chain | Complete | structures/fascial-bunching.md, structures/kinetic-chain.md, structures/joint-centration.md, case-studies/* |
| Ch 4 - Pain Is an Encrypted Message | Complete | concepts/pain-as-signal.md, reference/pain-decision-tree.md |
| Ch 5+ | Not yet added | — |

---

## Maintenance

This index is maintained by:
- `/kb:reindex` - Full regeneration of this file
- `/book:add-content` - Updates after adding book content
- `/kb:optimize-md` - Updates after optimizing files

**To regenerate**: Run `/kb:reindex` to scan all `knowledge-base/` directories and rebuild this manifest.
