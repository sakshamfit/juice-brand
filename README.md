# THENGA 🥥 — *A Taste of Kerala in Every Sip*

> An immersive, scroll-driven brand site for **THENGA**, a conceptual coconut-water brand rooted in
> Kerala, India. One page, one continuous story: a green coconut cracks open, the shell halves part,
> and a 3D drink can grows out of the centre — all choreographed to the visitor's scroll position.

**Made by [sakshamfit](https://github.com/sakshamfit).**

![React](https://img.shields.io/badge/React-19.2-61dafb?logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-16.3-black?logo=next.js)
![vinext](https://img.shields.io/badge/vinext-1.0.0--beta.5-f48120?logo=cloudflare&logoColor=white)
![Three.js](https://img.shields.io/badge/Three.js-0.186-black?logo=threedotjs&logoColor=white)
![GSAP](https://img.shields.io/badge/GSAP-3.15-88ce02?logo=greensock&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.2-38bdf8?logo=tailwindcss&logoColor=white)
![Cloudflare Workers](https://img.shields.io/badge/Deploy-Cloudflare%20Workers-f38020?logo=cloudflare&logoColor=white)
![Node](https://img.shields.io/badge/Node-%3E%3D22.13-3c873a?logo=nodedotjs&logoColor=white)

---

## Table of contents

1. [What this site is](#what-this-site-is)
2. [The experience, top to bottom](#the-experience-top-to-bottom)
3. [The collection — five flavours](#the-collection--five-flavours)
4. [How it works](#how-it-works)
5. [Performance and accessibility](#performance-and-accessibility)
6. [Project structure](#project-structure)
7. [Getting started](#getting-started)
8. [Scripts](#scripts)
9. [Design system](#design-system)
10. [Assets and credits](#assets-and-credits)
11. [Hosting, platform and deployment](#hosting-platform-and-deployment)
12. [Notes and limitations](#notes-and-limitations)
13. [Credits](#credits)

---

## What this site is

THENGA is a **brand concept**, not a live commerce store. The site explores a product world —
packaging, flavour identities, origin storytelling and daily rituals — through motion, photography
and real 3D geometry. There is deliberately no pricing, no nutrition panel, no cart and no checkout
provider, because none of that was part of the concept.

The name comes straight from Malayalam: **തേങ്ങ (thenga)** means *coconut* — which is why the
wordmark uses a coconut as its full stop.

What the page does instead of selling:

- **Tells an origin story** — from a whole green coconut, to the water inside it, to Kerala's palms,
  backwaters and Kathakali colour, to a finished 330 ml can.
- **Shows the packaging** — every can label is generated at runtime in Three.js (canvas typesetting
  plus original Kathakali-and-palms artwork), so the cans are real rotatable geometry, not flat images.
- **Lets people browse five flavours** — a draggable carousel with per-flavour colour theming and a
  detail dialog you can step through without closing it.

---

## The experience, top to bottom

| # | Section | What happens |
| --- | --- | --- |
| 0 | **Logo intro** (`app/intro.tsx`) | The letters of `THENGA` rise out of their masks, a coconut drops in and bounces as the full stop, a splash of water droplets arcs away, and a ten-frond palm crown fans open behind the lockup with the Malayalam word തേങ്ങ. The lockup then shrinks into the header logo while the coconut flies to its hero position and the green drains out of the panel. Any click, scroll or key fast-forwards it. |
| 1 | **Hero** | "Paradise in every sip." Oversized condensed headline, a photographic green coconut floating over palm fronds, benefits list, a "Good by Nature" seal, and the Kerala coordinates `9.9312° N 76.2673° E`. |
| 2 | **The journey** (`app/product-scene.tsx`) | A pinned 3D stage driven by scroll: the coconut rotates and cracks into two hemispheres, white flesh and a water surface appear, the halves separate, and a lathed drink can grows from the centre and turns through a full rotation. |
| 3 | **Chapter copy** | Four caption beats fade in and out over the same scene — `01 Straight from nature`, `02 Nothing complicated`, `03 Where it all begins` (Kathakali artwork), `04 A little paradise, to go` (packaging detail) — then a full-bleed **KEEP SIPPING** statement. A numbered chapter rail lets you jump between them. |
| 4 | **Pure by nature** (`#nature`) | A deep-green scalloped panel with an oversized statement and the Kathakali motif. |
| 5 | **The collection** (`#collection`) | Five colour-coded product cards in a drag/scroll carousel, each showing its runtime-rendered can. Arrow controls, pointer-drag, and a card that tilts toward the cursor on hover. |
| 6 | **Product dialog** | Clicking a card opens the flavour detail: a can floating among animated fronds, banana leaves, leaflets and coconuts, plus taste, moment and ritual facts, a flavour-dot picker and a "discover the next flavour" step button. |
| 7 | **Our roots** (`#kerala`) | A four-photo collage of real Kerala imagery (Kathakali performer, Palakkad paddy fields, a traditional Kannur home, coconuts on a palm) with opposing parallax, beside the brand's heritage copy. |
| 8 | **From the palms** (`#from-the-palms`) | Full-viewport backwaters landscape with parallax and overlay copy. |
| 9 | **Your everyday** (`#everyday`) | Three ritual cards — *The slow start*, *The fresh reset*, *The golden hour* — in a three-column rhythm. |
| 10 | **Closing pair + footer** | A final campaign panel, then a scalloped footer with navigation, a share/copy-link button, a photography-credits dialog and the full-width THENGA wordmark. |

A fixed header tracks scroll context: the brand mark and menu button switch to their light variant
over green panels and dark photography. A floating "Discover your daily sip" CTA follows the page.

---

## The collection — five flavours

Defined once in [`app/products.ts`](app/products.ts) and consumed by the cards, the dialogs, the
can-label textures and the flavour picker.

| # | Flavour | Colour / ink | The taste | The moment |
| --- | --- | --- | --- | --- |
| 01 | **Original Kerala** | `#d7e1a8` / `#174b32` | Coconut water | Slow mornings & everyday refreshment |
| 02 | **Tender Coconut** | `#eee9ce` / `#626b36` | Tender coconut water | A quiet afternoon moment |
| 03 | **Coconut Lime** | `#c6d75c` / `#2f532c` | Coconut water · Lime | Sun-filled days & fresh starts |
| 04 | **Coconut Mango** | `#f4bf58` / `#805129` | Coconut water · Mango | Golden-hour breaks |
| 05 | **Coconut Pineapple** | `#edd985` / `#656434` | Coconut water · Pineapple | Picnics & a change of scenery |

To add a flavour: append an entry to `products.ts`. The card, the dialog, the picker and the
runtime-rendered can label all pick it up — the label texture typesets the name, the flavour band and
the artwork automatically, and one extra card appears in the carousel.

---

## How it works

**Stack:** React 19 + Next.js 16 App Router, compiled and served by [vinext](https://github.com/cloudflare/vinext)
(Vite → Cloudflare Worker). Styling is Tailwind CSS 4 with a hand-written `globals.css` for the brand
layout; UI primitives come from the bundled shadcn/Base-UI component set.

**Motion — GSAP ScrollTrigger**

- One master tween maps the `.journey` section (`600vh` desktop, `520vh` mobile) to a single
  `progress` value between 0 and 1, written to the `--journey` CSS custom property and to a ref that
  the 3D scene reads every frame.
- Copy beats use a `fade(a, b, c, d)` envelope so each caption enters and leaves inside its own
  scroll window; the hero, coconut and frond get continuous parallax transforms.
- Scrub smoothing is `0.85s`. **Native scrolling is never hijacked** — the intro is the only place
  wheel/touch is intercepted, and only to fast-forward itself.
- Header theme, `.reveal` entrances and photo parallax are separate ScrollTrigger instances.

**3D — Three.js (`app/product-scene.tsx`)**

- The coconut is two deformed `SphereGeometry` hemispheres (vertex-noise shaping) sharing a
  photographically-calibrated husk texture on an unlit, tone-mapping-independent material, with
  flesh rings, an inner shell, a clearcoat water disc, a stem and 120 instanced droplets.
- The can is a real `LatheGeometry` body with re-authored UVs, metal rims, lid and pull tab. Its
  label is a 2048×2048 `CanvasTexture` typeset per flavour, with wrapped side and rear panels that
  stay readable through the full rotation.
- Opening, reveal and exit are `smoothstep` windows over scroll progress, plus gentle pointer
  parallax and ambient float/bob.
- Lighting: `RoomEnvironment` PMREM + hemisphere + key/fill directionals, ACES Filmic tone mapping.

**Software fallback (`app/software-renderer.ts`)**

When WebGL is unavailable, the same Three.js meshes are projected and textured by a small Canvas2D
renderer (painter's-algorithm triangle sort, UV barycentric sampling, linear-space material tinting,
simple directional shading) and throttled to ~24 fps. The page is fully usable without a GPU.

**Progressive loading**

`Intro`, the 3D scene, the foliage and the gallery renderer are `next/dynamic` imports with
`ssr: false`. The heavy scene mounts only after the intro finishes (its chunk is prefetched *during*
the intro), and the five can thumbnails are rendered during `requestIdleCallback` by an offscreen
`ProductGalleryImages` pass that renders once per flavour, exports a data URL and disposes every
geometry, texture and renderer.

---

## Performance and accessibility

- **Reduced motion** — `prefers-reduced-motion` skips the intro entirely, disables parallax and
  entrance offsets, sets scrub to instant, and stops ambient 3D movement.
- **Manual pause** — the header's pause/play button toggles a `motion-paused` class that freezes
  ambient animation page-wide for people who want a still page.
- **Rendering budget** — pixel ratio capped at 1.75, an `IntersectionObserver` stops rendering when
  the stage is off-screen, `document.hidden` short-circuits frames, and all Three.js resources are
  disposed on unmount.
- **Keyboard & semantics** — a "Skip to the collection" link, labelled sections and controls,
  `aria-current="step"` on the chapter rail, `aria-pressed` on the flavour picker, `role="img"` with a
  description on the 3D stage, screen-reader-only dialog titles/descriptions, and a visible
  `:focus-visible` ring.
- **Mobile** — layout reflows at `1050px` and `700px`; the carousel uses `touch-action: pan-x pan-y`
  with drag-vs-tap discrimination so a swipe never fires a click.

---

## Project structure

```
juice-brand/
├── app/
│   ├── layout.tsx            # Metadata, favicon, fonts, root <html>/<body>
│   ├── page.tsx              # The whole site: header, journey, collection, heritage, rituals, footer, dialogs
│   ├── intro.tsx             # Logo intro timeline and its handoff into the hero
│   ├── intro-state.ts        # Shared "bloom" value between the intro and the hero foliage
│   ├── product-scene.tsx     # Three.js coconut + can scene, and the offscreen can-thumbnail renderer
│   ├── software-renderer.ts  # Canvas2D fallback renderer for the same meshes
│   ├── flora.tsx             # Vector coconut fronds, banana leaves and leaflets (generated SVG paths)
│   ├── products.ts           # The single source of truth for the five flavours
│   ├── globals.css           # Brand layout, tokens, responsive rules, reduced-motion rules
│   └── chatgpt-auth.ts       # Optional dispatch-owned sign-in helpers (unused by the public site)
├── components/ui/            # shadcn / Base-UI primitives (the site uses Dialog + lucide icons)
├── public/
│   ├── assets/               # Generated artwork + licensed Kerala photography
│   ├── fonts/                # Self-hosted Barlow Condensed (600/800) and DM Sans
│   └── favicon.svg
├── build/, scripts/          # vinext/Sites build plumbing, Worker entry, install + env helpers
├── db/, drizzle/, examples/  # Optional Cloudflare D1 + Drizzle scaffolding (intentionally empty schema)
├── vite.config.ts            # vinext + Cloudflare plugin, local binding simulation
├── IMAGE-CREDITS.md          # Per-file photography licensing and generated-artwork notes
└── REFERENCE-NOTES.md        # Shot-by-shot adaptation notes for the motion choreography
```

---

## Getting started

**Prerequisites**

- Node.js `>= 22.13.0`
- pnpm (the lockfile is `pnpm-lock.yaml`, `packageManager: pnpm@11.25.0`)

```sh
pnpm install        # or: npm run install:ci  (one locked install against the shared lockfile)
pnpm dev            # vinext dev server with HMR, starting at http://localhost:5173
```

Build and preview the deployable Worker locally:

```sh
pnpm build          # produces dist/, including dist/server/wrangler.json
pnpm start          # runs the built Worker through Wrangler on 127.0.0.1 with local D1/R2 support
```

`pnpm dev` records the running server in ignored `.vinext/` state and rejects a duplicate launch.
Pass `pnpm dev -- --port <port>` or `-- --hostname <host>` to change it. Generated `.sites-runtime/`,
`.vinext/` and `.wrangler/` directories are disposable and ignored by Git.

---

## Scripts

| Command | What it does |
| --- | --- |
| `pnpm dev` | Start the vinext/Vite development server with HMR |
| `pnpm build` | Build the deployable Sites/Worker artifact |
| `pnpm start` | Preview the built Worker locally with D1/R2 support |
| `pnpm lint` | ESLint across the project (ignores `dist` and `.next`) |
| `pnpm db:generate` | Generate Drizzle migrations after a schema change |
| `pnpm install:ci` | Perform the one locked dependency install |

---

## Design system

| Token | Value |
| --- | --- |
| Page ground | `#ffffff` (the cream `#f6f3e8` remains as the legacy panel token) |
| Kerala green (ink) | `#174b32` |
| Light panel text | `#cfdaa8` · lime accent `#b9d66a` |
| Gold rules | `#c7a45a` / `#e0bd6a` |
| Display type | **Barlow Condensed** 600/800 — `clamp()`ed up to ~130–178px, `-0.035em` tracking |
| Body type | **DM Sans** 400–600 |
| Corners | `--radius: 0px` — everything is square except the seals, discs and pill buttons |

Both families are self-hosted from `public/fonts` with `font-display: swap`, so the intro waits on
`document.fonts.ready` before measuring the wordmark.

---

## Assets and credits

**Original generated artwork** — `coconut.png`, `coconut-texture.jpg`, `palm.png` and
`kathakali-palms.png` (the Kathakali-and-palms illustration used on all five can labels and in page
accents). The can itself is an original Three.js model with canvas typesetting.

**Licensed photography** — Kerala houseboat/backwaters, paddy fields, coconuts on a palm, a
traditional Kerala home and a Kathakali performer. Full per-file attribution and licence terms live in
[`IMAGE-CREDITS.md`](IMAGE-CREDITS.md); the same credits are surfaced in the site itself via the
footer's **Photography credits** dialog. Several images are licensed **CC BY-SA** (3.0 / 4.0) — keep
the attribution and licence notes intact if you adapt or redistribute them.

---

## Hosting, platform and deployment

This checkout is the Sites-managed **vinext** starter, so it also carries optional Cloudflare
platform scaffolding that the THENGA page does not currently use.

**Included shape**

- Edit site code under `app/`.
- `.openai/hosting.json` declares optional Sites D1 and R2 bindings (both `null` today);
  `vite.config.ts` simulates any declared bindings for local development.
- `db/index.ts` reads the D1 binding from the Worker environment; `db/schema.ts` is intentionally
  empty. `@cloudflare/workers-types` provides Worker types and `cloudflare-env.d.ts` declares the
  optional `DB`/`BUCKET` bindings.
- `examples/d1/` contains an opt-in D1 example surface; `drizzle.config.ts` supports local migration
  generation.
- `vercel.json` is present for a plain Next.js build path (`next build`).

**Execution profiles**

The Sites initializer copies the shared starter and selects `managed-linux` only when
`SITES_MANAGED_LINUX_CONTAINER=1`; otherwise it selects `portable`. The choice is stored only in the
ignored `.sites-runtime/execution-profile.json` — it never changes tracked source and never requires
reinstalling valid dependencies (restart an existing preview to use a new selection). Do not commit
`.sites-runtime/`.

- **Portable** — preserves host HOME, npm cache, registry, proxy, temporary paths, retry/concurrency
  settings and lifecycle-script policy; installs use `--prefer-offline --no-audit --no-fund`.
  `pnpm dev` keeps previews on loopback.
- **Managed Linux** — uses the project-local HOME/cache/tmp setup, an install lock, tarball preflight
  and timeouts; the image-seeded npm cache is restored only when its lockfile hash matches. Browser QA
  runs through `sites-preview start`, which accepts `--host 0.0.0.0 --port 4173 --strictPort`.

`scripts/sites-env.mjs` preserves the caller's HOME, npm cache, proxy, XDG and temp configuration
while defaulting Wrangler/Miniflare state to the checkout. Local previews use Miniflare's placeholder
`Request.cf` metadata; set `CLOUDFLARE_CF_FETCH_ENABLED=true` to opt into real lookups, and
`WRANGLER_SEND_METRICS=true` to opt into tool metrics. Both default to off.

**Optional ChatGPT sign-in (SIWC)**

`app/chatgpt-auth.ts` provides dispatch-owned helpers — `getChatGPTUser()` for optional signed-in UI,
`requireChatGPTUser(returnTo)` for protected server-rendered pages, and
`chatGPTSignInPath()` / `chatGPTSignOutPath()` for links. Sign-in must start as a top-level navigation
(never `fetch`, XHR or a prefetching router link), and protected pages need
`export const dynamic = "force-dynamic"`. Dispatch owns `/signin-with-chatgpt`,
`/signout-with-chatgpt`, `/callback`, the OAuth cookies and identity header injection
(`oai-authenticated-user-id`, `oai-authenticated-user-email`, and optionally a percent-encoded
`oai-authenticated-user-full-name`) — don't implement app routes for those paths. Use the stable
`userId` as the durable key, not email. On the portable profile, loopback development can mock sign-in
at `/signin-with-chatgpt?return_to=/`; mock auth is disabled in managed-linux and excluded from
production builds. **THENGA is a public, anonymous site and does not call these helpers.**

**Local D1 migrations** (only if you add a schema)

```sh
pnpm db:generate
pnpm build   # regenerates dist/server/wrangler.json
node --import ./scripts/sites-env.mjs ./node_modules/wrangler/bin/wrangler.js \
  d1 execute DB --local --config dist/server/wrangler.json --persist-to .wrangler/state \
  --file drizzle/0000_example.sql
```

Apply each pending migration once, in order. Use `.wrangler/state` (not `.wrangler/state/v3`) — this
only updates the local preview database; publishing applies production migrations separately.

---

## Notes and limitations

- Everything on the page is **conceptual**: no verified commercial SKU data, pricing, nutrition panel,
  real customers or checkout provider. There are no fabricated testimonials — the three "ritual" cards
  are brand copy, not quotes.
- The 3D coconut and can are authored approximations built to match the photographic hero, not scanned
  commercial models. The husk colour is calibrated against the supplied reference photo.
- `REFERENCE-NOTES.md` documents the shot-by-shot mapping from the original reference recording to the
  scroll-driven implementation, plus the QA that was run (desktop hero, coconut opening, can reveal,
  the five thumbnails, product dialog, flavour stepping, navigation and a 390px mobile viewport).
- `public/assets/kerala-backwaters.jpg` and `kerala-houseboat.jpg` are byte-identical copies of the
  same Kumarakom houseboat photograph (2200×1100). The page only references the `backwaters` file, so
  `kerala-houseboat.jpg` is spare weight (~768 KB) you can delete if you want a slimmer bundle —
  remember to drop it from `IMAGE-CREDITS.md` at the same time.
- The heaviest assets are `kathakali-palms.png` (~2.9 MB), `palm.png` (~2.2 MB) and `coconut.png`
  (~1.9 MB). `coconut.png` is the hero image and loads with `fetchPriority="high"`; `palm.png` is only
  fetched by the 3D scene; the decorative repeats of the Kathakali art (`#nature`, footer) are
  `loading="lazy"`. Compressing those three PNGs is the single biggest win if you want a lighter page.

---

## Credits

Site concept, motion choreography, 3D packaging, and implementation by
**[sakshamfit](https://github.com/sakshamfit)**.

Photography and generated artwork are credited per-file in [`IMAGE-CREDITS.md`](IMAGE-CREDITS.md) and
in the site footer.

**Made by sakshamfit.**
