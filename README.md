<h1 align="center">md-slides</h1>

<p align="center">
  <strong>A Claude Code skill for generating slides from Markdown</strong>
</p>

<p align="center">
  <a href="#installation">Install</a> •
  <a href="#usage">Usage</a> •
  <a href="#flavors">Flavors</a> •
  <a href="https://zl190.github.io/md-slides/">Live Demo</a> •
  <a href="docs/presentation-showcase-zh.pdf">Showcase (PDF)</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Skill-blueviolet?logo=anthropic" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/Markdown-000?logo=markdown" alt="Markdown">
  <img src="https://img.shields.io/badge/LaTeX-008080?logo=latex" alt="LaTeX">
  <img src="https://img.shields.io/badge/Marp-CLI-blue?logo=markdown" alt="Marp">
  <img src="https://img.shields.io/badge/Pandoc-Beamer-orange?logo=latex" alt="Pandoc">
  <img src="https://img.shields.io/badge/License-MIT-yellow" alt="License">
</p>

<p align="center">
<img src="assets/flowchart.png" width="700" alt="How md-slides works">
</p>

---

## What is this?

A **Claude Code skill** that generates presentation slides from Markdown. Just describe what you want, and Claude creates the slides.

```bash
# In Claude Code:
/md-slides "Create a 5-slide presentation about Python async programming"
```

Claude will:
1. Write the Markdown content
2. Choose the best tool (Marp, Beamer, etc.)
3. Generate PDF/PPTX/HTML output

## Installation

```bash
# Clone this repo
git clone https://github.com/zl190/md-slides.git

# The skill is in .claude/skills/md-slides/
# Claude Code auto-discovers skills in your project
```

## Usage

The skill uses natural language — just describe what you want:

```bash
# Generate from a topic
/md-slides "Create slides about machine learning basics"

# Convert existing markdown
/md-slides "Convert slides.md to PDF"

# With style preferences
/md-slides "Create slides about Q4 results, executive style, keep it brief"
```

**Workflow:** When generating from a prompt, Claude writes the `.md` file first, giving you a chance to adjust the content if needed.

<p align="center">
<img src="assets/hero.png" width="600" alt="Markdown to Slides concept">
</p>

## Flavors

Claude understands these style preferences:

| Flavor | Options | Default |
|--------|---------|---------|
| **audience** | `manager` · `developer` · `learner` · `general` | general |
| **style** | `professional` · `minimal` · `visual` · `academic` | professional |
| **language** | `en` · `zh` · `mixed` | en |
| **length** | `brief` (5-8) · `standard` (10-15) · `detailed` (20+) | standard |

### Examples

```bash
# Executive summary
/md-slides "Q4 results for management, brief and professional"

# Technical tutorial
/md-slides "Git branching tutorial for developers, detailed with code examples"

# Research presentation
/md-slides "ML research findings, academic style, bilingual"
```

## Supported Tools

The skill automatically selects the best tool:

| Tool | Formats | Best For |
|------|---------|----------|
| **[Marp](https://marp.app/)** | PDF, PPTX, HTML | General purpose (default) |
| **[Pandoc Beamer](https://pandoc.org/)** | PDF | Academic, math-heavy |
| **[python-pptx](https://python-pptx.readthedocs.io/)** | PPTX | Template-based, fine control |
| **[reveal.js](https://revealjs.com/)** | HTML | Web presentations |

> **Note:** Marp only requires Node.js (`npm install -g @marp-team/marp-cli`). Beamer requires a full LaTeX installation (`sudo apt install texlive-full` ~4GB).

## Visual Comparison

### Marp vs Beamer Output

<table>
<tr>
<th>Marp (Gaia Theme)</th>
<th>Beamer (Metropolis)</th>
</tr>
<tr>
<td><img src="assets/marp_gaia-1.png" width="400" alt="Marp"></td>
<td><img src="assets/beamer_metropolis-1.png" width="400" alt="Beamer"></td>
</tr>
</table>

### Code & Math Rendering

<table>
<tr>
<th>Code (Marp)</th>
<th>Math (Beamer)</th>
</tr>
<tr>
<td><img src="assets/marp_code-2.png" width="400" alt="Code"></td>
<td><img src="assets/beamer_math-4.png" width="400" alt="Math"></td>
</tr>
</table>

## Manual Usage (without Claude)

If you want to use the tools directly:

<details>
<summary><strong>Marp CLI</strong></summary>

```bash
npm install -g @marp-team/marp-cli

marp slides.md -o slides.pdf
marp slides.md -o slides.pptx
marp slides.md -o slides.html
```

</details>

<details>
<summary><strong>Pandoc Beamer</strong></summary>

```bash
sudo apt install pandoc texlive-xetex

pandoc slides.md -t beamer --pdf-engine=xelatex -o slides.pdf
```

</details>

<details>
<summary><strong>reveal.js</strong></summary>

```bash
pandoc slides.md -t revealjs -s -o slides.html
```

</details>

## Project Structure

```
.claude/skills/md-slides/   # The Claude Code skill
docs/                       # Sample markdown & research
assets/                     # Comparison screenshots
```

## Research

This skill is based on research comparing 6 markdown-to-slides tools for LLM integration. See the [full report](docs/report-research-zh.md) (Chinese).

**Key finding:** Marp and python-pptx scored highest (24/25) for LLM integration due to simple CLI, text-based input, and clear error messages.

## License

MIT
