---
layout: ../../layouts/MainLayout.astro
title: Web Animations Primer
description: Web Animations Primer — My Talk
---

#### Date: Nov 16, 2025

Animations Primer: all you need to know before starting animations

### Why Animations?

Animations make the web feel alive.
They make things interactive, playful, memorable.

I have a quote for this:

> "When your body moves, your brain improves."

Our brain naturally loves movement — watching planets orbit, fire crackle, waves, whatever.

And honestly… I always felt animations were magical.
They resemble human imagination directly in pixels.

If you can imagine it, with a few pointers —
you can create the effect.

### Fun Fact

![Winamp Visualizer](/winamp.jpeg)

```
My first conscious animation moment was the Winamp music player.
Disco lights, wavy patterns…

Bhai, those visualizers were next level.
```

### Ways to Create Animations Today

**1. CSS Animations**

- Used everywhere for simple UI/UX motion
- Built into frameworks like Tailwind
- Can be triggered with JavaScript
- Best for: transitions, hover effects, loading spinners

**2. Canvas/WebGL Based**

- Three.js, Particle.js, custom canvas loops
- For heavy effects, 3D, and movie-like scenes
- Best for: complex visualizations, games, interactive art

**3. Third-Party Libraries**

- GSAP (GreenSock Animation Platform)
- Framer Motion (React animations)
- ScrollTrigger (scroll-based animations)
- Best for: complex timelines, physics-based motion, scroll animations

### What Makes Animations Possible? (GPU Explanation)

![GPU Architecture](/gpu.jpeg)

_Image credit: [Sarah Drasner](https://www.linkedin.com/in/sarahdrasner/)_

**CPU = brain**  
**GPU = muscle**

#### What is a GPU?

A GPU (Graphics Processing Unit) is **hardware** — a physical chip in your device. It's not something browsers "have," but something browsers **use**.

Think of it like this:

- **GPU** = The engine (hardware chip)
- **Drivers** = The interface (C++ software that talks to the GPU)
- **Browser engines** = The bridge (V8, SpiderMonkey, WebKit connect JavaScript/CSS to GPU)

#### Does Every Browser Use GPU?

Yes! All modern browsers (Chrome, Firefox, Safari, Edge) use GPU acceleration when available. If your device doesn't have a GPU, browsers fall back to CPU rendering (much slower).

#### What Does GPU Do in Browsers?

The GPU handles the visual heavy lifting:

1. **Rendering** - Drawing pixels (text, images, shapes) in parallel
2. **Compositing** - Combining layers into the final image you see
3. **Transform/Opacity** - Smoothly animating CSS transforms and opacity
4. **WebGL/WebGPU** - Direct GPU access for 3D graphics and complex visualizations

#### The Animation Pipeline

Here's how your animation flows from code to screen:

```
┌─────────────────────────────────────────────────────────────┐
│                    ANIMATION PIPELINE                         │
└─────────────────────────────────────────────────────────────┘

┌──────────────┐
│  HTML/CSS    │  ← Your code: transform, opacity, animation
│  JavaScript  │
└──────┬───────┘
       │
       ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 1: PARSE & LAYOUT (CPU)                                │
│  ─────────────────────────────────────────────────────────  │
│  • Browser parses HTML/CSS                                   │
│  • Calculates element positions, sizes                       │
│  • Determines which elements need animation                  │
└──────────────────┬───────────────────────────────────────────┘
                   │
                   ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 2: PAINT (CPU → GPU)                                   │
│  ─────────────────────────────────────────────────────────  │
│  • Draws text, images, shapes                                 │
│  • Creates visual representation of elements                 │
│  • Prepares layers for compositing                           │
└──────────────────┬───────────────────────────────────────────┘
                   │
                   ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 3: LAYER CREATION (CPU)                                 │
│  ─────────────────────────────────────────────────────────  │
│  • Browser creates separate layer for animated element        │
│  • Isolates animated properties (transform, opacity)         │
│  • Marks layer as "GPU-accelerated"                           │
└──────────────────┬───────────────────────────────────────────┘
                   │
                   ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 4: GPU COMPOSITING ⚡ (GPU)                             │
│  ─────────────────────────────────────────────────────────  │
│  • GPU receives layer data                                    │
│  • Applies transforms/opacity changes                         │
│  • Combines all layers into final image                       │
│  • Renders at 60fps (16.67ms per frame)                      │
└──────────────────┬───────────────────────────────────────────┘
                   │
                   ▼
┌──────────────────────────────────────────────────────────────┐
│  STEP 5: DISPLAY (GPU → Screen)                              │
│  ─────────────────────────────────────────────────────────  │
│  • Final composited frame sent to display                    │
│  • Smooth animation visible to user                           │
│  • Process repeats for each frame                             │
└───────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────┐
│  KEY INSIGHT:                                                 │
│  ─────────────────────────────────────────────────────────  │
│  Steps 1-3: CPU does the thinking (layout, calculations)     │
│  Steps 4-5: GPU does the heavy lifting (rendering, display)   │
│                                                               │
│  For smooth animations, keep Steps 1-3 minimal and           │
│  let GPU handle Steps 4-5!                                   │
└───────────────────────────────────────────────────────────────┘
```

**When you create a CSS animation:**

1. **Parse & Layout** (CPU) - Browser calculates where everything goes
2. **Paint** (CPU → GPU) - Elements are drawn
3. **Layer Creation** (CPU) - Animated element gets its own layer
4. **GPU Compositing** ⚡ (GPU) - GPU smoothly animates the layer at 60fps
5. **Display** (GPU → Screen) - Final frame appears on your screen

**Result:** Buttery smooth animations! 🎬

Everything visual you see — smoke, fire, motion blur —
is powered by the GPU.

The more I explore web animations,
the more respect I get for the C++ developers who built V8, SpiderMonkey, and WebKit.

They made this whole experience possible.
