# Default Chinese Looking Template

Use this frontmatter for consistent Chinese slides.

```yaml
---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    font-family: 'Noto Sans CJK SC', 'Microsoft YaHei', sans-serif;
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

# {标题}
## {副标题}

**日期:** {YYYY-MM-DD}
```
