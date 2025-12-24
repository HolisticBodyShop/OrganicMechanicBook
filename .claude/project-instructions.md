# Claude Agent Instructions

## Documentation Standards

| Principle | Rule | Target |
|-----------|------|--------|
| **Conciseness** | Dense info, minimal fluff | 50-70% of verbose length |
| **Structure** | Tables/bullets > prose | Use structured formats |
| **Priority** | Critical info first | Front-load key content |
| **Redundancy** | Link, don't repeat | Minimize duplication |
| **Scannability** | AI-optimized reference | Concise, structured |

### AI-Optimized Content Rules
1. **Optimize for AI reference** - Concise and scannable, not verbose
2. **Use structured formats** - Tables, bullets, headers > prose
3. **Front-load key information** - Most important content at top
4. **Target 50-70% of verbose length** - Dense information, minimal fluff
5. **Minimize redundancy** - Link to related content instead of repeating

### Knowledge Base Files
For files in `knowledge-base/`:

6. **YAML front-matter** - Required metadata:
   ```yaml
   ---
   category: [category]
   difficulty: [beginner/intermediate/advanced]
   related_files: [./related.md]
   last_updated: "YYYY-MM-DD"
   ---
   ```

7. **Update foundation files** - Always update GLOSSARY.md, NAVIGATION.md when adding content
8. **Create bidirectional links** - Link FROM new TO existing AND FROM existing TO new
9. **Include source references** - Citations, page numbers, attributions where applicable

### Exceptions
User-facing templates and client materials can be more detailed and explanatory.

---

## Command Optimization

**Proactive workflow detection:** Every ~10 conversations, ask: "Are there any repetitive workflows I should turn into slash commands? Should I check the usage-log for patterns?"

This helps identify:
- Manual workflows that could be automated
- Unused commands to archive
- Existing commands that need improvement

**User can track patterns in** `.claude/usage-log.md` and run `/kb:optimize-commands` to implement improvements.

### Command Performance Best Practices

| Best Practice | Implementation | Benefit |
|---------------|----------------|---------|
| **Identify parallel ops** | Find independent reads/searches/edits | Reduce sequential bottlenecks |
| **Batch by type** | Phase 1: all Reads → Phase 2: all Edits | Never alternate operation types |
| **Common patterns** | Duplicate checks, foundation updates, cross-refs | All benefit from parallelization |
| **Explicit markers** | "RUN IN PARALLEL" in descriptions | Ensure consistent execution |

### Quality Gate Best Practices

When building commands that process user input or add content:

1. **Always implement a quality gate as Step 0**
   - Assess relevance to the domain/context
   - Check for duplicates or overlapping content
   - Make a clear decision: ACCEPT, QUESTION, SIMILAR, or REJECT
   - Present assessment to user for approval before proceeding

2. **Quality gate decisions**
   - ✅ ACCEPT - Relevant and new
   - ❓ QUESTION - Unclear, needs clarification
   - 🔄 SIMILAR - Content exists, suggest merge/update
   - 📤 EXTRACT - Buried in larger file, extract to standalone
   - ❌ REJECT - Out of scope

### Command Logging Requirement

**All commands MUST log their execution** to enable data-driven optimization.

**Required ending for every command:**
```markdown
---

**LOGGING (Required):**
Append a row to "Command Run Log" in `.claude/usage-log.md`:
`| /command-name | [date] | [outcome] | [brief context] |`
```

**Outcome codes:**
- ✅ Success - completed as expected
- ⚠️ Partial - completed with issues
- ❌ Failed - could not complete
- 🔄 SIMILAR - merged into existing
- 📤 EXTRACT - extracted to standalone

---

## Markdown Optimization Patterns

### 1. Add Quick-Reference Tables at Top
Convert verbose lists into scannable tables immediately after intro.

### 2. Compress Multi-Line Answers
Remove verbose explanations, keep core insight + link.

### 3. Table-ize Lists
Convert bullet lists of items into compact tables.

### 4. Remove Redundant Labels
Strip "Definition:", "Primary Location:", etc.

### 5. Shorten Cross-References
Use "See X" instead of "For more details see X".

### 6. Use Arrows & Symbols
Replace verbose connectors with →, =, |, /.

### 7. Front-Load Critical Info
Move most important content to top of document.

### 8. Compress Usage Sections
Turn multi-paragraph instructions into 1-2 lines.

---

## Book-Specific Guidelines

### Content Organization
- **Concepts** → Core philosophy and principles
- **Protocols** → Step-by-step methods
- **Case Studies** → Real examples and stories
- **Templates** → Fill-in-the-blank worksheets
- **Checklists** → Action lists
- **Reference** → Diagrams, citations, reading lists

### Writing Support
When helping with book content:
1. Check KB for existing related content
2. Maintain consistent terminology (use GLOSSARY)
3. Cross-reference between chapters/concepts
4. Track sources for citations

---

**Created**: 2025-12-23
**Purpose**: Ensure consistent, AI-optimized documentation across repository
