# Tool Comparison Reference

## LLM Agent Integration Scores

| Tool | Text Input | CLI/API | Template | Error Clarity | Incremental | **Total** |
|------|:----------:|:-------:|:--------:|:-------------:|:-----------:|:---------:|
| **Marp** | 5 | 5 | 4 | 5 | 5 | **24/25** |
| **reveal.js** | 5 | 4 | 5 | 4 | 5 | **23/25** |
| **Slidev** | 5 | 3 | 4 | 4 | 5 | **21/25** |
| **Pandoc Beamer** | 5 | 5 | 4 | 2 | 4 | **20/25** |
| **Pandoc PPTX** | 5 | 5 | 3 | 4 | 3 | **20/25** |
| **python-pptx** | N/A | 5 | 5 | 4 | 5 | **19/20** |

## Slide Element Support

| Element | Marp | Pandoc | python-pptx | reveal.js |
|---------|:----:|:------:|:-----------:|:---------:|
| Text | ✓ | ✓ | ✓ | ✓ |
| Layout | ✓ | ✓ | ✓✓ | ✓ |
| Images | ✓ | ✓ | ✓✓ | ✓ |
| Shapes | - | - | ✓✓ | ✓ |
| Tables | ✓ | ✓ | ✓✓ | ✓ |
| Animation | - | - | ✓ | ✓✓ |

**Legend:** ✓ = Supported, ✓✓ = Full control, - = Not supported

## Output File Sizes (6-slide sample)

| Tool/Format | Size |
|-------------|------|
| Marp PDF | ~88 KB |
| Marp PPTX | ~683 KB |
| Pandoc Beamer | ~36 KB |
| Pandoc PPTX | ~35 KB |
| python-pptx | ~29 KB |

## Installation Commands

```bash
# Marp (recommended)
npm install -g @marp-team/marp-cli

# Pandoc + LaTeX
sudo apt install pandoc texlive-xetex texlive-latex-extra

# python-pptx
pip3 install python-pptx

# Slidev (interactive)
npm init slidev@latest
```

## Beamer Themes

Popular themes: `default`, `metropolis`, `madrid`, `berlin`, `singapore`, `warsaw`

```bash
pandoc slides.md -t beamer -V theme:metropolis -o slides.pdf
```

## reveal.js Themes

Available: `beige`, `black`, `blood`, `league`, `moon`, `night`, `serif`, `simple`, `sky`, `solarized`, `white`

```bash
pandoc slides.md -t revealjs -s -V theme=moon -o slides.html
```
