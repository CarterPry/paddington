# Wash Day — layer generation prompts

Pipeline adapted from 里大猫's course-01 pattern: generate a **style anchor** first,
then generate every layer **with the anchor attached as a reference image**, treating
it as the locked source of truth for style. Do the steps by hand once before automating.

**Recommended models:** Gemini image (Nano Banana) or GPT-image — both follow
reference images + transparency instructions well. Always request PNG with
transparent background for layers 2–8.

**Important:** these prompts describe an *original* naive folk-art scene of ours.
Don't feed the model someone else's artwork as the reference — the anchor we
generate in Step 1 is the only reference used.

---

## Step 1 — style_anchor.png (1600×1000, opaque)

> A naive folk-art landscape painting in gouache, with dense visible stippled
> brushwork and a soft matte paper grain. Rolling olive-green hills under a muted
> powder-blue sky. A small white farmhouse with a brick-red tiled roof and green
> shuttered windows sits mid-right. A cluster of dark cypress trees on the
> hillside to the right. The middle ground is a sea of big round bushes, each
> built from hundreds of tiny leaf strokes in layered greens, lighter toward the
> upper-left where the sun hits. The foreground is a smooth pale yellow-green
> meadow hill with fine vertical grass hatching. A large gnarled olive tree with
> a leaning brown trunk fills the upper-left quarter, its canopy silvery-green
> clusters of stippled leaves. A thin clothesline runs from the tree toward the
> right. Flat perspective, no outlines, consistent light from upper-left,
> muted matte colors, hand-painted texture everywhere. No people, no animals.

Keep this image. Attach it to **every** prompt below as the style reference with:

> Match the attached reference image exactly for style: same gouache stippled
> brushwork, same palette, same matte grain, same light direction. The reference
> is the source of truth for style — do not restyle, do not smooth, do not add
> outlines or gloss.

---

## Step 2 — background.png (3200×2000, opaque)

> [attach style_anchor] Repaint this exact scene at higher detail. Composition
> requirements: olive tree canopy fills the upper-left quarter with its trunk
> reaching the bottom-left meadow; white house with red roof centered slightly
> right at one-third height; cypresses on the right hillside; round stippled
> bushes spanning the full width of the middle ground; pale meadow hill across
> the entire foreground; a thin dark clothesline from the tree trunk to the
> right edge at 60% height; ONE pale blue-grey bed sheet hanging on the line
> left of center, reaching down behind the meadow crest. Absolutely no people
> and no animals anywhere.

## Step 3 — woman.png (460×790, transparent)

> [attach style_anchor] A single isolated figure on a fully transparent
> background, same painted style: an elderly village woman standing in profile
> facing right. White headscarf knotted behind, ruddy warm-red face and hands,
> long dark-green dress covered in tiny white polka dots reaching her ankles,
> small red shoes. Her far arm reaches up and forward to chest height as if
> holding a clothesline. Her near arm is MISSING — cleanly absent, the dress
> side smooth where it would attach. Feet at the bottom-center of the canvas.

## Step 4 — woman_arm.png (280×120, transparent)

> [attach style_anchor + woman.png] The missing near arm for this painted
> figure, isolated on a transparent background, same dark-green sleeve fabric:
> a bent arm from shoulder (left edge of canvas, lower third) reaching
> rightward and slightly up to a small ruddy red hand with fingers pinching.
> Horizontal orientation, shoulder at far left.

## Step 5 — shirt.png (400×340, transparent)

> [attach style_anchor] A white long-sleeve shirt hanging on a clothesline,
> isolated on a transparent background, same gouache style: two small wooden
> clothespins at the very top edge grip the shoulders, sleeves hang slightly
> spread, soft grey fold shadows down the body, gentle breeze in the fabric.

## Step 6 — white_cat.png (180×168, transparent)

> [attach style_anchor] A small white cat sitting upright facing left, isolated
> on a transparent background, same painted style: compact rounded body, pink
> inner ears, calm dark eyes, tail curled beside its paws.

## Step 7 — cat_body.png (520×260, transparent)

> [attach style_anchor] The TORSO ONLY of a black cat in side view facing
> right, isolated on a transparent background: chest at right, long slightly
> arched back, full rounded haunch at left. NO head, NO neck, NO tail, NO legs —
> every edge where those parts would attach is cleanly cropped and smooth.
> Near-black paint (#131311) with a faint darker brush speckle, matte.

## Step 8 — cat_head.png (260×220, transparent)

> [attach style_anchor + cat_body.png] The HEAD ONLY of the same black cat,
> facing right, isolated on a transparent background: rounded skull, two tall
> pointed ears, slight muzzle, two yellow-green almond eyes with vertical black
> pupils, tiny rust-red nose, three fine off-white whiskers sweeping from each
> cheek. The neck edge at lower-left is cleanly cropped.

## Step 9 — cat_leg.png (80×130, transparent)

> [attach style_anchor + cat_body.png] ONE leg of the same black cat, isolated
> on a transparent background: vertical, from hip at the top to a small rounded
> paw at the bottom, slightly tapered at the ankle. Same near-black matte paint.

---

## Install

Drop the finished PNGs into `folk-painting/assets/` with the exact filenames
above and reload the page. Each layer upgrades independently — anything missing
keeps the procedural painted fallback, so you can iterate one layer at a time.

Check alignment with `?debug=1` (draws pivot markers and layer rects).
