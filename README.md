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

**Right now** it cross-fades the 5 keyframes in `images/stage*.jpg` with a slow push-in.

**To switch to real video playback:**
1. Make one continuous 10–15 s clip from the keyframes (Kling / Runway / Veo).
2. Export ~150 frames at 1920×1080 as WebP: `ffmpeg -i film.mp4 -vf "fps=12,scale=1920:-1" -c:v libwebp -quality 70 images/seq/%04d.webp`
3. In `index.html`, set `SEQUENCE.count` to the number of frames.

## Images
- `images/stage*.jpg`: storyboard keyframes (AI-generated in Figma, full resolution).
- `images/step*.jpg`, `images/clinic.jpg`: AI-generated stand-ins; replace with real photos of the doctor and clinic before launch.
- `images/logo-white.png`, `images/logo-green.png`: client wordmark.

## Deploy
Connected to Vercel. Every push to `main` deploys automatically.
