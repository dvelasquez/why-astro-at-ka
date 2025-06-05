---
# For personal use only
theme: 'default'
# aspect ratio for the slides
aspectRatio: '16/9'
# enable presenter mode, can be boolean, 'dev' or 'build'
presenter: 'dev'
# syntax highlighter, can be 'prism' or 'shiki'
highlighter: 'shiki'
# show line numbers in code blocks
lineNumbers: false
# enable slide recording, can be boolean, 'dev'
record: 'dev'
# allow 'click' animation globally
clicks: true
# draw slides with mouse
drawings:
  enabled: true
  persist: false
  presenterOnly: false
  syncAll: true
# default frontmatter applies to all slides
defaults:
  layout: 'default'
# slide transition
transition: fade
# enable print mode, can be 'pdf' or 'html'
print: false
# information for the slides, available in all slides through $frontmatter
info: |
  ## Re-thinking Next.js: Why We Picked Astro for Kleinanzeigen's High-Traffic Frontend
  Danilo Velasquez
  ReactJS Barcelona, June 10th, 2025
# favicon, can be a local file path or URL
favicon: '[https://d13z.dev/favicon.svg](https://d13z.dev/favicon.svg)'
# controls whether texts in slides are selectable
selectable: true
# enable slide recording, can be boolean or 'dev'
---

<div class="slidev-layout cover flex flex-col justify-center items-center text-center h-full p-8">
  <div class="my-auto max-w-3xl mx-auto">
    <h2 class="text-2xl mb-2">Re-thinking Next.js:</h2>
    <h1 class="text-4xl font-bold leading-tight mb-6">
      Why We Picked Astro for<br/>
      Kleinanzeigen's High-Traffic Frontend
    </h1>
    <p class="text-xl mt-4 opacity-75 mb-8">
      Real-world experiences from Germany's largest classifieds site.
    </p>
    <p class="text-lg mt-8">
      <strong>Danilo Velasquez</strong>
      <br/>
      <span class="opacity-75">Staff Software Engineer @ Kleinanzeigen</span>
    </p>
  </div>

  <div class="absolute bottom-2 left-8 text-left">
    <p class="text-md">ReactJS Barcelona</p>
    <p class="text-sm opacity-75">June 10th, 2025</p>
  </div>

  <div class="absolute bottom-8 right-8 flex items-center gap-3">
    <img src="/logo-kleinanzeigen-horizontal.svg" class="h-8" alt="Kleinanzeigen Logo"/>
    <img src="/2025-04-23/astro-logo.png" class="h-8" alt="Astro Logo"/>
    <img src="/reactjs_barcelona_logo.jpg" class="h-8" alt="ReactJS Barcelona Logo"/>
  </div>
</div>

---
src: ./pages/02.-who-is-ka.md
---

---
src: ./pages/03.-the-challenge.md
---

---
src: ./pages/04.-the-search-for-a-modern-solution.md
---

---
src: ./pages/05.-option-1-nextjs.md
---

---
src: ./pages/06.-option-2-deno-fresh.md
---

---
src: ./pages/07.-option-3-astro.md
---

---
src: ./pages/08.-why-astro-island-architecture.md
---

---
src: ./pages/09.-the-rendering-problem.md
---

---
src: ./pages/10.-the-decision-and-rollout.md
---

---
src: ./pages/11.-java-monolith-status-quo.md
---

---
src: ./pages/12.-the-new-approach.md
---

---
src: ./pages/13.-results-developer-experience-wins.md
---

---
src: ./pages/14.-results-performance-widget-reuse.md
---

---
src: ./pages/15.-challenges-and-learning-curves.md
---

---
src: ./pages/16.-conclusion-astro-right-tool.md
---

---
src: ./pages/17.-when-might-astro-be-right-for-you.md
---

---
src: ./pages/18.-thank-you-and-qa.md
---

---
src: ./pages/99.-animation-demo.md
---

