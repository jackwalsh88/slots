# Odyssey: Voyage of Fortune — Engine Art Asset Manifest (5x3 Expanding Wild Edition) — v2

**Platform:** Engine (`stake-engine.com` — Svelte 5 + PixiJS 8 Web SDK / Python Math SDK)  
**Template & Mechanic:** `lines` Template (5 Reels × 3 Rows, 20 Paylines) + **Expanded Full-Reel Wild (`1:3`) with Dynamic Multipliers (`2×` to `100×`)**  
**Math Profile:** Stateless (No Progressive Jackpots), 10,000× Max Win, Stake.us Social-Mode Compliant  
**Master Color Palette:** Burnished Gold, Glowing Cyan, Molten Amber/Crimson, Deep Aegean Navy  
**Source of platform rules:** Engine docs (`/docs/approval-guidelines/*`, `/docs/front-end/*`), read 2026-11-03. See Section 7 for the full change log. **v3: every asset is generated from scratch with the moodboard; no earlier images are used.**

---

## 0. Generation Order *(v3)*
All prompts run with your moodboard enabled as the default personalisation, so they carry no `--profile` flag. Generate in this order, so the first results lock the character and the style for everything after them:
1. **Character anchor:** `hero_bigwin_popup.png`. It fixes how Odysseus looks.
2. **Style anchors:** `wild_base_1x1.png` and `H1.png`. They fix the symbol frame, metals, and glow.
3. **Wild suite:** the banners, crest, plaques, and sticky frame.
4. **Remaining symbols:** `SCATTER`, `H2`–`H4`, `L1`–`L4`.
5. **Backgrounds**, then the **reel frame, logo, and UI**, then the **tile assets**.

Once steps 1 and 2 are approved, add those images to the moodboard so every later prompt inherits their look.

**Odysseus character sheet (locked from the approved `hero_bigwin_popup`)**: ornate gold Corinthian helmet worn down, with cheek guards and nose guard, eyes visible through the openings; tall crimson horsehair crest; full grey-and-white beard; weathered, stern face; ornate gold cuirass with swirling relief; crimson cloak over one shoulder; golden recurve bow slung behind the shoulder; warm skin with cyan rim light on the armour edges. Every prompt that shows Odysseus uses this wording.

---

## 1. The Expanded Full-Reel Wild (`1:3`) Asset Suite
When a player lands the `1×1` Bow Wild on a reel, it triggers the **"Odysseus’s Arrow"** animation: the bow fires a cyan lightning beam upward and expands vertically to cover all **3 rows of that reel (`1:3` ratio)**, revealing a random multiplier (`2×` to `100×`). In the Free Spins Cave Bonus, Expanded Wilds lock in place (**Sticky Wilds**).

To make this work dynamically in PixiJS 8 (so the math engine can display *any* multiplier number from `2×` to `100×`), the suite is **1 finished base symbol + 5 modular layers**. **The multiplier number and the "WILD" lettering are never baked into the banner art** — they are layered on top (crest + plaque + live text).

| File Name | Aspect Ratio | Target Resolution | Status | Purpose in Engine (PixiJS 8) |
| :--- | :--- | :--- | :--- | :--- |
| `wild_base_1x1.png` | `1:1` | `512 × 512 px` | ✅ **Final** (`assets/wild_base_1x1.webp` + `@2x`; plaque band ≈ x 115–399, y 336–390) | The initial 1-cell Bow of Odysseus symbol that lands on the reel before expanding. Carries the `"WILD"` plaque scaled to 50% (256 × 128) in its bottom quarter. |
| `wild_expanded_hero_1x3.png` | `1:3` | `512 × 1536 px` | ⛔ **Dropped** | Option A (Odysseus figure). Not used: Option B continues the 1×1 bow directly and reads better at reel size. |
| `wild_expanded_beam_1x3.png` | `3:8` canvas | `576 × 1536 px` (+ `@2x` 1152 × 3072) | ✅ **Final** (`assets/wild_expanded_beam_1x3.webp`) | **The expanded wild.** Canvas is 32 px wider on each side than the 512 px reel so the wings and corner brackets can overhang; anchor at the center (x = 288). Socket center x 295, y 172 (inner Ø 120, outer Ø 168). Plaque band x 125–458, y 1322–1393. |
| `wild_text_plaque.png` | `4:1` | `512 × 128 px` (+ `@2x` 1024 × 256) | ✅ **Final** (`assets/wild_text_plaque.webp`) | Raised badge over the plaque band. **Banner:** 370 px wide, centered at x 291, y 1357. **1 × 1:** 320 px wide, centered at x 257, y 363. |
| `wild_mult_crest_blank.png` | `1:1` | `256 × 256 px` (+ `@2x` 512) | ✅ **Final** (`assets/wild_mult_crest_blank.webp`) | Placed over the banner socket (center x 295, y 172) at **180 px** wide; empty plate ≈ 113 px. Multiplier text ≈ 44 px bold, gold fill, dark stroke. At Popout S the label is unreadable, so scale the crest ×1.5 when the viewport is below 800 px wide. |
| `wild_sticky_frame_1x3.png` | `3:8` canvas | `576 × 1536 px` (+ `@2x`) | ✅ **Final** (`assets/wild_sticky_frame_1x3.webp`) | Chains + padlocks overlay, transparent center (lightning kept), deskewed and fitted over the banner border (outer x 45–531, y 62–1474). **Layer order:** banner → sticky frame → crest → plaque. |

> **Text note:** Midjourney renders lettering unreliably. If the `"WILD"` letters on the plaque come out warped, generate the plaque blank and set the word with a **locally bundled** font (see Section 6), or retouch the letters.

### Midjourney v8 Production Prompts for the `1:3` Expanded Wild Suite *(v2.1)*

**Shared settings**
* Your moodboard is the default personalisation, so no `--profile` flag is needed.
* `--s 150`: a starting point. Raise it toward 250 if the moodboard look is too weak; lower it toward 75 if Midjourney drifts from the prompt.
* **Layout grid for 512 × 1536:** the crest (256 × 256) sits in the **top sixth**, the plaque (512 × 256) sits in the **bottom sixth**, and the subject fills the **middle two-thirds**. The prompts below state this grid explicitly.
* **Layout for the 1 × 1 base symbol:** the bow fills the top three-quarters, and the bottom quarter is an empty band for the 50%-scaled plaque.
* Pick one seed that works for Option A or B and reuse it (`--seed`) across re-rolls to keep frames consistent.

