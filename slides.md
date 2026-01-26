---
# try also 'default' to start simple
theme: dracula
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# some information about your slides (markdown enabled)
title: Adriel Coding Test
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply UnoCSS classes to the current slide
class: text-left
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 35min
---

# Adriel Coding Test


<div @click="$slidev.nav.next" class="py-2 text-xl" hover:bg="white op-10">
  BI Dashboard Widget 구현
<carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>


---
transition: slide-up
src: ./pages/purpose.md
---
---
src: ./pages/skills.md
---
---
transition: slide-up
src: ./pages/requirements_widget.md
---
---
transition: slide-up
src: ./pages/requirements_sort.md
---
---
transition: slide-up
src: ./pages/requirements_scroll.md
---
---
transition: slide-up
src: ./pages/requirements_filter.md
---
---
src: ./pages/requirements_url.md
---
---
transition: slide-up
src: ./pages/api.md
---
---
src: ./pages/api_endpoints.md
---
---
transition: slide-up
src: ./pages/api_guide_pagination.md
---
---
transition: slide-up
src: ./pages/api_guide_sort.md
---
---
transition: slide-up
src: ./pages/api_guide_filter.md
---
---
src: ./pages/api_guide_combination.md
---
---
src: ./pages/result.md
---
