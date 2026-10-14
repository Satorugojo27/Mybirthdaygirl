# For Parthona

An interactive birthday film for Parthona's 19th. Plain HTML, CSS and JavaScript. No build step, no frameworks, no installs.

**The journey:** a cake with 19 candles to blow out, a letter hidden inside, a realistic night sky with her star, five photo moments, 19 notes, a 19th-year celebration, a promise to seal, and a heart of 19 stars with her photo.

## 1. Try it on your computer

Open a terminal in this folder and run one of these, then visit the address it prints:

```bash
npx serve .            # Node
# or
python3 -m http.server 8080   # Python, then open http://localhost:8080
```

Opening `index.html` by double-click shows everything except the YouTube song. YouTube refuses to play inside pages opened from `file://`. Use a local server, or GitHub Pages as below.

## 2. Put it online with GitHub Pages (free)

1. Create a GitHub account, then a **new repository** (e.g. `for-parthona`). Choose **Public** (free Pages needs public; use a private-looking name, the page already has `noindex`).
2. Upload everything in this folder to the repository root (`index.html` must sit at the top level):
   ```bash
   git init
   git add .
   git commit -m "Birthday universe"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/for-parthona.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`, **Save**.
4. After about a minute your site is live at `https://YOUR-USERNAME.github.io/for-parthona/`.
5. Send her that link and tell her to **open it in Chrome or Safari, volume up, headphones on**.

*Alternative:* in Settings → Pages choose **Source: GitHub Actions**; the included `.github/workflows/pages.yml` deploys on every push.

Every path in the project is relative, so it works in a sub-folder such as `/for-parthona/`.

## 3. The photos

All five are already in `assets/photos/`, resized for fast phone loading. Her photos are cropped only (black bars and the video-call inset were removed), never edited.

| File | Original upload | Moment |
|---|---|---|
| `photo-1.jpg` | `1000156373.jpg` (blue saree) | Opening moment, iris of light. Also inside the final heart |
| `photo-2.jpg` | `1000161071.jpg` (garden path) | Frame drawn in starlight |
| `photo-3.jpg` | `1000161365.jpg` (grass, coral saree) | Floats down |
| `photo-4.jpg` | `1000156384.jpg` (rooftop, pink saree) | Curtain of light parts |
| `photo-5.jpg` | `1000170163.jpg` (laughing) | Rises into focus with a sweep of light |

To swap one, replace the file with the same name (portrait 4:5 looks best), or edit the `photos` list in `js/config.js` (path, alt text, crop focus `pos`, reveal style). If a file is missing, a soft placeholder shows the exact path to add.

## 4. The music (Perfect, Ed Sheeran)

- **Default:** the official video on Ed Sheeran's YouTube channel, through YouTube's own embedded player. Nothing is copied or hosted by you.
- It starts only after her first tap (blowing a candle). Controls (top right): **play/pause**, **mute**, and **♪** which opens the player card with an **Open on YouTube** fallback link.
- If a phone blocks scripted playback, a gentle hint appears and the player card opens so she can tap the real play button.
- YouTube asks that its player stays visible to users; the card is a compact one you can open any time with ♪.
- **Your own licensed file instead:** put it at `assets/audio/perfect.mp3` and set `audioFile: "assets/audio/perfect.mp3"` in `js/config.js`. It is then played with a normal audio element and falls back to YouTube if it can't load. Only add audio you have the right to use.
- To change the song, change `youtubeId` and `youtubeUrl` in `js/config.js`.

## 5. Make it yours

| What | Where |
|---|---|
| Every word (letter, captions, 19 notes, promise, ending) | `js/content.js` |
| Names, song, photo list, final-heart photo | `js/config.js` |
| Colours, fonts, animation timing | top of `css/style.css` |
| Photos | `assets/photos/` |

Fonts (Cormorant Garamond, Jost, Pinyon Script) load from Google Fonts with elegant fallbacks if offline. To self-host, download them and add `@font-face` rules to `css/style.css`.

## 6. How it's built

- `js/cosmos.js` draws the sky on a canvas: procedural nebula, 300-800 parallax stars with a Milky Way band, her pink-gold star with diffraction spikes and drifting gold dust, rare shooting stars, and the 19-star heart.
- `js/cake.js` draws the cake in SVG with 19 tappable candles; the cake splits in two to reveal the letter.
- `js/music.js` handles YouTube / audio file, `js/main.js` runs the scenes, navigation, notes, promise and finale.
- No Three.js on purpose: Canvas 2D keeps it light and dependency-free for phones and GitHub Pages. If canvas isn't available the page falls back to a CSS night-sky gradient.

**Mobile and access:** touch and keyboard friendly (large tap targets, arrow keys, swipe left/right on message and photo pages), respects `prefers-reduced-motion` (static sky, simple fades), labelled controls, safe-area support for iPhone notches, and graceful fallbacks for missing photos, blocked audio and no canvas.

## 7. Troubleshooting

- **No sound:** tap the ♪ button, then the play button in the card. Check the phone isn't on silent (iPhone) and the volume is up.
- **YouTube says video unavailable:** use **Open on YouTube**, or supply a licensed file (section 4).
- **Old version showing after an update:** hard refresh (Ctrl/Cmd+Shift+R) or wait a minute for Pages to rebuild.
- **Replay:** at the end, the *Watch it again* button resets everything.

Made with love, by Trishul.