* **`wild_base_1x1.png` (Bow Wild — 1 × 1 base symbol)**
  > `3D slot machine symbol icon, the legendary golden recurve bow of Odysseus with a nocked crackling cyan lightning arrow pointing straight up, the bow fills the top three-quarters, framed inside an ornate square hammered-gold and dark-bronze Greek key border, an empty smooth bronze plaque band across the bottom quarter, burnished gold and glowing cyan palette, dramatic rim light, glossy ray-traced 3D render, premium casino slot game asset, the whole symbol small enough to leave empty black space on all four sides, lightning kept inside the frame, no loose particles, no embers, no smoke, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges`

* **`wild_expanded_hero_1x3.png` (Option A — Odysseus Hero Banner)**
  > `Tall vertical full-reel slot machine banner, the Greek hero Odysseus in an ornate gold Corinthian helmet with cheek guards and a tall crimson horsehair crest, full grey-and-white beard, ornate gold cuirass with swirling relief, crimson cloak over one shoulder, full figure, drawing a massive glowing golden recurve bow with a crackling cyan lightning arrow aimed straight up, figure fills the middle two-thirds, framed by a tall rectangular dark-bronze Greek key meander border with raised gold corner brackets around a deep navy-blue inner panel, the same frame design as the 1x1 Bow Wild symbol, an empty dark circular medallion socket centered in the top sixth, an empty smooth bronze plaque band across the bottom sixth, burnished gold and glowing cyan palette, dramatic rim light, glossy ray-traced 3D render, premium casino slot game asset, the whole frame inside the canvas with black space on all sides, no loose particles, no embers, no smoke, perfectly front-facing, flat solid black background --ar 1:3 --s 150 --chaos 5 --no text, letters, numbers, logo, cropped edges, watermark`

* **`wild_expanded_beam_1x3.png` (Option B — Bow & Lightning Beam Banner)**
  > `Tall vertical full-reel slot machine banner, the legendary winged golden recurve bow of Odysseus with sweeping ornate limbs, mounted at the base of the frame, firing a blazing column of cyan lightning straight up through the center, branching electric arcs, beam fills the middle two-thirds, framed by a tall rectangular dark-bronze Greek key meander border with raised gold corner brackets around a deep navy-blue inner panel, the same frame design as the 1x1 Bow Wild symbol, an empty dark circular medallion socket centered in the top sixth, an empty smooth bronze plaque band across the bottom sixth, burnished gold and glowing cyan enamel, glossy ray-traced 3D render, premium casino slot game asset, the whole frame inside the canvas with black space on all sides, no loose particles, no embers, no smoke, perfectly front-facing, flat solid black background --ar 1:3 --s 150 --chaos 5 --no text, letters, numbers, logo, cropped edges, watermark, people`

* **`wild_text_plaque.png` (WILD Plaque — lettered version)**
  > `Long narrow horizontal 3D game UI plaque, four times wider than tall, bearing the single word "WILD" in thick embossed ancient Greek gold capital letters, dark hammered-bronze plate with glowing cyan enamel inlay and a fine Greek key trim, perfectly front-facing, symmetrical, centered, generous black margin on every side, dramatic golden rim light, glossy ray-traced render, casino slot game asset, flat solid black background --ar 4:1 --s 100 --chaos 5`

* **`wild_text_plaque.png` (fallback — blank version)** *(use if the letters warp; set "WILD" in a bundled font, or retouch)*
  > `Long narrow horizontal 3D game UI plaque, four times wider than tall,, dark hammered-bronze plate with glowing cyan enamel inlay and a fine Greek key trim, smooth empty center panel, perfectly front-facing, symmetrical, centered, generous black margin on every side, dramatic golden rim light, glossy ray-traced render, casino slot game asset, flat solid black background --ar 4:1 --s 100 --chaos 5 --no text, letters, numbers`

* **`wild_mult_crest_blank.png` (Multiplier Crest)**
  > `Perfectly front-facing circular 3D game UI medallion, a thick polished dark-bronze rim with a fine Greek key meander band and four small gold studs at the compass points, a thin glowing cyan inner ring, a smooth flat dark navy-black enamel center plate filling about seventy percent of the diameter, completely empty center, zero perspective, perfect circle, symmetrical, centered with black margin around it, warm gold key light with cyan rim light only on the edge, no loose particles, glossy ray-traced render, premium casino slot game asset, flat solid black background --ar 1:1 --s 100 --chaos 5 --no text, letters, numbers, engraving in center, cropped edges`

* **`wild_sticky_frame_1x3.png` (Sticky Wild Lock Frame)**
  > `Tall vertical rectangular 3D game UI border frame, heavy glowing golden chains running along all four edges and crossing at the corners with bronze padlocks, crackling cyan lightning crawling along the chains, thin border about one-twelfth of the frame width, the entire center is completely empty flat black, perfectly front-facing, symmetrical, casino slot game overlay asset, flat solid black background --ar 1:3 --s 150 --no text, letters, numbers, figure, objects in center`

**Post-production notes**
* **Glow layers** (the beam, lightning on the sticky frame, cyan sparks): do not cut these out with background removal, which leaves dark halos. Keep them on black and render them in PixiJS with the `add` (additive) blend mode; black then becomes invisible. Separate the solid metal parts onto an alpha PNG layer if needed.
* **Crest:** if the plate shows any tilt, warp it flat before export; the live multiplier text is stamped dead-center.
* **Resize:** downscale Midjourney upscales to the exact target sizes (512 × 1536, 512 × 256, 256 × 256), then apply the 5% padding rule.
* **Alignment test:** stack hero/beam + crest + plaque + sticky frame in one file at 512 × 1536 before export to confirm the socket and plaque band line up.

---

## 2. Special & High-Paying Symbols (`SCATTER`, `H1`–`H4`)
All standard reel symbols are `1:1` square (`512 × 512 px` transparent PNGs; ship as a sprite atlas, see Section 6).

