
# Richard's Art Gallery — Immersive 3D Web Experience

A single-file, fully self-contained first-person 3D museum experience. Walk through Richard's personal art gallery, discover pencil artworks, and read descriptions — all from one HTML file with zero setup, no server, no install.

---

## Quick Start

1. Download `richards-gallery-final.html`
2. Double-click to open in Chrome or Firefox
3. Click **Enter Museum**
4. Wait ~10–15 seconds for the 3D model to decode
5. Click the canvas to lock your cursor and start exploring

No server needed. No folder structure. One file.

---

## Controls

### Desktop

| Input | Action |
|-------|--------|
| `W A S D` | Move forward / left / backward / right |
| Arrow keys | Same as WASD |
| Mouse drag | Look around (requires pointer lock) |
| `E` | Inspect artwork you are looking at |
| Click on painting | Inspect it |
| `ESC` | Release cursor / close panel |
| Mute button | Toggle ambient audio |

### Mobile

| Input | Action |
|-------|--------|
| Left joystick (bottom-left) | Walk |
| Right-half screen drag | Look around |
| Tap near an artwork | Inspect it |

---

## Features

### Navigation
- First-person WASD movement at natural walking speed
- Mouse look with pointer lock
- Eye height locked at 1.65m — realistic gallery perspective
- Camera starts at the gallery entrance facing inward
- Mobile virtual joystick and right-half touch drag

### Artwork Detection
- Raycaster-based — crosshair must point directly at a painting
- Works by click or E key
- 16 artworks tagged by exact Three.js mesh name
- No false positives from proximity guessing

### Info Panel
- Slides from right on desktop, rises from bottom on mobile
- Typewriter word-by-word reveal
- Title, medium, location shown
- Audio ducks while panel is open

### Discovery Counter
- HUD shows artworks discovered out of total

### Ambient Audio (Web Audio API — zero audio files)
- Layered pad — sine oscillators with convolution reverb and LFO tremolo
- Piano — random pentatonic notes every 3–10 seconds
- Wind — bandpass-filtered noise with breathing LFO
- Birds — synthesised chirp bursts every 8–28 seconds
- Footsteps — wooden click on every step, silent when still

### Mobile Responsive
- Breakpoints at 768px and 480px
- Entry screen, panel, HUD all scale for small screens
- user-scalable=no prevents accidental pinch-zoom

---

## Artworks in the Gallery

| Title | Subject |
|-------|---------|
| Loveknot — Shetland Pony | Pencil drawing of a Shetland Pony |
| Jag — Dog Portrait | Dark dog portrait in deep graphite |
| Shore Scene | Rowing boat on a grey shore |
| End Frame | Ornate frame, Lockett Portraits composition |
| Squirrel | Red squirrel on dark bark |
| Propinquity | Extreme close-up human face |
| The London Eye | The London Eye at night, Thames reflection |
| Pug — Two Short Planks | Pug portrait, silver frame |
| Guinea Pig | Fluffy guinea pig, warm wooden frame |
| Pomeranian-Border Terrier | Small scruffy dog portrait |
| Seal | Close-up seal face in graphite |
| Jaguar E-Type Series 2 | Classic car pencil drawing |
| Scarlett | Woman portrait in pencil |
| Simon and Jake | Portrait of Simon |
| Dream Catcher | Ceiling hanging installation |
| Aston Martin | Aston Martin pencil drawing |

---

## Technical Notes

### Why base64-embedded?
Browsers block fetch() from file:/// origins. Embedding the GLB as a base64 data URI means GLTFLoader.load(dataUrl) works without any server.

### Coordinate system
The GLB root matrix applies scale 1/827 and a 90deg X-axis rotation. All positions in code are in post-transform world space in metres.

### Mesh name normalisation
Three.js converts spaces and special characters to underscores at load time. The MESH_TO_KEY lookup uses these normalised names, confirmed via runtime console dump.

### Script load order
1. Three.js CDN script
2. GLB_DATA declaration (base64 string)
3. Logic script — uses waitForThree() to poll until THREE is defined before running

---

## Browser Support

| Browser | Status |
|---------|--------|
| Chrome 100+ | Recommended |
| Firefox 100+ | Works |
| Edge 100+ | Works |
| Mobile Chrome | Works with joystick |
| Mobile Firefox | Works with joystick |
| Safari | May have pointer lock limitations |

---

## Local Server (optional)

```bash
npx serve .
# or
python -m http.server 8080
```

---

## Credits

- 3D Model: Richard's Art Gallery – Audio Tour by shinymagic — CC-BY-4.0
- 3D Engine: Three.js r128
- Fonts: Cormorant Garamond + Josefin Sans via Google Fonts

## License

Code: MIT
3D Model: CC-BY-4.0 — credit shinymagic / Sketchfab when sharing
