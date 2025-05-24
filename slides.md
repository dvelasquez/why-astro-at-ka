---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./cover.png
# some information about your slides (markdown enabled)
title: "Re-thinking Next.js: Why We Picked Astro for Kleinanzeigen's High-Traffic Frontend"
info: |
  ## ReactJS Barcelona Meetup
  Presentation by Danilo Velasquez

  Based on [this blog article](https://d13z.dev/blog/07-why-kleinanzeigen-picked-astro-over-nextjs/)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# Re-thinking Next.js: Why We Picked Astro for Kleinanzeigen's High-Traffic Frontend

<div class="pt-12">
  Danilo Velasquez <br/>
  Staff Software Engineer @ Kleinanzeigen.de
</div>

<div class="absolute bottom-8 left-8"> 
  ReactJS Barcelona Meetup
</div>
<div class="absolute bottom-8 right-8">
  June 10th, 2025
</div>

---
layout: two-cols-header
---

## A Bit of History: Me & Kleinanzeigen

::left::

<br/> 

### Danilo Velasquez
* Web Platform Engineer @ Kleinanzeigen.de
* 14 years experience
* #UseThePlatform
* `d13z.dev`

::right::

![Kleinanzeigen Evolution](https://placehold.co/600x400?text=Kleinanzeigen:+15+Years+Growth) 
### Kleinanzeigen.de, top 1 classifieds DE
* **~15 Years** Strong
* Startup Roots ➡️ PE Ownership
* Mandate: **GROW!** 🚀

<!--
asd
-->

---
layout: center 
---

## The Challenge: A Platform in "Adolescence"

![Platform Adolescence](https://placehold.co/700x500?text=Startup+-->+Adolescence+<--+Enterprise)

---
layout: two-cols 
---

### The "Heritage" Core
![Java Monolith](https://placehold.co/500x350?text=Java+Monolith+|+jQuery/JSP+Frontend)
* Java Springboot
* JSP/Moustache
* jQuery/Vanilla JS

::right::

### ...Emerging Cracks
![Hybrid System](https://placehold.co/500x350?text=Monolith+PLUS+~50+MFEs)
* **~50** Preact/TS Widgets
* Tactical Fixes ➡️ Complexity

---
layout: two-cols-header
---

## The Monolith's Grip: Mounting Pressures

::left::

### Developer 😩
![Developer Pain Visual](https://placehold.co/500x350?text=Developer+Frustration)
* Local Setup "Quicksand"
* Glacial Dev Cycles
* The "Haunted Forest"

::right::

### Business 📉
![Business Pain Visual](https://placehold.co/500x350?text=Business+Bottleneck)
* Time-to-Market Crisis
* Stagnation & Tech Debt
* Speed vs. Stability Tension

---
---

## A Different Beast: The Next.js Unification Saga (Cancelled)

![Complex Project Visual](https://placehold.co/700x400?text=The+MASSIVE+Next.js+Project)

* Goal: Unify multiple marketplaces ➡️ **One GIGANTIC Next.js app**
* ~1.5 years of hands-on experience
* Key Lesson: **Scaling Self-Hosted Next.js is HARD**

---
layout: center
---

## The Crossroads: Time for a New Path

![Decision Point](https://placehold.co/600x400?text=New+Strategy+Needed!)

* **Mandate:** Modernize core for GROWTH
* **Constraints:**
    * Leverage React/Preact & TypeScript
    * Improve DX & Performance
    * **Critical: Self-Host at Scale**

---
---

## Re-Evaluating Next.js: A Sober Look

![Next.js Scrutiny](https://placehold.co/600x400?text=Next.js+Under+the+Microscope)

* **Pros:** Familiarity, Ecosystem, React ❤️
* **Cons (for *Kleinanzeigen's* scale & needs):**
    * Self-Hosting Friction (Vercel-first an issue)
    * Perf. with 3rd Parties (Hydration/Reconciliation complexity)
    * RSCs: A workaround for *our* minimal JS goal?
    * "Monolith PTSD" from Unification Project

---
layout: two-cols
---

::left::

### Deno / Fresh
![Deno/Fresh Logo](https://placehold.co/400x300?text=Deno+|+Fresh)
* **Pros:** Modern, Preact ❤️, SSR Default
* **Cons:** Smaller Community, Newness, Internal Approval Hurdles

::right::

### Astro Emerges
![Astro Logo/Concept](https://placehold.co/400x300?text=Astro+ 등장!) 
* Minimal JS by Default
* UI Agnostic (Preact!)
* **Island Architecture!** 🏝️

---
layout: center
---

## The "Aha!" Moment: Island Architecture 🏝️

![Island Architecture Diagram](https://placehold.co/700x500?text=Static+HTML+Ocean+|+Interactive+JS+Islands)
* **Our Pages:** ~80% Static Content / ~20% Interactive Widgets
* **Astro Default:** Send HTML. JS is Opt-In for "Islands".
* **Benefit:** Solves 3rd Party Script vs. Hydration Battles!

---
---

## From Theory to Reality: PoC & The Green Light

![Team Decision & PoC](https://placehold.co/700x400?text=PoC+Success+|+CoP+Approval)

* **PoC:** Homepage, Search, Detail pages + GDPR Preact Widget
* **Process:** ADR / RFC ➡️ CoP Feedback (4 weeks)
* **Rollout:** Homepage 1% ➡️ 10% ➡️ 40% ➡️ **100% Live!**

---
layout: two-cols-header # Or similar
---

## Our Astro Blueprint: Key Decisions

::left::
![Multi-App Diagram](https://placehold.co/500x350?text=Domain-Specific+Astro+Apps)
* **No More Monoliths!**
    * Multiple Astro Apps per Domain
    * Team Autonomy & Independent Releases

::right::
![Shared Libs & SSR](https://placehold.co/500x350?text=Shared+Libs+|+SSR+|+Preact+|+Tailwind)
* **Shared Libraries** (Monorepo)
* **SSR** (Node.js Adapter)
* **Preact** & **TailwindCSS**

---
---

## Early Wins: Developer Velocity & Happiness 🚀

![Dev Velocity](https://placehold.co/700x400?text=Happy+Developers+|+Fast+CI/CD)

* **Onboarding:** Days ➡️ **<15 Minutes!**
* **CI/CD:**
    * Java Full Release: **>1 Hour**
    * Astro Full Release: **~7-10 Minutes Total!**
    * (Lint/Unit: ~1.5m, E2E: ~2m, Build/Deploy: ~5m)
* **Dev Quotes:** *"Smooth & easy"*, *"Great docs"*, *"Modern"*

---
layout: two-cols
---

::left::

### Web Performance  lighthouse
![Performance Graph](https://placehold.co/500x350?text=Lighthouse:+Java+64+->+Astro+69)
* Java CWV: Mostly Green (LCP ~2.3s)
* Astro CWV: **Maintained!** (LCP ~2.0s)
* *Room for Astro-specific optimization!*

::right::

### Widget Reuse ✅
![Widget Integration](https://placehold.co/500x350?text=Preact+Widgets+in+Astro)
* Existing Preact widgets integrated easily.
* *Challenge:* Managing multiple Preact versions.

---
---

## The Learning Curve & Ongoing Challenges 🤔

![Challenges Ahead](https://placehold.co/700x400?text=Learning+|+Testing+|+Coordination)

* **Astro Onboarding:** `.astro` syntax, `defineAction()` (for some)
* **Tooling Shift:** Vite/Vitest vs Webpack/Jest
* **Data Fetching:** New APIs for decoupled frontend
* **Testing Preact + styled-jsx + Vitest:** Tricky! (Accelerated Tailwind move)
* **Multi-App Coordination:** Platform team vigilance needed!
* **Server Features:** Maturing (Logging, Monitoring)

---
layout: center
---

## Key Takeaways for React Developers 💡

![React Takeaways](https://placehold.co/700x500?text=Lessons+for+the+React+Ecosystem)

* **Next.js isn't *always* the default.** (Context matters!)
* Consider **Island-like patterns** for less JS.
* **Preact:** Still a great lightweight choice.
* **DX & CI/CD Speed:** Huge impact on velocity!

---
layout: center
---

## Conclusion & Q&A

![Conclusion Graphic](https://placehold.co/600x400?text=Astro+@+Kleinanzeigen:+The+Right+Fit)

* **Astro: Right choice *for Kleinanzeigen's* needs.**
    * Solved specific scale, perf, & self-hosting issues.
* Empowered Teams, Faster Delivery ➡️ Value Creation
* The Journey Continues!

**Blog Post:** `d13z.dev/blog/07-why-kleinanzeigen-picked-astro-over-nextjs`
**Questions?**

<div class="abs-bl m-6">
  <carbon-logo-github class="inline-block"/> dvelasquez 
</div>