| Symbol ID | Asset Name | Dominant Accent | Status | Notes |
| :--- | :--- | :--- | :--- | :--- |
| `SCATTER.png` | The Trojan Horse (`BONUS`) | Bronze & Molten Gold | ✅ **Final** (`assets/SCATTER.webp` + `@2x`) | Statue on a wheeled cart; `"BONUS"` plaque 240 px wide, centered at x 284, y 382 (over the cart front panel). Add a warm additive radial glow behind it in PixiJS so it reads as the most important symbol. **Never use on the game tile.** |
| `H1.png` | Odysseus Medallion | Gold & Crimson | ✅ **Final** (`assets/H1.webp` + `@2x`) | Style anchor for the symbol set. Keep the helmet crest inside the 5% margin. |
| `H2.png` | Trireme Warship | Navy & Gold | ✅ **Final** (`assets/H2.webp` + `@2x`) | Front-facing gold medallion, navy rim. **Medallion size standard:** ring ≈ 330–360 px wide on the 512 canvas (H1 331 + crest; H2 360), so the medallion symbols read as one family. |
| `H3.png` | The Cyclops Emblem | Amber & Obsidian | ✅ **Final** (`assets/H3.webp` + `@2x`) | Ring ≈ 355 px (medallion standard); eye brightened +35% in post so it stays the brightest point at reel size. |
| `scatter_text_plaque.png` | `"BONUS"` lettering plate | Gold & Bronze | ✅ **Final** (`assets/scatter_text_plaque.webp` + `@2x`, 512 × 128) | Matches the WILD plaque; end spikes trimmed. On `SCATTER.png`: 240 px wide, centered at x 284, y 382. |
| `H4.png` | Island Map & Astrolabe | Glowing Cyan & Brass | ✅ **Final** (`assets/H4.webp` + `@2x`) | Disc ≈ 355 px (medallion standard); cyan elements boosted (+35% saturation, +30% brightness) in post. Reads as copper + cyan at reel size. |

> **Colour-clash watch:** `H1` (gold & crimson) and `L1` (ruby red) are the closest pair at ~50 px. Verify them side by side at the 400×225 Popout S size (Section 6). Adjust `L1` toward a deeper ruby/black-glaze read if they blur together.

### Midjourney Prompts for Special & High Symbols

* **`SCATTER.png` — The Trojan Horse**
  > `3D slot machine symbol icon, the wooden Trojan Horse of legend with bronze armour plates and molten-gold glowing seams, standing on a wheeled bronze platform, compact chunky silhouette filling the top three-quarters, an empty smooth bronze plaque band across the bottom quarter, burnished bronze and molten gold palette with faint cyan rim light, glossy ray-traced 3D render, premium casino slot game asset, the whole symbol small enough to leave empty black space on all four sides, no loose particles, no embers, no smoke, perfectly front-facing, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges`

* **`scatter_text_plaque.png` — "BONUS" Plate** *(same plate as the WILD plaque; generate the blank fallback and set the letters in a bundled font if they warp)*
  > `Long narrow horizontal 3D game UI plaque, four times wider than tall, bearing the single word "BONUS" in thick embossed ancient Greek gold capital letters, dark hammered-bronze plate with glowing cyan enamel inlay and a fine Greek key trim, perfectly front-facing, symmetrical, centered, generous black margin on every side, dramatic golden rim light, glossy ray-traced render, casino slot game asset, flat solid black background --ar 4:1 --s 100 --chaos 5`

* **`H1.png` — Odysseus Medallion**
  > `3D slot machine symbol icon, a circular burnished-gold shield medallion bearing the embossed helmeted profile of the Greek hero Odysseus in an ornate gold Corinthian helmet with cheek guards and a tall crimson horsehair crest, full grey-and-white beard, crimson enamel inlays around the rim, compact badge silhouette, the whole medallion and the full crest inside the frame with empty black space on all four sides, warm gold key light with cyan rim light only on the rim edges, no loose particles, no embers, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges`

* **`H4.png` — Island Map & Astrolabe** *(v3.4: the astrolabe is the medallion, matching the `H1`–`H3` family)*
  > `3D slot machine symbol icon, a perfectly front-facing circular polished brass astrolabe used as a medallion, concentric engraved brass rings with glowing cyan star markers and a cyan-lit pointer arm, a small rolled parchment sea chart of Aegean islands tucked diagonally behind the lower left of the disc, clean bold readable shapes, compact badge silhouette, the whole object inside the frame with empty black space on all four sides, warm brass key light with glowing cyan accents, no loose particles, no sparks, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, tilted disc`

* **`H2.png` — The Trireme Warship** *(v3.4: matched to the approved `H1` medallion)*
  > `3D slot machine symbol icon, a perfectly front-facing circular burnished-gold shield medallion with a polished navy-blue enamel rim inlay and a thin glowing cyan outer edge, inside it an ancient Greek trireme warship in three-quarter view with a golden ram at the bow, rows of oars, and billowing ivory-and-gold sails, cutting through stylised deep navy-blue glossy waves, the ship's mast and sail top may break out above the rim, compact badge silhouette, the whole medallion inside the frame with empty black space on all four sides, warm gold key light with cyan rim light only on the edges, no loose particles, no spray droplets, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, crimson sails`

* **`H3.png` — The Cyclops Medallion** *(v3.4: matched to the `H1`/`H2` medallion family)*
  > `3D slot machine symbol icon, a perfectly front-facing circular medallion with a jagged black obsidian rim bound by heavy golden chains and a thin glowing cyan outer edge, inside it a close-up head-and-shoulders bust of a fierce roaring Cyclops with one large glowing molten-amber eye in the center of the forehead, rough grey-green skin, wild dark hair, head and shoulders only, the bust may break out slightly above the rim, compact badge silhouette, the whole medallion inside the frame with empty black space on all four sides, warm amber key light with cyan rim light only on the edges, no loose particles, no sparks, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, full body, legs, gore, blood`

---

## 3. Low-Paying Symbols (`L1`–`L4` — Color-Coded for `400×225` Popout S)
Engine requires games to stay legible in the **Popout S (`400×225`) and Popout L (`800×450`)** mini-player views, where symbols shrink to ~45–55px. Color-coding the 4 low symbols in **Ruby Red, Sapphire Blue, Emerald Green, and Amethyst Purple** ensures instant visual separation.

