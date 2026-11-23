# Launch posts for Backdrop

Media for both: `marketing/promo.mp4` (21 s, 1600×1084, no sound): the six slides of the
site carousel, each painted by the real panel inside 3ds Max. To rebuild it after the
slides change (run in Git Bash from the repository root):

```bash
for i in 0 1 2 3 4 5; do printf "file 'src/assets/demo/dark-0%s.png'\nduration 3\n" $i; done > list.txt
printf "file 'src/assets/demo/dark-05.png'\n" >> list.txt
ffmpeg -y -f concat -safe 0 -i list.txt -vf "scale=1600:-2:flags=lanczos,fps=30,format=yuv420p" -c:v libx264 -crf 18 -movflags +faststart marketing/promo.mp4
rm list.txt
```

Links sit at the end of each post. Both networks tend to show posts with links to fewer
people, so the X thread keeps the first post free of links and puts them in the reply.

---

## X (Twitter)

A post is limited to 280 characters, and any link counts as 23. The list uses plain
hyphens on purpose: X counts a "•" bullet as two characters.

### Post (with promo.mp4)

Published 2026-11-23: https://x.com/demchenko_a/status/2124916383624331384

```text
I made a free panel for 3ds Max that puts client comments right on the viewport.

- the delivered render behind the camera view
- comments from Dropbox or Google Drive as numbered frames on top
- a checklist and DeepL translation

Open source, one Python file.
```

### Reply 1

Published 2026-11-23: https://x.com/demchenko_a/status/2124916524976832898

```text
It follows the scene: activate another setup and its image and comments come up. Tick a comment off when it is done.

Site and download: https://shimodos.github.io/backdrop-site/
Code (MIT): https://github.com/Shimodos/Backdrop

#3dsmax #archviz #python #opensource
```

### Reply 2 (optional, for the curious) — not posted

```text
The frames are painted by a transparent, click-through Qt window kept over the camera viewport, so they never get in the way of selecting things.

The same file runs on PySide2 (3ds Max 2024) and PySide6 (2026), and the tests run inside 3ds Max itself, headless.
```

---

## LinkedIn

The first two lines are what LinkedIn shows before "see more", so they carry the hook.

LinkedIn attaches a link preview card as soon as a URL is typed, and a post can carry only
one attachment: add the video first (the media button, then Next) and type the text after
it, so no card appears.

### Post (with promo.mp4)

Published 2026-11-23 (Oleksiy Demchenko, the 3D profile): https://www.linkedin.com/feed/update/urn:li:activity:7530682680636641280/

Not posted on the developer profile (Aleksey Demchenko).

```text
A client marks up a render in Dropbox: "lower", "warmer", "move this closer to the wall". Then I sit in 3ds Max with a browser tab next to it, trying to work out which lamp "this" was. So I wrote a panel that brings the comments to the viewport.

It is called Backdrop. It puts the image you delivered behind the camera viewport and the client's comments on top of it, as numbered frames exactly where they were drawn. It is free and open source.

What it does:

• Shows the delivered render behind the camera view, fitted to the render frame. Top, side and perspective views stay clean.
• Finds the image by the name of the render output, so activating another setup in Pulze Scene Manager swaps the picture and its comments.
• Draws every comment as a frame with a numbered pin. Pick one in the list and it lights up with its text.
• Works as a checklist: tick a comment off and its frame goes grey; a badge on each preview counts what is left.
• Reads comments from the file Dropbox saves with "Download comments", or fetches them from Google Drive by the link of the folder.
• Translates the comments with DeepL and your own API key; the original stays under the translation.
• Dark and light themes: it picks the one that matches your 3ds Max.

A few things I learned on the way. The background image of a viewport belongs to the active viewport only, so to show it in another one the panel makes that view active for a moment. Text drawn with the viewport's own drawing calls has one fixed font, so the frames are painted by a transparent, click-through Qt window kept over the camera view. And Google Drive has no "download comments" at all: its API gives them, with the place on the image stored in a field that is not documented, which I had to read from real data.

The tests run inside 3ds Max itself, without a window, in 3ds Max 2024 and 2026. The screenshots on the site and the video in this post are painted by the panel the same way, not captured from the screen. The renders in them are my own work; the comments are made up.

One Python file, no plugins, no installer beyond dragging an .mzp into the viewport. MIT license.

Download and site: https://shimodos.github.io/backdrop-site/
Code: https://github.com/Shimodos/Backdrop

#3dsmax #archviz #python #opensource #cgi
```

---

## Checklist before posting

- The site must be live first: both posts link to it.
- Watch `promo.mp4` once with your own eyes; its slides were checked as images, the clip
  itself was not played.
- The video has no audio track. Both networks accept that.
- The third slide shows a Russian translation: fine for the feature, but decide whether
  you want Cyrillic in an English post.
- After posting, paste the link next to the heading here, as in the Layer Manager file.
