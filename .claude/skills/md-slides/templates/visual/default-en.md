# Default English Visual Template

Use this frontmatter for consistent English slides.

```yaml
---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    font-family: 'Noto Sans', 'Helvetica Neue', sans-serif;
  }
  section.small-table table { font-size: 0.85em; }
---
```

## Rules

- Use frontmatter exactly as shown above
- Use `<!-- _class: lead -->` only on title slide
- End slides with content (last slide should have text/table)

## Title Slide Pattern

```markdown
<!-- _class: lead -->

# {Title}
## {Subtitle}

**Date:** {YYYY-MM-DD}
```
