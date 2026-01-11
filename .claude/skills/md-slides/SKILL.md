---
name: md-slides
description: Convert Markdown to presentation slides in multiple formats (PDF, PPTX, HTML). Use when user mentions slides, presentations, Marp, Beamer, or wants to generate PDF/PPTX from markdown. Supports flavors (audience, style, language), visual comparisons, and AI-generated images via mcp-image.
allowed-tools: Read, Write, Edit, Bash, Glob, Grep, mcp__mcp-image__generate_image
---

# Markdown Universal Slides Generator

Convert Markdown source files to presentation slides in multiple formats.

## Workflow

**From prompt (recommended workflow):**
```
Prompt → Claude writes slides.md → [Optional: Generate images] → User reviews/edits → Convert to PDF/PPTX
```

1. Generate markdown content based on user's prompt
2. **Write to a .md file first** (e.g., `slides.md` or `output/slides.md`)
3. **Optional**: If visuals needed and mcp-image is configured, generate diagrams/charts
4. Tell user: "I've created `slides.md`. Review and edit if needed."
5. **Ask before converting**: "Ready to convert to PDF/PPTX?"
6. Convert using the appropriate tool (use `--allow-local-files` if images included)

**From existing file:**
```
slides.md → Select tool → Convert to PDF/PPTX
```

## Core Concept

**One source, multiple outputs:**
```
slides.md → Marp/Pandoc/python-pptx → PDF / PPTX / HTML
```

## Slide Flavors

When creating slides, ask or infer these parameters to customize output:

### Audience Types

| Audience | Characteristics |
|----------|-----------------|
| **manager** | Executive summary, key metrics, recommendations, minimal technical details |
| **developer** | Code examples, technical details, implementation specifics |
| **learner** | Step-by-step explanations, examples, progressive complexity |
| **general** | Balanced, accessible language, visual explanations |

### Visual Styles

| Style | Theme | Characteristics |
|-------|-------|-----------------|
| **professional** | `gaia` | Clean, corporate colors, structured layouts |
| **minimal** | `default` | Simple, lots of whitespace, focus on content |
| **visual** | `gaia` + custom CSS | Rich graphics, comparisons, diagrams, screenshots |
| **academic** | Beamer `metropolis` | Formal, math-friendly, citations |

### Language Options

| Option | Usage |
|--------|-------|
| `zh` | Chinese content, Chinese-friendly themes |
| `en` | English content |
| `mixed` | Bilingual titles/subtitles |

### Content Density

| Length | Slides | Bullets per slide |
|--------|--------|-------------------|
| **brief** | 5-8 | 3-4 |
| **standard** | 10-15 | 4-6 |
| **detailed** | 20+ | 5-8 |

## Flavor Examples

**Manager presentation (Chinese):**
```yaml
audience: manager
style: professional
language: zh
length: standard
```
→ Use Gaia theme, executive summary, key findings, recommendations

**Technical tutorial (English):**
```yaml
audience: developer
style: minimal
language: en
length: detailed
```
→ Use default theme, code examples, step-by-step

**Research showcase:**
```yaml
audience: general
style: visual
language: mixed
length: standard
```
→ Use Gaia with custom CSS, screenshots, comparisons

## Available Tools & Best Use Cases

| Tool | Best For | Output Formats | Command |
|------|----------|----------------|---------|
| **Marp** | Modern slides, LLM workflows | PDF, PPTX, HTML | `marp input.md -o output.{pdf,pptx,html}` |
| **Pandoc Beamer** | Academic, math-heavy | PDF | `pandoc input.md -t beamer --pdf-engine=xelatex -o output.pdf` |
| **Pandoc PPTX** | Editable PowerPoint | PPTX | `pandoc input.md -o output.pptx` |
| **reveal.js** | Web presentations | HTML | `pandoc input.md -t revealjs -s -o output.html` |

## Quick Commands

### Generate with Marp (Recommended)

```bash
# PDF output
marp slides.md -o slides.pdf

# PPTX output
marp slides.md -o slides.pptx

# HTML output
marp slides.md -o slides.html

# With custom theme
marp slides.md --theme gaia -o slides.pdf

# Allow local images
marp slides.md -o slides.pdf --allow-local-files
```

### Generate with Pandoc Beamer

```bash
# Basic PDF
pandoc slides.md -t beamer -o slides.pdf

# With XeLaTeX (better font support, required for CJK)
pandoc slides.md -t beamer --pdf-engine=xelatex -o slides.pdf

# With theme
pandoc slides.md -t beamer -V theme:metropolis -o slides.pdf

# CJK support
pandoc slides.md -t beamer --pdf-engine=xelatex \
  -V mainfont="Noto Sans CJK SC" -o slides.pdf
```

### Generate with reveal.js

```bash
pandoc slides.md -t revealjs -s -o slides.html
pandoc slides.md -t revealjs -s -V theme=moon -o slides.html
```

## Markdown Slide Format

### Marp Format

```markdown
---
marp: true
theme: default  # or gaia, uncover
paginate: true
---

# Slide Title

Content here

---

# Next Slide

- Bullet points
- More content
```

### Pandoc/Beamer Format

```markdown
---
title: Presentation Title
author: Author Name
date: 2026
---

# Section Title

## Slide Title

- Content
- More content

---

## Another Slide

Content continues
```

## Generating Visual Showcases

When user wants to compare tools visually:

1. **Create sample slides** with representative content:
   - Title slide with Chinese/English
   - Code highlighting example
   - Math formulas
   - Tables

