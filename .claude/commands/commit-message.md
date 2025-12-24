Generate commit message optimized for AI reference and future analysis.

## Format

```
[type]: [brief description]

[optional body with key changes]

Generated with Claude Code
```

## Types

| Type | Use When |
|------|----------|
| `Add` | New file or feature |
| `Update` | Enhancement to existing |
| `Fix` | Bug fix |
| `Refactor` | Code restructuring |
| `Docs` | Documentation only |
| `Merge` | Content merged into existing file |
| `Extract` | Content extracted to standalone file |

## Examples

```
Add book: new protocol for stress assessment

Add kb: GLOSSARY entries for holistic terms

Update book: expanded case study with outcomes

Merge book: consolidated nutrition protocols into single file

Extract kb: moved checklist from protocols to checklists/
```

## Process

1. **Check git status** - See what's staged/modified
2. **Analyze changes** - Understand the nature of modifications
3. **Generate message** - Following format above
4. **Present for approval** - Do not commit automatically

---

**Note**: Present the commit message but do not run `git commit` unless explicitly requested.
