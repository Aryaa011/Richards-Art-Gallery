# Richard's Art Gallery — Immersive 3D Web Experience

A first-person 3D museum experience built with Three.js. Walk through Richard's personal art gallery, discover pencil artworks, and read descriptions


## Repo Structure

```
├── index.html                              ← Main experience (~36KB)
└── richards_art_gallery_-_audio_tour.glb  ← 3D model (37MB, tracked by Git LFS)
```

The GLB file must be in the **same folder** as `index.html`.

---

## Git LFS Setup (required for the GLB)

```bash
git lfs install
git lfs track "*.glb"
git add .gitattributes
git add index.html richards_art_gallery_-_audio_tour.glb
git commit -m "Add Richard's Art Gallery"
git push
```

---

## Running Locally

```bash
# Option 1 - Node
npx serve .

# Option 2 - Python
python -m http.server 8080

# Option 3 - VS Code
Install "Live Server" → right-click index.html → Open with Live Server
```

Then open `http://localhost:3000`

> ⚠️ Opening `index.html` directly as `file:///` won't work — browsers block local file loading. You need a server.

---

## Deploy to GitHub Pages

1. Push repo with Git LFS (see above)
2. Go to repo **Settings → Pages**
3. Source: **Deploy from branch → main → / (root)**
4. Visit `https://yourusername.github.io/repo-name`

---

## Controls

### Desktop

| Input | Action |
|-------|--------|
| `W A S D` | Move |
| Mouse drag | Look around (pointer lock) |
| `E` or Click | Inspect artwork |
| `ESC` | Release cursor / close panel |
| Mute button | Toggle ambient audio |

### Mobile

| Input | Action |
|-------|--------|
| Left joystick | Walk |
| Right-half drag | Look |
| Tap near artwork | Inspect |

---

## Artworks in the Gallery

| Title | Subject |
|-------|---------|
| Loveknot — Shetland Pony | Pencil drawing of a Shetland Pony |
| Jag — Dog Portrait | Dark dog portrait in graphite |
| Shore Scene | Rowing boat on a grey shore |
| End Frame | Ornate frame, Lockett Portraits pug |
| Squirrel | Red squirrel on dark bark |
| Propinquity | Extreme close-up human face |
| The London Eye | London Eye at night, Thames reflection |
| Pug — Two Short Planks | Pug portrait, silver frame |
| Guinea Pig | Fluffy guinea pig, wooden frame |
| Pomeranian–Border Terrier | Scruffy small dog portrait |
| Seal | Close-up seal face in graphite |
| Jaguar E-Type Series 2 | Classic car pencil drawing |
| Scarlett | Woman portrait in pencil |
| Simon and Jake | Portrait of Simon |
| Dream Catcher | Ceiling hanging installation |
| Aston Martin | Aston Martin pencil drawing |

---

## Features

- First-person WASD navigation, eye height locked at 1.65m
- Raycaster artwork detection — crosshair must point at painting
- Info panel with typewriter word-by-word reveal
- Artwork discovery counter
- Ambient audio (Web Audio API — no audio files): pad, piano, wind, birds, footsteps
- Mobile responsive: virtual joystick, touch look, panel slides from bottom
- Breakpoints at 768px and 480px

---

## Technical Notes

- **Engine:** Three.js r128 + GLTFLoader + DRACOLoader (all CDN)
- **Audio:** Fully synthesised via Web Audio API — zero audio files
- **Mesh detection:** Uses exact Three.js underscore-normalised mesh names in a lookup table
- **Camera start:** Entrance door position, facing inward — matches original Sketchfab preview

---

## Credits

| | |
|--|--|
| 3D Model | Richard's Art Gallery by shinymagic — CC-BY-4.0 |
| Engine | Three.js r128 |
| Fonts | Cormorant Garamond + Josefin Sans (Google Fonts) |

## License

Code: MIT  
3D Model: CC-BY-4.0 — credit shinymagic / Sketchfab when sharing
