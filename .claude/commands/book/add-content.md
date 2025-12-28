Process new book material into the knowledge base with AI optimization, quality gates, and DRY enforcement.

## Workflow

### Step 0: Gather Input

**Wait for user to provide content in session** (pasted text, file path, or description).

If no content attached, respond:
> "Ready to process book content. Please paste text, provide a file path, or describe the topic."

---

### Step 0.5: Extract Images from PDF (if applicable)

**When processing PDF files with images:**

1. **Ask about page offset for multi-part PDFs:**
   - If this is Part 2, 3, etc., ask: "What book page does this PDF start on?"
   - Calculate: `book_page = pdf_page + offset`
   - Example: Part 2 PDF page 5, offset 41 → book page 46

2. **List images in PDF:**
   ```bash
   pdfimages -list /path/to/file.pdf
   ```

3. **Extract images to knowledge-base/images/:**
   ```bash
   pdfimages -j /path/to/file.pdf knowledge-base/images/extract
   ```

4. **Clean up extracted files:**
   - Remove `.ppm` files (masks/duplicates): `rm knowledge-base/images/*.ppm`
   - Remove small files under 10KB (likely icons)
   - View images to identify content before renaming

5. **Rename with descriptive names:**
   - Use lowercase, hyphenated names describing the content
   - Examples: `biotensegrity-human-model.jpg`, `kinetic-chain-diagram.jpg`

6. **Document image in the target markdown file:**

   **In YAML frontmatter:**
   ```yaml
   images:
     - path: images/descriptive-name.jpg
       alt: "Brief description for accessibility"
       caption: "Detailed caption for the image"
       source_chapter: "Chapter X - Title"
       source_page: 42
   ```

   **In body text (at relevant section):**
   ```markdown
   ![Alt Text](../images/descriptive-name.jpg)
   *Caption describing what the image shows.*
   *(Source: Chapter X - Title, Page 42)*
   ```

7. **Image naming conventions:**
   | Content Type | Naming Pattern | Example |
   |--------------|----------------|---------|
   | Anatomy diagrams | `[structure]-[detail].jpg` | `myofascial-lines-four-anatomy-views.jpg` |
   | Comparison images | `[topic]-comparison.jpg` | `joint-centration-comparison.jpg` |
   | Process diagrams | `[process]-[type].jpg` | `muscle-contraction-cascade.jpg` |
   | Body region | `[region]-[view].jpg` | `shoulder-anatomy-diagram.jpg` |

8. **Expected image sizes:** Typical range 23KB - 250KB. Larger images (>200KB) are usually full-page diagrams.

**Note:** Requires `poppler` package. Install with `brew install poppler` if not available.

---

### Step 1: Quality Gate

**Run in parallel:**
- Search GLOSSARY.md for key terms
- Search NAVIGATION.md for topic routing
- Grep existing files for similar concepts

| Code | Meaning | Action |
|------|---------|--------|
| **ACCEPT** | Relevant and new | Proceed |
| **QUESTION** | Unclear | Ask user |
| **SIMILAR** | Content exists | Suggest merge |
| **EXTRACT** | Buried in larger file | Extract to standalone |
| **REJECT** | Not book-related | Explain and stop |

**Present assessment for user approval before proceeding.**

---

### Step 2: Analyze & Route

**Detect content type:**
- Asset type: template, protocol, checklist, case study, or conceptual
- Key elements: quotes, numeric data, process steps

**Asset Type Routing:**

| Asset Type | Indicators | Route To |
|------------|------------|----------|
| **Template** | Fill-in-the-blank, [PATIENT NAME] | `/templates/` |
| **Protocol** | Step-by-step procedure, treatment method | `/protocols/` |
| **Checklist** | Numbered steps, action list | `/checklists/` |
| **Case Study** | Patient story, before/after | `/case-studies/` |
| **Paradigm** | Worldview, belief system, foundational assumptions | `/paradigms/` |
| **Concept** | Mental model, thinking tool derived from paradigm | `/concepts/` |
| **Reference** | Diagram, citation, reading list | `/reference/` |

**Paradigm vs Concept Decision:**
- **Paradigm** = "How reality works" — foundational worldview that shapes all reasoning (e.g., "body is unified whole", "reductionism is flawed")
- **Concept** = "How to think about X" — specific mental model or framework derived from paradigm (e.g., "pain as signal", "body as system")
- Rule: If removing it would change the book's philosophical foundation → paradigm. If it's a tool for understanding specific phenomena → concept.

---

### Step 3: Create Content File

**YAML front-matter required**, then:

**A) Front-Load Critical Info (First 30 Lines)**
- Quick Reference table after title
- Key quotes/insights in table format

**B) Table-First Formatting**

| Content Type | Format |
|--------------|--------|
| Key insights | Table (Insight, Context, Application) |
| Numeric data | Quick Reference table |
| Process steps | Table (Step, Action, Notes) |
| Comparisons | Side-by-side table |

**C) Content Compression**: Target 50-70% of verbose length

---

### Step 4: Update Foundation Files

**Run in parallel - Phase 1:** Read all 4 foundation files
**Run in parallel - Phase 2:** Edit all applicable files

**DRY PATTERN (CRITICAL):**

| File | Content Level |
|------|---------------|
| **Source file** | Full content |
| **GLOSSARY.md** | Summary + link (1-2 sentences max) |
| **FAQ.md** | Summary + link |
| **NAVIGATION.md** | Routing entry only |

**DRY Rules:**
- NEVER duplicate full content across files
- Full quotes, lists, tables in ONE source file only
- If content appears in 3+ places, consolidate

---

### Step 5: Add Bidirectional Cross-Links

**Run in parallel:**
- Read all related files
- Edit to add "See Also" or "Related" sections

---

### Step 6: Quality Check

- [ ] YAML front-matter complete
- [ ] Quick Reference in first 30 lines
- [ ] Tables used where applicable
- [ ] DRY pattern enforced
- [ ] Foundation files updated
- [ ] Bidirectional cross-links added
- [ ] Images extracted and linked (if PDF had images)
- [ ] Image sources documented (chapter + page)

---

### Step 7: Update KB-INDEX.md

- Update "Last Regenerated" date
- Update domain file counts
- Add new file to manifest

---

## EXTRACT Workflow

When duplicate content should become standalone:

1. Create standalone file in appropriate folder
2. Replace original with condensed reference + link
3. Update foundation files
4. Add bidirectional cross-links

---

## Reference Files

- [README.md](knowledge-base/README.md)
- [NAVIGATION.md](knowledge-base/NAVIGATION.md)

---

**LOGGING:** Append to `.claude/usage-log.md`:
`| /book:add-content | [date] | [outcome] | [content type, file created/updated] |`

Outcomes: `SUCCESS`, `SIMILAR`, `EXTRACT`, `PARTIAL`, `FAILED`, `REJECTED`

---

### Step 8: Generate Commit Message

Run `/commit-message` to generate a commit message for all changes made during this workflow. Present the message for user approval but do not commit.