| Symbol ID | Asset Name | Color Code | Target Resolution | Status |
| :--- | :--- | :--- | :--- | :--- |
| `L1.png` | Greek Amphora Pottery | **Ruby Red** & Gold | `512 × 512 px` | ✅ **Final** (`assets/L1.webp` + `@2x`). **Low-symbol size standard:** longest side 430 px on the 512 canvas (lighter weight than the medallion highs). |
| `L2.png` | Ancient Drachma Coin | **Sapphire Blue** & Silver/Gold | `512 × 512 px` | ✅ **Final** (`assets/L2.webp` + `@2x`). Dark shadow halo removed, tilt corrected to a true circle (+8% width). Round lows use a **330 px diameter** (below the 355–360 px medallion highs). |
| `L3.png` | Penelope’s Loom Shuttle | **Emerald Green** & Gold | `512 × 512 px` | ✅ **Final** (`assets/L3.webp` + `@2x`). Blue-cyan glass edges shifted to emerald in post. Source was 1024 px, so `@2x` is slightly upsampled; replace from an upscaled source if available. |
| `L4.png` | Kylix Wine Goblet | **Amethyst Purple** & Gold | `512 × 512 px` | ✅ **Final** (`assets/L4.webp` + `@2x`). Indigo bowl shifted to true amethyst in post. Source 1024 px (`@2x` slightly upsampled). |

### Midjourney Prompts for Low-Paying Symbols (`L1`–`L4`)

* **`L1.png` — Greek Amphora Pottery (Ruby Red)** *(v3.4: simpler, unframed low symbol)*
  > `3D slot machine symbol icon, a chunky stylised ancient Greek amphora vase with a tall narrow neck, two curved handles and a wide rounded belly, standing upright in a slight three-quarter view, the entire body glazed in deep glossy ruby-red enamel like a polished gemstone, thin polished gold meander bands at the neck and foot, warm key light with a soft red inner glow and only a faint cyan rim light, the whole object small enough to leave empty black space on all four sides, bold simple silhouette readable at small size, no loose particles, no splashes, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, frame, border, medallion, cup, goblet, trophy, orange, lava, blue glow`

* **`L2.png` — Ancient Drachma Coin (Sapphire Blue)** *(v3.4: simpler, unframed low symbol)*
  > `3D slot machine symbol icon, a thick ancient Greek drachma coin standing upright and facing the viewer, the entire coin face filled with deep glossy sapphire-blue enamel like a polished gemstone, a raised polished silver owl embossed in the center, a thin gold rim, warm key light with a soft blue inner glow and only a faint cyan rim light, the whole object small enough to leave empty black space on all four sides, bold simple silhouette readable at small size, no loose particles, no splashes, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, frame, border, medallion`

* **`L3.png` — Penelope’s Loom Shuttle (Emerald Green)** *(v3.4: simpler, unframed low symbol)*
  > `3D slot machine symbol icon, a chunky ornate weaving shuttle lying diagonally, its body carved from deep glossy emerald-green jade like a polished gemstone, thickly wrapped in bright emerald-green silk thread with one loose curl, small polished gold end caps, warm key light with a soft green inner glow and only a faint cyan rim light, the whole object small enough to leave empty black space on all four sides, bold simple silhouette readable at small size, no loose particles, no splashes, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, frame, border, medallion`

* **`L4.png` — Kylix Wine Goblet (Amethyst Purple)** *(v3.4: simpler, unframed low symbol)*
  > `3D slot machine symbol icon, a wide shallow ancient Greek kylix drinking cup on a short stem with two handles, the bowl made of deep glossy amethyst-purple glass like a polished gemstone and brimming with purple wine, thin polished gold rim and handles, warm key light with a soft purple inner glow and only a faint cyan rim light, the whole object small enough to leave empty black space on all four sides, bold simple silhouette readable at small size, no loose particles, no splashes, no smoke, glossy ray-traced 3D render, premium casino slot game asset, centered, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped edges, frame, border, medallion`

---

## 4. Environment Backgrounds (`16:9` — `1920 × 1080 px`)
Used to visually transition the player between Base Game, Free Spins, and Max Win states. **All three ship as opaque WebP** (or opaque PNG if WebP is not possible).

| File Name | Set Piece | Game State | Status |
| :--- | :--- | :--- | :--- |
| `bg_basegame.png` | Walls of Troy at Night | Base Game (`basegame`) | ✅ **Final** (`assets/bg_basegame.webp`, 1920 × 1080, 169 KB) |
| `bg_freegame.png` | The Cyclops’s Treasure Cave | Free Spins Bonus (`freegame`) | ✅ **Final** (`assets/bg_freegame.webp`, 1920 × 1080, 216 KB) |
| `bg_superbonus.png` | Volcanic Shores of Hades | Super Bonus / Max Win Screen | ✅ **Final** (`assets/bg_superbonus.webp`, 1920 × 1080) |
| `bg_basegame_mobile.png` | Walls of Troy at Night — portrait | Base Game, mobile | ✅ **Final** (`assets/bg_basegame_mobile.webp`, 1080 × 1920, 129 KB; source 816 × 1456, upsampled 1.3×). Made by extending the landscape final in the MJ Editor. |
| `bg_freegame_mobile.png` | Cyclops’s Cave — portrait | Free Spins, mobile | ✅ **Final** (`assets/bg_freegame_mobile.webp`, 1080 × 1920, 127 KB; source 816 × 1456) |
| `bg_superbonus_mobile.png` | Shores of Hades — portrait | Super Bonus, mobile | ✅ **Final** (`assets/bg_superbonus_mobile.webp`, 1080 × 1920; source 816 × 1456) |

> **Mobile backgrounds (v3.5):** on a portrait phone (425 × 812, a reviewer test size), a 16:9 background shows only its central strip, which sits behind the reels. Each background therefore gets a **9:16 portrait version**, generated with the same prompt at `--ar 9:16` and the same seed, with the set piece placed **above and below** the reel area instead of at the sides.
> **Composition rule for all backgrounds:** the reel grid covers the centre, so keep the centre darker and low in detail; put the landmark (walls, boulder, basalt pillars) at the edges (16:9) or the top and bottom (9:16). Keep the frame edges free of bright detail that would compete with the UI.
> **Parallax:** Midjourney cannot output separate depth layers. Parallax is done in-engine with a slow scale drift on the plate plus separate ambient sprites (torch flames, mist, embers) layered on top (Section 5c).

* **`bg_basegame.png` — Walls of Troy at Night**
  > `Stylized 3D-rendered game environment background for an online slot machine, matching the glossy cinematic ray-traced look of a premium 3D slot game, the towering stone walls and gates of Troy at night under a deep Aegean-navy starry sky, flickering braziers casting molten-gold light along the battlements, the great wooden horse silhouetted before the gates, faint glowing cyan mist over the plain, darker low-detail center reserved for a slot reel grid, landmark detail kept toward the left and right edges, no text --ar 16:9 --s 150 --chaos 5 --no text, letters, people, characters, logo, watermark`

