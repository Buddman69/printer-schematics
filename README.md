# Printer Schematics

Board-level reference for 3D printer hardware: pinouts, connector maps, photos,
and what has been verified against a real machine. Kept separate from any
firmware or calibration project so it stays clean and reusable.

> **Disclaimer.** Nothing here is official. Vendor pinout sheets are often for
> an older board revision than the one shipping, and anything transcribed or
> inferred can be wrong. Before connecting anything, check a pin with a
> continuity meter against the MCU. Use at your own risk.

## Layout

```
<Brand>/<Model>/<Part>/<Board ID>/
    README.md          the part: what it is, where it sits, revision history
    <Revision>/
        README.md      what is known about this exact revision
        *.png / *.pdf  photos and source documents for this revision
```

- **Board ID** is the silkscreened designation. Filesystem-unfriendly
  characters are replaced, so `A-9(GD)` becomes `A-9-GD`.
- **Revision** is the silkscreened version, e.g. `V1.5`.
- Each revision folder only holds material about that revision. A pinout sheet
  for V1.2 goes in `V1.2/` even if the board you own is V1.5.

## Confidence tags

Every fact in a revision README carries one of these:

| Tag | Meaning |
|---|---|
| **[verified]** | Checked on a real machine: live config, measurement, or continuity test. Says how and when |
| **[vendor]** | From a vendor document. Correct for the revision the document names, possibly not for others |
| **[inferred]** | Reasoned from photos, part markings, or conventions. Plausible, not checked |

When sources disagree, the README says so and names which one wins.

## Contents

| Brand | Model | Part | Board | Revisions |
|---|---|---|---|---|
| QIDI | Max4 | Toolhead | [A-9(GD)](QIDI/Max4/Toolhead/A-9-GD/) | V1.2 (vendor pinout), V1.5 (photo + verified pins) |
