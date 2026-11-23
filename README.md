# backdrop-site

Landing page for [Backdrop](https://github.com/Shimodos/Backdrop), a panel for Autodesk
3ds Max that puts the delivered render behind the viewport and the client's comments on
top of it. Astro + Tailwind CSS, deployed to GitHub Pages:
https://shimodos.github.io/backdrop-site/

```
npm install
npm run dev        # http://localhost:4321/backdrop-site/
npm run build      # static site in dist/
```

Pushing to `main` builds and deploys the site (`.github/workflows/deploy.yml`).
One-time setup in the repository: Settings → Pages → Source: "GitHub Actions".

## Screenshots and the carousel

Nothing here is drawn by hand. The images in `src/assets/shots`, the slides in
`src/assets/demo`, `public/sources.gif` and `public/icon-256.png` are rendered from the
real panel inside 3ds Max by `tools/make_shots.ps1` in the Backdrop repository. To refresh
them after a change in the panel:

```powershell
pwsh ..\Backdrop\tools\make_shots.ps1
Copy-Item ..\Backdrop\docs\shots\panel-*.png, ..\Backdrop\docs\shots\viewport.png, ..\Backdrop\docs\shots\drive-menu.png src\assets\shots
Copy-Item ..\Backdrop\docs\shots\demo\* src\assets\demo
Copy-Item ..\Backdrop\docs\shots\sources.gif, ..\Backdrop\docs\icon-256.png public
ffmpeg -y -i src\assets\demo\dark-01.png -vf "scale=-2:590,pad=1200:630:(ow-iw)/2:(oh-ih)/2:color=0x15171b" public\og.png
```

`src/assets/demo/demo.json` lists the slides of the hero carousel and their captions
(`src/components/Demo.astro`). The slides sit in a ring: the current one in front, its
neighbours peeking out behind it. The ring turns every 3.4 s while it is on screen (the
active dot fills up as a timer), pauses under the mouse, can be dragged left / right with
the mouse or a finger, and a side slide comes forward when clicked. For visitors who prefer
reduced motion only the front slide is shown and slides cross-fade in place.

The renders in the screenshots are the author's own work; the comments on them are made up.