* **`bg_freegame.png` — The Cyclops’s Treasure Cave** *(v3.5: symmetric, matched to the approved base-game settings)*
  > `Stylized 3D-rendered game environment background for an online slot machine, matching the glossy cinematic ray-traced look of a premium 3D slot game, the vast cave of the Cyclops Polyphemus seen straight on, a giant round boulder half-sealing the cave mouth in the center, heaps of gold and bronze treasure piled symmetrically on the left and right, burning torches on both cave walls casting warm amber firelight, glowing cyan crystals in the rock, glowing cyan mist on the cave floor, deep shadows at the edges, symmetrical composition, no text --ar 16:9 --s 250 --chaos 5 --no text, letters, people, characters, creatures, logo, watermark`
  > **Portrait version:** open the approved landscape image in the Midjourney Editor, change the aspect ratio to 9:16 with the cave mouth centered, and extend top and bottom with: `cave ceiling with hanging rock and cyan crystals above, treasure-strewn cave floor with cyan mist below`.

* **`bg_superbonus.png` — Shores of Hades** *(v3.5: symmetric, matched to the approved backgrounds)*
  > `Stylized 3D-rendered game environment background for an online slot machine, matching the glossy cinematic ray-traced look of a premium 3D slot game, the bleak volcanic black-sand shore of the Underworld seen straight on, a dark river of glowing spectral cyan water flowing toward the viewer through the center, tall jagged black basalt pillars rising symmetrically on the left and right, glowing molten-gold lava cracks running through the rocks, a dim crimson-and-cyan sky with drifting ash clouds, deep shadows at the edges, symmetrical composition, no text --ar 16:9 --s 250 --chaos 5 --no text, letters, people, characters, creatures, skulls, gore, logo, watermark`
  > **Portrait version:** open the approved landscape image in the Midjourney Editor, change the aspect ratio to 9:16 with the river centered, and extend top and bottom with: `dim crimson-and-cyan ash-clouded sky above, black volcanic sand shore with glowing cyan river below`.

> **Style check:** generate the three backgrounds in one session with the same seed, and compare them against the approved symbols. All art must read as one cohesive style. Mismatched styles are a named cause of low reviewer ratings.

---

## 5. UI, Reel Frame, Win Popups & Custom Loader
Engine approval guidelines strictly require replacing all default `web-sdk` sample assets: the loader (`loader.gif`, `stake-engine-loader.gif`), the symbols, the backgrounds, and the win banners. **The Engine/Stake loader, logo, or splash must never appear**, including on launch, reload, replay, or reconnect.

| File Name | Aspect Ratio | Target Resolution | Status | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| `hero_bigwin_popup.png` | `4:5` | `1024 × 1280 px` | ✅ **Final** (`assets/hero_bigwin_popup.webp`, 1024 × 1280, alpha, bottom fade) | **Character anchor; generate first.** Waist-up Odysseus portrait used as the centerpiece for `BIG WIN` / `MEGA WIN` popups, and the source for the game tile foreground (Section 5b). |
| `reel_frame_5x3.png` | ≈ `1.39:1` | `1600 × 1150 px` (+ master 1387 × 997) | ✅ **Final** (`assets/reel_frame_5x3.webp`) | Transparent opening sized to exactly **5:3**: inner edge x 236–1362, y 250–926 on the 1600 file (cells ≈ 225 px). Lengthened by inserting one repeat of the side meander (seamless) plus a 4% band stretch. Companion layer `reel_backing_5x3` = dark panel at 80% opacity behind the symbols. **Layer order:** background → backing → symbols → frame. |
| `reel_backing_5x3.png` | same as frame | `1600 × 1150 px` | ✅ **Final** (`assets/reel_backing_5x3.webp`) | Dark translucent reel panel for symbol contrast; opacity can be tuned in-engine. |
| `game_logo_title.png` | `16:9` | `1024 × 576 px` (+ `@2x`) | ✅ **Final** (`assets/game_logo_title.webp`) | "ODYSSEY" + "VOYAGE OF FORTUNE" ribbon, spelling verified. Black background keyed out with the cyan/orange glow kept as soft alpha. |
| `win_banner_ribbon.png` | `16:9` canvas | `1024 × 576 px` (+ `@2x`, upsampled 1.4×) | ✅ **Final** (`assets/win_banner_ribbon.webp`) | Scroll ribbon with laurel and cyan gem; empty text panel ≈ x 195–820, y 201–368 on the 1024 file — fits "EPIC ODYSSEY WIN" at ~64 px with the amount below. Tier text and amount are live; set them in a bundled carved/classical display font, not a default UI font. |
| `feature_spin_badge.png` | `1:1` | `512 × 512 px` (+ `@2x`) | ✅ **Final v2** (`assets/feature_spin_badge.webp`) | Alpha rebuilt (v3.7): solid mask traced along the outer rim edge, so the dark Greek-key grooves stay opaque; outer orange/cyan glow kept as soft alpha within 18 px of the rim. Readable at 64–96 px. |

### Midjourney Prompts for UI & Framing Assets

* **`hero_bigwin_popup.png` — Odysseus Character Anchor** *(v3.1: 4:5 framing, waist-up, full crest in frame)*
  > `Heroic 3D character portrait of the bearded adult Greek hero Odysseus, waist-up view, the whole figure small enough to fit with empty black space on all sides, the complete helmet and the full crimson horsehair crest visible with black space above the crest tip, crested Corinthian bronze helmet pushed back high on the head revealing the full weathered face, ornate bronze-and-gold cuirass and crimson cloak, a golden recurve bow over one shoulder, triumphant confident expression, warm natural skin tones, bright warm frontal key light on the face, glowing cyan rim light only on the armour edges, no particles, no embers, no smoke, glossy ray-traced 3D render, premium casino slot character art, centered, flat solid black background --ar 4:5 --s 150 --chaos 5 --no text, letters, numbers, logo, watermark, cropped head, cropped crest`

* **`reel_frame_5x3.png` — The 5×3 Slot Grid Frame**
  > `Front-facing rectangular ornamental game UI frame for a 5x3 slot machine, crafted from dark weathered Greek marble columns and hammered gold trim with a glowing cyan Greek key meander pattern, completely empty solid black center, evenly lit, casino game UI asset, isolated on a flat solid black background --ar 16:9`

