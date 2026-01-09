# Markdown to Slides Showcase

A research project comparing tools for generating presentation slides from Markdown, with focus on LLM agent integration.

## Overview

This project explores various approaches to convert Markdown into presentation slides (PDF, PPTX, HTML), evaluating each tool's:
- Visual output quality
- Ease of use
- LLM agent integration capability

## Tools Evaluated

| Tool | Output Formats | LLM Score | Best For |
|------|----------------|:---------:|----------|
| **Marp** | PDF, PPTX, HTML | 24/25 | Multi-format, Markdown workflow |
| **python-pptx** | PPTX | 24/25 | Fine control, enterprise templates |
| **reveal.js** | HTML | 23/25 | Web presentations |
| **Slidev** | HTML | 21/25 | Developer talks |
| **Pandoc Beamer** | PDF | 20/25 | Academic, LaTeX |
| **Pandoc PPTX** | PPTX | 20/25 | Simple editable PPTX |

## Quick Start

### Marp (Recommended)

```bash
# Install
npm install -g @marp-team/marp-cli

# Generate PDF
marp docs/sample-universal.md -o output/slides.pdf

# Generate PPTX
marp docs/sample-universal.md -o output/slides.pptx

# Generate HTML
marp docs/sample-universal.md -o output/slides.html
```

### Pandoc Beamer

```bash
# Install
sudo apt install pandoc texlive-xetex

# Generate PDF (with CJK support)
pandoc docs/sample-universal.md -t beamer --pdf-engine=xelatex -o output/slides.pdf
```

### python-pptx

```bash
# Install
pip install python-pptx

# Run example
python samples/test_python_pptx.py
```

## Project Structure

```
slides_marker/
├── README.md                          # This file
├── CLAUDE.md                          # Claude Code instructions
├── docs/
│   ├── presentation-showcase-zh.md    # Main showcase presentation (Chinese)
│   ├── report-research-zh.md          # Detailed research report (Chinese)
│   ├── sample-universal.md            # Universal test markdown
│   └── sample-marp-format.md          # Marp-specific sample
├── output/                            # Generated slides
│   ├── presentation-showcase-zh.pdf
│   ├── marp_output.pdf
│   ├── pandoc_beamer_*.pdf
│   └── ...
├── screenshots/                       # Visual comparisons
│   ├── marp_default-1.png
│   ├── beamer_metropolis-1.png
│   └── ...
├── samples/
│   └── test_python_pptx.py            # python-pptx example
└── .claude/
    └── skills/md-slides/              # Claude Code skill
```

## Visual Comparison

### Marp vs Beamer (Cover Page)

| Marp (Default) | Beamer (Metropolis) |
|:--------------:|:-------------------:|
| ![Marp](screenshots/marp_default-1.png) | ![Beamer](screenshots/beamer_metropolis-1.png) |

### Code Highlighting

| Marp | Beamer |
|:----:|:------:|
| ![Marp Code](screenshots/marp_code-2.png) | ![Beamer Code](screenshots/beamer_code-3.png) |

### Math Formulas

| Marp (MathJax) | Beamer (LaTeX) |
|:--------------:|:--------------:|
| ![Marp Math](screenshots/marp_math-3.png) | ![Beamer Math](screenshots/beamer_math-4.png) |

## Key Findings

1. **Marp and python-pptx tie for best LLM integration** (24/25)
   - Marp: Simple CLI, multi-format output, Markdown input
   - python-pptx: Full PPTX control, LLM generates Python code

2. **Tool selection depends on use case:**
   - Need PDF/HTML → Marp
   - Need fine PPTX control → python-pptx
   - Academic/Math → Pandoc Beamer
   - Web presentation → reveal.js

3. **CJK (Chinese) support:**
   - Marp: Works out of the box
   - Beamer: Requires `--pdf-engine=xelatex` and CJK fonts

## Claude Code Skill

This project includes a Claude Code skill (`md-slides`) for automated slide generation with flavor support:

```yaml
# Example flavors
audience: manager | developer | learner | general
style: professional | minimal | visual | academic
language: zh | en | mixed
length: brief | standard | detailed
```

Install the skill:
```bash
# Clone skills repo
git clone https://github.com/zl190/claude-skills.git ~/claude-skills

# Install
cd ~/claude-skills && ./install.sh
```

## Documentation

- **[Research Report](docs/report-research-zh.md)** - Detailed analysis (Chinese)
- **[Showcase Presentation](docs/presentation-showcase-zh.md)** - Main presentation source (Chinese)
- **[Sample Universal](docs/sample-universal.md)** - Test markdown with code, math, tables
- **[Sample Marp](docs/sample-marp-format.md)** - Marp-specific format example

## License

MIT
