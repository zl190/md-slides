---
theme: default
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Markdown 幻灯片工具对比
---

# Markdown 幻灯片工具对比

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---

# Why Markdown for Slides?

<v-clicks>

- **Version Control**: Plain text works with Git
- **Portability**: Write once, export anywhere  
- **Focus on Content**: Separate content from styling
- **Developer Friendly**: Use familiar tools and workflows

</v-clicks>

---
layout: two-cols
---

# Code Examples

Slidev supports syntax highlighting out of the box

```python
def hello_world():
    print("Hello, Slidev!")
    return 42
```

::right::

# Features

- Vue Components support
- Live coding
- Recording & Export
- Presenter mode
- Drawing annotations