* **`game_logo_title.png` — Title Logo ("ODYSSEY: VOYAGE OF FORTUNE")** *(v3.6: full title; lettering matched to the WILD/BONUS plaques)*
  > `3D game title logo with two lines of text: the single large word "ODYSSEY" in massive chiseled rough hammered bronze-gold ancient Greek block capital letters with a strong glowing cyan outline around every letter, and below it on a narrow dark-bronze ribbon banner the smaller words "VOYAGE OF FORTUNE" in polished gold capitals, set over a dark-bronze Greek shield crest with a fine Greek key meander rim and a golden recurve bow crossed behind it, molten orange-gold glow along the underside, perfectly front-facing, symmetrical, centered, generous black margin on every side, dramatic rim lighting, glossy ray-traced render, premium casino slot game logo, flat solid black background --ar 16:9 --s 150 --chaos 5 --no extra words, numbers, tagline, watermark, cropped edges`
  > **Fallback if the small line warps:** generate with `the smaller line left as an empty ribbon banner` instead, and the subtitle is set in post in a classical carved-gold style.

  > Title check: "Odyssey: Voyage of Fortune" contains none of Engine's restricted title terms (Megaways, XWays, Enhanced, Boosted, RTP, "Gates of…", "…Bonanza", Olympus, Rush, Kraken, Waylanders) and no social-mode restricted words. "Odyssey" is a common word in slot titles, so reviewers will judge resemblance to existing games (guideline 253): keep the logo, tile and art style distinctly our own.


* **`win_banner_ribbon.png` — Big Win Celebration Ribbon** *(v3.6: matched to the logo ribbon)*
  > `Front-facing 3D game UI celebration banner, a wide dark-bronze ribbon banner with polished gold borders and swallow-tail ends curling back on both sides, a smooth dark empty center panel with no text, golden laurel wreath branches rising from both ends, a small glowing cyan gem at the top center, molten orange-gold glow along the underside, perfectly front-facing, symmetrical, centered, generous black margin on every side, dramatic rim lighting, glossy ray-traced render, premium casino slot game UI asset, flat solid black background --ar 16:9 --s 150 --chaos 5 --no text, letters, numbers, coins, particles, watermark, cropped edges`

* **`feature_spin_badge.png` — Feature Spin Button Badge** *(v3.6: matched to the multiplier crest and plaques)*
  > `Perfectly front-facing round 3D game UI button badge, a dark-bronze Greek shield with a fine Greek key meander rim and four small gold studs, a thin glowing cyan inner ring, in the center a bold embossed golden Trojan Horse head in profile with molten-gold glowing seams, simple strong silhouette readable at small size, centered with black margin around it, warm gold key light with cyan rim light only on the edge, no loose particles, glossy ray-traced render, premium casino slot game UI asset, flat solid black background --ar 1:1 --s 150 --chaos 5 --no text, letters, numbers, cropped edges, watermark`

---

## 5b. Platform-Required Branding & Marketing Assets *(new in v2)*
Engine will not let a game be submitted without a tile and cover art. The tile is **composed inside the Studio tile editor** from the layers below; there are no separate files to send. The editor adds the title text and studio name itself.

| File Name | Aspect Ratio | Target Resolution | Status | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| `tile_bg_3x4.png` | `3:4` | `1224 × 1638 px` | ✅ **Final** (`assets/tile_bg_3x4.webp`) | Daylight Troy harbour. Dark foliage in the bottom corners lifted in post (bottom-edge brightness 15 → 32). |
| `tile_fg_hero.png` | any (transparent) | `1053 × 1200 px` | ✅ **Final** (`assets/tile_fg_hero.png`) | Odysseus cutout from the hero source with the outer cyan neon halo removed (reads as an outline on bright backgrounds) and a soft bottom fade. |
| `cover_bg_16x9.png` | `16:9` | `1920 × 1080 px` *(exports at 640 × 360)* | ✅ **Final** (`assets/cover_bg_16x9.webp`) | 16:9 band cut from the `tile_bg_3x4` source (citadel + harbour), so tile and cover are one artwork. Source band 1506 × 847, ample for the 640 × 360 export. |
| `favicon.svg` | `1:1` | vector (+ PNG 16/32/48/512, `favicon.ico`, `apple-touch-icon.png` 180) | ✅ **Final** (hand-built SVG) | Gold recurve bow + cyan arrow on a navy rounded square with gold border, echoing the Bow Wild. The 16 px raster uses a simplified variant (thicker bow, no string, no border). Bundle locally; reference with relative URLs. |
| `loader` (replaces `loader.gif`) | `16:9` | `768 × 432 px` | ✅ **Final** (`assets/loader/`) | `loader.webp` (animated, 202 KB: logo shine sweep, breathing cyan glow, looping cyan comet bar), `loader.gif` fallback (512 px, 624 KB), `loader_poster.png`, and `loader.html` — a CSS reference loader with **real progress** (`setProgress(0–1)`), tested at 1024×576, 400×225 and 425×812. Remove `stake-engine-loader.gif` and `<LoaderStakeEngine>` from the build. |
| `provider_logo.png` | `1:1` | `1024 × 1024 px` | 🟡 **Placeholder** (`assets/branding/provider_logo.png` + `.svg`) | "Lobster Media" — coral claw mark and wordmark on navy. Replace with the final studio logo before launch. |
| `studio_logo_white.png` | `4:1` | `1200 × 300 px` | 🟡 **Placeholder** (`assets/branding/studio_logo_white.png` + `.svg`) | One colour (white), transparent background, as Engine requires. Replace before launch. |

**Tile rules (all must pass):**
* All three sources contain **no text of any kind**: no wording, promo text, or multipliers (e.g. `"1000x"`, `"NEW"`, `"BONUS"`). The title comes from the editor.
* Bright, vibrant, and not blending into the dark Stake lobby. The palette must be lifted here: warm golden-hour, turquoise sea, and sunlit marble rather than the night/cave scenes.
* Foreground subject large, with the title safe area left clear.
* Uploads: PNG, JPEG, WebP, or AVIF, **≤ 10 MB each**.

### Midjourney Prompts for Tile Assets

* **`tile_bg_3x4.png` — Bright Portrait Tile Background** *(v3.6: same set piece as the base game, but daylight)*
  > `Bright sun-drenched golden-hour view of the towering stone walls and gates of Troy on a hill above a sparkling turquoise Aegean sea with a fleet of Greek ships, warm glowing peach-and-gold sky with soft clouds, high-key vibrant luminous colors, the lower half of the image kept open and softly lit with sea and sky, no dark edges, no vignette, no people, no text, stylized 3D-rendered cinematic game key art matching a premium 3D slot game --ar 3:4 --s 150 --chaos 5 --no text, letters, people, characters, logo, watermark, night, dark sky, vignette`

