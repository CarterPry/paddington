# Paddington — Wash Day

An interactive naïve-art painting, drawn entirely in code (Canvas 2D, single HTML file).

A grandmother pins laundry under an olive tree while a little bear in a red hat
and blue duffle coat follows your mouse around the meadow — walking, leaping,
sitting down to wait, and slipping behind the tree and the grandma as he roams.

## Run

```
python3 -m http.server 8642
# open http://localhost:8642/
```

## Interactions

- **Move the mouse** — the bear strolls toward it (spring physics with a polite
  personal-space radius); fast sweeps make him trot
- **Click far away** — he leaps
- **Hold still** — he sits, sets his suitcase down, and blinks
- The shirt on the line gusts when your cursor sweeps past it

## How it's painted

~130k procedural brush strokes laid down once at load: flow-aligned leaf flicks
in the foliage, a full pelt of combed grass, fine paper tooth on sky and hills.
Figures are flat matte shapes with offset under-layers, in the naïve / folk-art
tradition. `assets/` holds an optional image-layer pipeline (see `PROMPTS.md`)
for swapping any procedural layer with model-generated art.
