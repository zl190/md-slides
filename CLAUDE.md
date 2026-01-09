# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## Project Overview

Research project comparing Markdown-to-slides tools with focus on LLM agent integration. Evaluates Marp, Pandoc Beamer, python-pptx, reveal.js, and Slidev.

## Key Files

- `docs/report-research-zh.md` - Detailed research report (Chinese)
- `docs/presentation-showcase-zh.md` - Main showcase presentation (Chinese)
- `docs/sample-universal.md` - Universal test markdown
- `samples/test_python_pptx.py` - python-pptx example

## Build Commands

### Marp (Recommended)

```bash
# Generate PDF/PPTX/HTML
marp docs/presentation-showcase-zh.md -o output/presentation-showcase.pdf --allow-local-files
marp docs/presentation-showcase-zh.md -o output/presentation-showcase.pptx --allow-local-files
marp docs/presentation-showcase-zh.md -o output/presentation-showcase.html --allow-local-files
```

### Pandoc Beamer

```bash
# With XeLaTeX (required for CJK)
pandoc docs/sample-universal.md -t beamer --pdf-engine=xelatex -o output/slides.pdf

# With theme
pandoc docs/sample-universal.md -t beamer -V theme:metropolis --pdf-engine=xelatex -o output/slides.pdf
```

### reveal.js

```bash
pandoc docs/sample-universal.md -t revealjs -s -o output/slides.html
```

## Claude Code Skill

This project includes a `md-slides` skill in `.claude/skills/md-slides/` with:
- Multi-format output support
- Flavor system (audience, style, language, length)
- Tool selection guidance

## Key Findings

1. **Marp & python-pptx** tie for best LLM integration (24/25)
2. Use **Marp** for multi-format output, **python-pptx** for fine PPTX control
3. **Pandoc Beamer** best for academic/math content