2. **Generate outputs** from all tools:
   ```bash
   # Marp outputs
   marp sample.md -o output/marp.pdf
   marp sample.md -o output/marp.pptx

   # Beamer outputs
   pandoc sample.md -t beamer --pdf-engine=xelatex -o output/beamer.pdf

   # Pandoc PPTX
   pandoc sample.md -o output/pandoc.pptx
   ```

3. **Create screenshots** for comparison:
   ```bash
   pdftoppm -png -f 1 -l 1 -r 150 output/marp.pdf screenshots/marp
   pdftoppm -png -f 1 -l 1 -r 150 output/beamer.pdf screenshots/beamer
   ```

4. **Build comparison presentation** with embedded screenshots

## Tool Selection Guide

| Scenario | Recommended Tool |
|----------|------------------|
| LLM/Agent automation | Marp |
| Academic/Math-heavy | Pandoc Beamer |
| Editable PPTX needed | Pandoc PPTX or python-pptx |
| Web presentation | reveal.js |
| Enterprise templates | python-pptx |
| Quick prototyping | Marp |

## LLM Integration Pattern

```python
import subprocess

def generate_slides(content: str, output_path: str):
    """Generate slides from LLM-produced content."""
    md_content = f"""---
marp: true
theme: gaia
paginate: true
---

{content}
"""
    with open("/tmp/slides.md", "w") as f:
        f.write(md_content)

    subprocess.run(["marp", "/tmp/slides.md", "-o", output_path], check=True)
    return output_path
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Chinese characters broken (Beamer) | Use `--pdf-engine=xelatex` with CJK font |
| Images not loading (Marp) | Add `--allow-local-files` flag |
| PPTX too large (Marp) | Normal - Marp embeds resources |
| Math not rendering (reveal.js) | Add `--mathjax` flag |

## AI Image Generation (mcp-image)

Generate professional diagrams, charts, and illustrations for slides using the `mcp-image` MCP server powered by Google Gemini.

### Prerequisites

The user must have `mcp-image` configured:

```bash
claude mcp add mcp-image \
  --env GEMINI_API_KEY=AIza... \
  --env IMAGE_OUTPUT_DIR=/absolute/path/to/images \
  -- npx -y mcp-image
```

### Image Generation Tool

Use `mcp__mcp-image__generate_image` with these parameters:

| Parameter | Required | Values | Description |
|-----------|----------|--------|-------------|
| `prompt` | Yes | string | Detailed description of the image |
| `aspectRatio` | No | `1:1`, `16:9`, `9:16`, `21:9` | Default: `16:9` for slides |
| `imageSize` | No | `2K`, `4K` | Default: `2K` |

### Workflow with Image Generation

```
1. User requests slides with visuals
2. Generate slide markdown content
3. Identify slides needing diagrams/charts
4. Call mcp-image to generate visuals
5. Embed generated images in markdown
6. Convert to PDF/PPTX with --allow-local-files
```

### Example: Generate Architecture Diagram

```python
# Step 1: Call mcp-image
mcp__mcp-image__generate_image(
    prompt="Professional flowchart showing: User → API Gateway → Microservices → Database. Clean lines, blue color scheme, white background, no text labels",
    aspectRatio="16:9",
    imageSize="2K"
)
# Returns: /path/to/images/generated-image.png
```

```markdown
# Step 2: Embed in slides
---
# System Architecture

![Architecture Diagram](./images/generated-image.png)
```

### Best Prompts for Slide Visuals

| Visual Type | Prompt Template |
|-------------|-----------------|
| **Flowchart** | "Professional flowchart showing: [steps]. Clean lines, [color] scheme, white background" |
| **Architecture** | "System architecture diagram with [components]. Minimalist style, tech aesthetic" |
| **Comparison** | "Side-by-side comparison chart: [A] vs [B]. Clear labels, contrasting colors" |
| **Timeline** | "Horizontal timeline showing: [events with dates]. Modern design, clean" |
| **Process** | "Step-by-step process diagram: [1] → [2] → [3]. Icons for each step" |
| **Data viz** | "Bar/pie chart showing [data]. Professional style, [colors]" |

### Image Generation Tips

1. **Be specific**: "Blue color scheme, white background, minimalist" > "nice looking"
2. **Specify no text**: Add "no text labels" if you'll add text in slides
3. **Use 16:9**: Best aspect ratio for presentation slides
4. **Request consistency**: "Same style as previous diagram" for visual coherence
5. **Keep it simple**: Complex diagrams may not render well

### Cost Awareness

| Resolution | Cost per Image |
|------------|----------------|
| 2K | ~$0.04-0.07 |
| 4K | ~$0.12-0.24 |

**Tip**: Generate 2K for drafts, 4K for final presentations.

### Complete Example: AI-Enhanced Slides

```markdown
---
marp: true
theme: gaia
paginate: true
---

# Cloud Migration Strategy

---

# Current Architecture

![Current State](./images/current-arch.png)
<!-- Generated: "Legacy monolithic architecture diagram with single database,
     traditional servers, showing bottlenecks. Gray/red color scheme" -->

---

# Target Architecture

![Target State](./images/target-arch.png)
<!-- Generated: "Modern cloud-native architecture with microservices,
     Kubernetes, multiple databases. Blue/green color scheme, clean" -->

---

# Migration Timeline

![Timeline](./images/migration-timeline.png)
<!-- Generated: "Horizontal timeline: Q1 Assessment → Q2 Pilot → Q3 Migration → Q4 Optimization.
     Professional style, blue gradient" -->
```

## Reference Files

- Sample Markdown: `docs/sample-universal.md`
- Marp-specific sample: `docs/sample-marp-format.md`
- Research report: `docs/report-research-zh.md`
- Showcase presentation: `docs/presentation-showcase-zh.md`
