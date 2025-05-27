---
# For personal use only
theme: 'seriph'
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

<div class="slidev-layout cover flex flex-col justify-center items-center text-center h-full">
  <div class="my-auto">
    <h2>Re-thinking Next.js:</h2>
    <h1 class="text-5xl font-bold">
      Why We Picked Astro for Kleinanzeigen's High-Traffic Frontend
    </h1>
    <p class="text-xl mt-4 opacity-75">
      Real-world experiences from Germany's largest classifieds site.
    </p>
    <p class="text-1xl mt-8">
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
layout: default
---
# The Search for a Modern Solution 🚀

* **Goal:** Evolve the *entire* platform, especially core pages, with modern tools.
* **Key Requirements:**
    * Leverage existing team skills: **React/Preact & TypeScript**.
    * Improve Developer Experience (DX) & Performance.
    * Excellent **self-hosting** support (critical for our scale).
* **Evaluation Process:**
    * Simple Demo App: Homepage, Search Results, Item Details.
    * Integrated a complex existing Preact widget (GDPR banner) to test compatibility.

---
layout: two-cols
---

# Option 3: Astro

<div class="prose">

**The Challenger**

* **Pros:**
    * 🏝️ **Island Architecture:** Send HTML by default, hydrate only specific components (`<client:load>`, etc.). Directly addressed Next.js hydration/3rd party script issues. **Less JS = Faster Loads!**
    * 🧩 **UI Framework Agnostic:** React, Preact, Vue, Solid, Svelte - flexibility for the future.
    * Mature & **Self-Hosting First:** Vibrant community, stable, first-class Node.js self-hosting support.
    * Demo successful, GDPR banner integrated.
* **Cons/Considerations:**
    * Steeper learning curve: `.astro` syntax, frontmatter.
    * New Tooling: Vite & Vitest (team mostly knew Webpack & Jest).
    * `styled-jsx` SSR limitation: Existing widgets would render client-side until migrated to TailwindCSS.

</div>

::right::

<img src="/2025-04-23/astro-logo.png" class="h-60" alt="Astro Logo"/>

---
layout: default
---

# Why Astro? The Island Architecture Advantage 🏝️

**Shipping HTML First, JavaScript Second (Only When Needed!)**

* **The Next.js Hydration Problem (for us):**
    1.  Server renders full React page.
    2.  Client renders HTML.
    3.  *3rd party scripts run, modify HTML.*
    4.  Full React JS bundle downloads & runs.
    5.  React compares its VDOM to (now modified) browser DOM &rarr; **Reconciliation pain, repaints.**
    6.  More 3rd party scripts run...
    * Result: Multiple re-renders, potential race conditions, poor Core Web Vitals.
* **Astro's Approach:**
    1.  Server renders HTML.
    2.  Client renders HTML (mostly static).
    3.  *Only* JS for explicit `<client:*> ` components is sent and hydrated.
    * Result: **Less JS, faster loads, smaller interactive islands, fewer conflicts.**

<img src="/2025-04-23/islands-architecture.png" class="mt-4 rounded-lg shadow-md" alt="Islands Architecture Diagram"/>

---
layout: default
---

# The Decision & Rollout ✅

* **Process:**
    * Platform team: Demos & evaluations.
    * Architectural Decision Record (ADR) + RFC (4 weeks) for Community of Practice (CoP) feedback.
    * **Astro Chosen!**
* **Buy-in & Proof of Concept (PoC):**
    * Workshops to introduce Astro to engineers.
    * Partnered with Homepage team to rebuild it in Astro.
    * Gradual rollout: **1% &rarr; 10% &rarr; 40% &rarr; 100%** traffic.

---
layout: default
---

# Implementation: Multi-App & Shared Components 🏗️

* **Key Decision: NO single giant Astro app!**
    * Separate Astro apps per business domain (Homepage, Search, Item Details etc.).
    * **Benefit:** Team autonomy, independent releases.
    * **Challenge:** More responsibility for Platform team (tooling, consistency).
* **Shared Libraries:**
    * Header, footer, etc., as versioned packages in a Monorepo:
        * Lerna-Lite, Turborepo, npm workspaces.
    * RenovateBot for automated dependency updates.
* **Tech Choices:**
    * **SSR** with Node.js adapter (SSG impractical for 50M+ ads).
    * **Preact** as primary UI framework (team experience, smaller bundles).
    * **TailwindCSS** adopted fully (new design system, styled-jsx issues).

<img src="/2025-04-23/diagram-architectures.jpg" class="h-48 mt-4 rounded-lg shadow-md" alt="Monolith vs Multi-App Architecture"/>

---
layout: two-cols
---

# Results: Developer Experience Wins! 🎉

* **Onboarding:** `<15 minutes` for new Astro Homepage vs. `days` for Java monolith.
* **CI/CD Drastically Faster:**
    * Linting & Unit Tests: `~1.5 minutes`
    * E2E Tests: `~2 minutes`
    * Build & Deploy: `~5 minutes`
    * (vs. Java: 15 min non-prod deploy, >1 hour full prod release).
* **Developer Quotes:**
    * *"Very smooth and easy to use."*
    * *"Great! It is easy to install and run, documentation is also very good."*
    * *"very easy to learn coming from react with next.js experience"*
    * *"Nice and modern."*

---
src: ./pages/11.-results-developer-experience-wins.md
---

---
src: ./pages/12.-results-performance-widget-reuse.md
---

---
layout: center
class: text-center
---

# Conclusion: Astro - The Right Tool for *Our* Job

<img src="/2025-04-23/conclusion-astro-logo.png" class="h-40 mx-auto my-6" alt="Astro Logo with Text Conclusion"/>
**Why Astro over Next.js for Kleinanzeigen?**

* 🏝️ **Island Architecture** was a perfect fit for our content-heavy, SEO-critical pages.
* ⚡ Directly addressed performance bottlenecks (hydration, 3rd party scripts).
* 🛠️ Improved DX, faster CI/CD, framework flexibility, strong self-hosting.

Astro empowered us to tackle our Value Creation Plan with speed and confidence.

---
src: ./pages/15.-when-might-astro-be-right-for-you.md
---

---
src: ./pages/08.-why-astro-island-architecture.md
---

---
src: ./pages/09.-the-decision-and-rollout.md
---

---
src: ./pages/10.-implementation-multi-app-shared-components.md
---

---
src: ./pages/13.-challenges-and-learning-curves.md
---

---
src: ./pages/14.-conclusion-astro-right-tool.md
---

---
src: ./pages/16.-thank-you-and-qa.md
---