* **`cover_bg_16x9.png` — Bright Wide Cover Background**
  > `Bright sun-drenched golden-hour Aegean seascape with the white-and-gold walls of Troy on a hill and a fleet of Greek ships on shimmering turquoise water, warm glowing sky, high-key vibrant luminous colors, no dark edges, no people, no text, no letters, stylized 3D-rendered cinematic game key art, wide composition with open space on the right and center --ar 16:9`

---

## 5c. Animation Plan — Stills In, Motion In-Engine *(new in v3.3)*
All art ships as **still layers**. Motion is built in **PixiJS 8** (tweens, blend modes, filters, particles), with **Spine** reserved for character animation. This keeps the bundle small (a 3★ criterion), keeps transparency working on every browser, and lets live values (multipliers, wins) stay dynamic.

### Core techniques
| Technique | How | Used for |
| :--- | :--- | :--- |
| **Additive glow** | Render glow layers with `blendMode = 'add'`; black becomes invisible, so no cut-out halos. | Lightning, cyan rims, sparks, beam |
| **Squash & stretch landing** | On reel stop: scale Y 0.9 → 1.06 → 1.0 over ~180 ms, ease-out-back. | Every symbol landing; heavier on WILD and SCATTER |
| **Anticipation** | Slow the last reel(s) and add a pulse on landed Scatters when 2 are already showing. | Scatter tease (near-trigger) |
| **Win pulse** | Winning symbols scale 1.0 → 1.12 → 1.0 (~400 ms loop) with an additive glow copy fading 0 → 0.8 → 0; non-winning symbols dim to ~45% brightness. | All line wins |
| **Shine sweep** | A diagonal white gradient strip masked to the symbol, sliding across in ~350 ms. | Metal surfaces: H1, plaques, crest, logo |
| **Lightning flicker** | Randomise alpha 0.6–1.0 every 40–80 ms plus small random X jitter (±2 px) on the lightning layer; never a regular rhythm. | Beam banner, wild bow, sticky chains |
| **Displacement shimmer** | `DisplacementFilter` with a scrolling noise texture at low strength. | Lightning heat-haze, Hades lava cracks, cave torchlight |
| **Particles** | A small pooled emitter (≤ 60 live particles per effect); sprites, not baked into art. | Sparks on landing, embers in Hades, coin burst on Big Win |
| **Screen shake** | 2–4 px, 150–250 ms, decaying; scale by event size. | Wild expansion, Full Fleet, Max Win |
| **Number roll-up** | Count win amounts up with ease-out; length scales with win tier. Must update incrementally to the final value (Engine rule). | Win meter, Big Win popup |

