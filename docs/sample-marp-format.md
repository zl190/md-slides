---
marp: true
theme: default
paginate: true
---

# Introduction

## Why Markdown for Slides?

- **Version Control**: Plain text works with Git
- **Portability**: Write once, export anywhere
- **Focus on Content**: Separate content from styling
- **Automation**: Easy integration with CI/CD and LLM agents

---

# Code Highlighting

## Python Example

```python
def fibonacci(n: int) -> int:
    """Calculate the nth Fibonacci number."""
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Usage
result = fibonacci(10)
print(f"F(10) = {result}")
```

---

# Mathematical Formulas

## The Quadratic Formula

Given $ax^2 + bx + c = 0$, the solutions are:

$$x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$

## Euler's Identity

$$e^{i\pi} + 1 = 0$$

---

# Structured Content

## Feature Comparison

| Feature | Support |
|---------|---------|
| PDF Export | Yes |
| PPTX Export | Varies |
| Custom Themes | Yes |
| LLM Integration | Excellent |

## Key Points

1. Simple syntax
2. Multiple output formats
3. Extensible with plugins

---

# Conclusion

## Summary

> Markdown-based slides combine simplicity with power,
> making them ideal for automated workflows.

**Next Steps:**
- Choose the right tool for your needs
- Customize themes to match your brand
- Integrate with your development workflow

---

# Thank You

Questions?
