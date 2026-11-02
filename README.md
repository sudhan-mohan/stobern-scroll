# Stöbern Homöopathie — Scroll Story Site

Cinematic, scroll-driven website for **Stöbern Homöopathie** (Dr. A. Thamarai Selvi, B.H.M.S., Regd 4141), Nehru Nagar, Kalapatti Road, Coimbatore.

## Stack
- Static `index.html`, no build step
- **GSAP 3 + ScrollTrigger**: pinned scroll story, horizontal journey, reveals
- **Lenis**: smooth scrolling
- **MorphSVG**: stage icon morphs leaf → drop → globule → bottle → spoon beside the progress rail
- **MotionPath + DrawSVG**: a gold thread draws down the page margins and a globule travels along it through waypoints to the booking button (desktop only)
- **Draggable**: infinite, auto-scrolling "Your journey" card slider (drag, arrows, pauses on hover, speeds up with scroll)
- Fonts: Cormorant Garamond, Inter, Noto Sans Tamil

## The scroll story
A canvas pinned to the screen plays the "how a remedy is made" film as you scroll:

1. From nature: calendula flower
2. Drop by drop: tincture into a vial
3. Absorbed with care: globules soak up the remedy
4. Sealed for purity: amber bottle corked
5. Made for you: globules poured onto a spoon

The film (10 s, 1080p, built from the 5 keyframes with dissolves between stages) is cut into WebP frames:
- `images/seq/` — 239 frames at 1280 px for desktop (~4.5 MB)
- `images/seq-m/` — 159 frames at 854 px for phones (~1.8 MB)

The canvas draws the frame that matches the scroll position. In `index.html`:
- `STAGE_AT` sets where each stage sits in the film (captions, rail and morph icon follow it)
- `FOCUS` pans the frame on portrait screens so the bottle stays in view

To replace the film: export new frames with
`ffmpeg -i film.mp4 -an -vf "scale=1280:-2" -c:v libwebp -quality 72 images/seq/%04d.webp`
(and `fps=16,scale=854:-2` for `seq-m`), then update the two counts in `SEQUENCE`.

The keyframes in `images/stage*.jpg` remain as the no-JavaScript / reduced-motion fallback.

## Images
- `images/stage*.jpg`: storyboard keyframes (AI-generated in Figma, full resolution).
- `images/step*.jpg`, `images/clinic.jpg`: AI-generated stand-ins; replace with real photos of the doctor and clinic before launch.
- `images/logo-white.png`, `images/logo-green.png`: client wordmark.

## Deploy
Connected to Vercel. Every push to `main` deploys automatically.
