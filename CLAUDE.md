# CLAUDE.md — Frontend Website Rules

## Always Do First

- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.
- **Immediately read and deeply understand the PRD.md file** in the project root.
  Every single piece of code, structure, content, colors, sections, features, animations, dark mode, CTAs, forms, branching logic (main page → law firms / home services pages), and design decisions **must** come directly from the PRD.md.
  Do NOT invent, assume, or add anything that contradicts or is missing from the PRD.
  If something is unclear in the PRD, ask the user for clarification before proceeding — never guess.

## Reference Images

- If a reference image is provided: match layout, spacing, typography, and color exactly. Swap in placeholder content (images via `https://placehold.co/`, generic copy). Do not improve or add to the design.
- If no reference image: design from scratch **but strictly within the constraints and style described in PRD.md** (Seattle/Seahawks-inspired colors, modern simplistic vibe, subtle animations, etc.).
- Screenshot your output, compare against reference (or PRD expectations), fix mismatches, re-screenshot. Do at least 2 comparison rounds. Stop only when no visible differences remain or user says so.

## Output Defaults

- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images: `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Logo

- The project logo is at `LOGO/Gemini_Generated_Image_jc95v2jc95v2jc95.png`
- **Always use this file** for the logo — never use a placeholder, text substitute, or inline SVG in its place.
- Reference it in HTML as: `<img src="LOGO/Gemini_Generated_Image_jc95v2jc95v2jc95.png" alt="Logo" />`

## Anti-Generic Guardrails

- **Colors:** Never use default Tailwind palette (indigo-500, blue-600, etc.). Use **only** the exact hex colors defined in PRD.md:Primary: #002244 (College Navy)Secondary/Accents/CTAs: #69BE28 (Action Green)Neutral: #A5ACAF (Wolf Gray)Light mode background: #FFFFFFDark mode: dark navy base with green highlights
- **Shadows:** Never use flat `shadow-md`. Use layered, color-tinted shadows with low opacity.
- **Typography:** Never use the same font for headings and body. Pair a display/serif with a clean sans. Apply tight tracking (`-0.03em`) on large headings, generous line-height (`1.7`) on body.Prefer: Inter Bold for headings, Roboto Regular for body (as noted in PRD.md).
- **Gradients:** Layer multiple radial gradients. Add grain/texture via SVG noise filter for depth (if it fits the energetic Seahawks-inspired glow).
- **Animations:** Only animate `transform` and `opacity`. Never `transition-all`. Use spring-style easing.Apply subtle fades/transitions on scroll section appearance and button hovers (green glow/shift) as described in PRD.md.
- **Interactive states:** Every clickable element needs hover, focus-visible, and active states. No exceptions.
- **Images:** Add a gradient overlay (`bg-gradient-to-t from-black/60`) and a color treatment layer with `mix-blend-multiply` where appropriate (especially for hero/demo visuals).
- **Spacing:** Use intentional, consistent spacing tokens — not random Tailwind steps.
- **Depth:** Surfaces should have a layering system (base → elevated → floating), not all sit at the same z-plane.

## Local Server

- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow

- Puppeteer is installed at `/Users/champ/Documents/Projects/Agents425/Landing page/node_modules/puppeteer/`. Chrome cache is at `/Users/champ/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool — Claude can see and analyze the image directly.
- When comparing, be specific: "heading is 32px but reference shows ~24px", "card gap is 16px but should be 24px"
- Check: spacing/padding, font size/weight/line-height, colors (exact hex), alignment, border-radius, shadows, image sizing

## Hard Rules

- Do not use `transition-all`
- Do not use default Tailwind blue/indigo as primary color
- Do not deviate from the structure, sections, or branding defined in **PRD.md**
- Dark/light mode toggle **must** be present in top-right corner on all pages (persist via localStorage)
- Include Calendly embed/link and email capture forms exactly where specified in PRD.md
- Respect the branched page flow: main entry page → dedicated law firms or home services pages
- Do not "improve" a reference design - match it
