Run quality checks on a knowledge base folder (default: knowledge-base/ or ask which folder).

## Quality Checks

### 1. YAML Front-Matter
- [ ] All content files have YAML front-matter
- [ ] Required fields present: category, difficulty, related_files, last_updated

### 2. Quick Reference Tables
- [ ] Files > 100 lines have Quick Reference table in first 30 lines
- [ ] Tables are scannable (not prose-heavy)

### 3. DRY Compliance
- [ ] No content duplicated across 3+ files
- [ ] Foundation files contain summaries + links, not full content
- [ ] Cross-references use links, not inline duplication

### 4. Cross-Links
- [ ] All new files have bidirectional cross-links
- [ ] Related files reference each other

### 5. Foundation File Updates
- [ ] GLOSSARY.md has entries for key terms
- [ ] NAVIGATION.md has routing for topics
- [ ] FAQ.md has common questions
- [ ] KB-INDEX.md manifest is current

### 6. File Organization
- [ ] Files in correct folders (templates/, protocols/, etc.)
- [ ] Naming follows kebab-case convention
- [ ] No orphan files (not linked from anywhere)

---

## Process

1. **Scan folder** - Find all .md files
2. **Run checks** - Evaluate each criterion
3. **Report findings** - List issues by category
4. **Suggest fixes** - Prioritize by impact

---

## Output Format

```
Quality Check: knowledge-base/
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ YAML Front-Matter: X/Y files pass
⚠️ Quick Reference: X files missing tables
❌ DRY Compliance: X violations found
✅ Cross-Links: All bidirectional
⚠️ Foundation Files: GLOSSARY needs X entries

Priority Fixes:
1. [High] Add Quick Reference to file.md
2. [Medium] Update GLOSSARY with term X
3. [Low] Add cross-link from A to B
```

---

**LOGGING (Required):**
Append a row to "Command Run Log" in `.claude/usage-log.md`:
`| /kb:check-quality | [date] | [outcome] | [folder, issues found] |`
