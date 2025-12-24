Regenerate `knowledge-base/KB-INDEX.md` by scanning all markdown files in the knowledge base.

**Process:**

1. **Scan all files** - Run: `find knowledge-base -name "*.md" -type f` with size and line counts
2. **Calculate totals** - Sum files, sizes, and lines per domain
3. **Regenerate KB-INDEX.md** with:
   - Updated "Last Regenerated" date (today)
   - Updated total file count and size in header
   - Updated "Domain Summary" table with current counts
   - Complete "Full File Manifest" with all files organized by directory
   - Preserve "Quick Router" and "Entry Points by Intent" sections (these are manually curated)

4. **Verify integrity**:
   - Check all linked files in Quick Router exist
   - Flag any broken references
   - Report files that exist but aren't in manifest (shouldn't happen after full regen)

5. **Show summary**: Files added, removed, or changed since last regeneration

**Output format:**
```
KB-INDEX.md regenerated
- Total files: X (±Y from previous)
- Total size: X KB
- Domains: [list with counts]
- Changes detected: [list of adds/removes/moves]
```

---

**LOGGING (Required):**
Append a row to "Command Run Log" in `.claude/usage-log.md`:
`| /kb:reindex | [date] | [outcome] | [file count, changes detected] |`