### Per-asset choreography
* **`wild_base_1x1` → `wild_expanded_beam_1x3` (Odysseus's Arrow, ~900 ms total)**
  1. Land with squash & stretch; bow glow pulses once (150 ms).
  2. Arrow flash: additive white flash on the arrowhead, then a light streak travels up the reel (200 ms).
  3. Expansion: the banner grows from the landed cell to full height with a mask reveal (scale Y from the cell origin, ease-out-expo, 300 ms); the 1×1 crossfades out under it.
  4. Lightning layer starts flickering; screen shake 3 px.
  5. Crest drops in (scale 1.4 → 1.0, ease-out-back, 200 ms), the multiplier **rolls through values** (slot-machine style, ~400 ms), then **stamps** with a shine sweep and a spark burst.
  6. Plaque slides up into place from 20 px below (150 ms).
* **Sticky lock (Free Spins)** — `wild_sticky_frame_1x3`: chains draw in from the corners (mask reveal, 250 ms), padlocks snap shut with a 1.15 → 1.0 scale bounce and a metal "clank" sound; chains keep a slow, low-strength lightning flicker while locked. Subsequent spins: locked reels stay still while others spin.
* **Multiplier sum on a line** — when 2+ expanded wilds share a winning line, their crest values fly to the win meter and merge (e.g. `10X` + `25X` → `35X`) before the line pays.
* **Scatter (`SCATTER`)** — idle: subtle gold seam glow pulse (2 s loop). Landed: squash & stretch + dust puff. On trigger: all scatters pulse together, then the camera pushes in (scale 1.0 → 1.08) before the bonus transition.
* **High symbols (`H1`–`H4`)** — win: pulse + shine sweep; `H4` astrolabe rings rotate slowly (separate ring layer if available; otherwise a rotating glow overlay).
* **Low symbols (`L1`–`L4`)** — win: pulse + coloured additive glow in their code colour (ruby, sapphire, emerald, amethyst). Keep them simpler than the highs, so the value hierarchy reads.
* **Full Fleet (Max Win)** — every sticky reel flashes in sequence left to right (80 ms apart), all crests stamp together, screen shake 6 px, then hard cut to the Max Win popup.
* **Big Win popup** (`hero_bigwin_popup` + `win_banner_ribbon`) — hero rises 40 px with a fade (300 ms), ribbon unrolls (mask reveal, 250 ms), coin and spark particles, tier label upgrades live (BIG → MEGA → EPIC ODYSSEY) as the count rises, each upgrade with a shine sweep and a shake. Optional Spine: idle breathing and cloak sway on the hero.

### Backgrounds & ambience
* **Parallax:** split each background into 2–3 depth layers if possible (sky / mid / foreground) and drift them a few pixels with the pointer or device tilt; otherwise a slow 1.0 → 1.03 "Ken Burns" scale over 20 s.
* **Ambient loops (in-engine):** torch flicker (additive light sprites with alpha noise) in the cave; drifting embers and lava-crack shimmer in Hades; mist and star twinkle at Troy.
* **Optional video:** the three backgrounds may ship as short opaque looping MP4/WebM files (a few seconds, heavily compressed) with the still image as a fallback. No video for any asset that needs transparency.

### Transitions between game states
* Base → Cyclops's Cave: reels darken, the scene "descends" (backgrounds slide up with a vertical blur), torches ignite in sequence.
* Base → Shores of Hades: a red-gold crack splits the screen, cyan spectral light floods in, then the volcanic shore fades up.
* Every transition is skippable and ≤ 2.5 s.

### Rules & performance limits
* **Turbo / fastplay:** shorten every timing by ~50–70%, but win amounts, winning combinations and popups must stay legible (Engine rule).
* **Spacebar** skips count-ups and celebration animations where permitted, and always places the next play when idle.
* **Sound off** must silence every animation sound (Engine rule); never tie a visual cue to sound alone.
* **Popout S (400 × 225):** drop screen shake and particle counts by half; scale the crest ×1.5 so the multiplier stays readable.
* **Performance budget:** target 60 fps on mid-range phones; cap particles, pool sprites, pack all frames into texture atlases, and avoid full-screen filters on mobile.
* **No animation may change an outcome:** results come only from the RGS response; animation is presentation only.

---

## 6. Engine Export & Compliance Checklist
Before handing the final folder over to the developer for the `web-sdk` (`PixiJS 8`):

1. **Alpha Channels:** Strip all black backgrounds and export as **32-bit PNGs (with transparency)**. **Exception: all three `1920×1080` backgrounds** (`bg_basegame`, `bg_freegame`, `bg_superbonus`) are opaque and ship as WebP (or opaque PNG). Midjourney outputs glowing assets on black, so check every cutout for dark halos at the edges.
2. **Padding Margin:** Leave a **5% transparent margin** around the outer edges of all `512×512` symbols and `512×1536` Expanded Wilds so glow shaders or scale-bounce animations in PixiJS never clip at the bounding box. *(Internal rule, not an Engine requirement.)*
3. **Bundle Size (3★ criterion):** Engine rates "optimised bundle size" and penalises slow loads. There is no published hard cap, so treat these as suggestions: ship backgrounds, popups, and the reel frame as **WebP**, pack the symbols and wild layers into **sprite atlases**, and strip metadata.
4. **No Baked Gambling Text (extends to images):** Social-mode word restrictions apply to images as well as UI. Keep currency symbols (`$`) out of all pixels, and never bake any of these: `bet`, `buy`, `bonus buy`, `pay`/`pays`/`paid`, `cash`, `credit`, `currency`, `money`, `deposit`, `wager`, `purchase`, `win feature`. Allowed baked text: `"WILD"`, `"BONUS"` (alone), `"THE ODYSSEY"`. All other labels (`FEATURE SPIN`, multiplier numbers, win tiers, balances) are dynamic text in Svelte 5 so the game can switch between Stake.com and Stake.us (Social Mode).
5. **No Stake™ / Engine Branding:** No Stake or Engine logos, marks, or themes in any asset. Remove the sample loaders, symbols, backgrounds, and win banners that ship with the `web-sdk`.
6. **Fonts:** Every font must be **bundled locally** and served from the Engine CDN. No Google Fonts or other external hosts at runtime. They produce console errors under the strict content policy and can fail review.
7. **Title Restrictions:** The title, logo text, loading screen, and HTML `<title>` must avoid `Megaways`, `XWays`, `Enhanced`, `Boosted`, `RTP`, `Gates of…`, `…Bonanza`, `Olympus`, `Rush`, `Kraken`, `Waylanders`, or anything implying a tie to another publisher.
8. **Content & Originality:** No imagery of children or child-like characters (a hard prohibition in any gambling context), nothing sexual, gory, hateful, or in poor taste, and nothing that closely resembles an existing slot's logo, symbols, or art style.
9. **Visual Cohesion:** One consistent art style across symbols, backgrounds, UI, and logo. Reviewers specifically penalise generic AI assets (default fonts, plain gradients, emoji-style icons, stock border effects) and mismatched styles. Plan hand-finishing passes on the logo, frame, and plaque.
10. **Reviewer Screen Sizes:** Verify every asset at **laptop 1024×576, Popout S 400×225, Popout L 800×450, and mobile 425×812**. Confirm `L1`–`L4` and `H1`–`H4` are distinguishable at ~45–55 px, and that nothing scrolls or clips.
11. **Animation:** See Section 5c. Ship still layers only; all motion is built in PixiJS (and optionally Spine). Animation polish counts toward the rating.

---

## 7. Change Log

**v3.3 (2026-11-03)**
* Added Section 5c, the animation plan (core techniques, per-asset choreography, transitions, and rules/performance limits). Video limited to optional opaque background loops.

**v3 (2026-11-03): full regeneration**
* All earlier images (Images 1–10) are discarded; every asset is now `To Generate`.
* Added Section 0 (generation order) and new prompts for `wild_base_1x1`, `SCATTER`, `H1`, `H4`, `bg_basegame`, `bg_freegame`, and `hero_bigwin_popup`.
* Added `scatter_text_plaque.png` so `"BONUS"` and `"WILD"` share one plaque design.
* Removed `--profile`, `--oref`, and `--iw` from all prompts; the moodboard is applied as the default.
* `bg_freegame` set piece is now only the Cyclops’s cave (the "Nestor’s" alternative is dropped).

**v2 (2026-11-03)**

**Corrections**
* `SCATTER.png`: baked `"BONUS"` is **allowed** in-game. v1 treated it as a risk. Only `"bonus buy"` is restricted. It is barred only from the game tile.
* `wild_expanded_hero_1x3` / `wild_expanded_beam_1x3` prompts: removed baked `"WILD"` and `"100X"`, which contradicted the modular design.
* `wild_text_plaque.png`: ratio unified to `2:1` (512 × 256) and the prompt changed to `--ar 2:1`.
* `bg_superbonus` and checklist: all three backgrounds are now opaque. v1 omitted `bg_superbonus`.
* `H2` prompt: crimson sails replaced with ivory/gold to match the table's Navy & Gold and to avoid a clash with `H1`/`L1`.
* `bg_superbonus` prompt: "2D/3D painted" replaced with the glossy 3D look of the rest of the game.

**Additions**
* New prompt for `feature_spin_badge.png`.
* New Section 5b: game tile, cover art, favicon, custom loader, and the provider and studio logos.
* Section 6 expanded: bundle size, social-mode word list, branding, fonts, title restrictions, content rules, cohesion, reviewer sizes, and Spine note.

**Decisions made**
* **Super Bonus renamed "The Shores of Hades".** The title restriction covers only the game title, but the new name stays clear of "Gates of…". `slot_rules.md` v2 uses it everywhere. Only the asset file name `bg_superbonus.png` is unchanged.
* **`slot_rules.md` v2 written:** adds the required general disclaimer, a Social Mode wording map, and a per-mode max win.
* **Bundle-size targets (Section 6, item 3) accepted** as working guidance.

**Open items**
* **Owner-supplied logos:** `provider_logo.png` and `studio_logo_white.png` must come from the studio owner.
* **Re-trigger rules** are still undefined in `slot_rules.md`. That is a math decision, not an art one.
