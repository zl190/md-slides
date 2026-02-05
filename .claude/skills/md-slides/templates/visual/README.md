# Visual Templates

Visual style templates for consistent slide rendering.

## What's a "Visual Template"?

A visual template defines the **visual appearance** of slides:
- Frontmatter (marp settings, theme, size)
- CSS (fonts, colors, table styles)
- Title slide pattern

It does NOT define content structure — that's a separate concern.

## Available Looks

| File | Language | Description |
|------|----------|-------------|
| `default-zh.md` | Chinese | Noto Sans CJK SC, minimal CSS |
| `default-en.md` | English | Noto Sans, minimal CSS |

## Using a Visual Template

When generating slides:
1. Read the appropriate visual template
2. Copy its frontmatter to your slides
3. Follow its gotchas/rules

## Adding Custom Looks

Create a new file in this folder:

```markdown
# My Custom Look

Description of when to use this look.

\`\`\`yaml
---
marp: true
theme: gaia
# ... your frontmatter
---
\`\`\`

## Gotchas

- List any pitfalls specific to this look
```

Name it descriptively: `corporate-zh.md`, `academic-en.md`, etc.

## Why Pluggable?

Different projects/organizations have different visual standards:
- Corporate branding
- Academic requirements
- Personal preference

The default looks work well for general use. Replace or extend as needed.
