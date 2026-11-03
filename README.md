# Odyssey: Voyage of Fortune — Art Assets

Art, rules and asset specifications for **Odyssey: Voyage of Fortune**, a 5×3, 20-line slot built for the Engine platform (Svelte 5 + PixiJS 8 web SDK).

| File | Contents |
| :--- | :--- |
| [`art_assets.md`](art_assets.md) | Asset manifest: every asset's size, status, placement coordinates, Midjourney prompts, the animation plan and the compliance checklist. |
| [`slot_rules.md`](slot_rules.md) | Game rules and paytable spec, including the social-mode (Stake.us) wording map and the general disclaimer. |
| [`assets/`](assets) | Final exported art. |

## Asset folder conventions
- **`.webp`** files are for the game bundle; **`.png` / `.jpg`** files are masters.
- **`@2x`** files are double resolution for high-DPI screens.
- Reel symbols are 512 × 512 with a 5% transparent margin; the expanded wild layers are 576 × 1536 and must be anchored at their horizontal centre.
- Backgrounds come in desktop (1920 × 1080) and mobile (`_mobile`, 1080 × 1920) versions.
- `assets/loader/` holds the custom loader (animated WebP, GIF fallback and an HTML/CSS reference with real progress).
- `assets/branding/` holds **placeholder** studio logos ("Lobster Media"), to be replaced before launch.

Placement data (plaque and crest positions, the reel opening, layer order) is recorded in `art_assets.md`.
