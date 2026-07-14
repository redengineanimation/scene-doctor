# The Panel

Scene Doctor lives in the 3D Viewport sidebar (++n++) under the
**Doctor** tab. Top to bottom:

## Masthead

The branded header — logo, wordmark, and your tier + version.

## Profile & Run Diagnosis

- **Profile** dropdown (Pro) — choose which checks run and how they weigh
  into the score. See **[Profiles](profiles.md)**.
- **Run Diagnosis** — scans the whole scene and refreshes the results.

## Health score

A live **0–100** score with a progress bar. It recalculates instantly as
you fix or dismiss checks, and turns red below 60. Full detail in
**[Health Score](health-score.md)**.

## Diagnosis Results

One collapsible group holding every check. Behavior:

- **Sorted worst-first** — errors on top, clean checks at the bottom.
- **Failing checks** show their custom icon, label, count, and a fix
  button.
- **Clean checks** show a dim check mark and recede.
- **Expand a row** (the ▸ triangle) to reveal its drill-down: affected
  objects with click-to-select, extra stats, and per-item fix tools.

### The dismiss (eye) button

Click the eye on any check to **dismiss** it. Dismissed checks:

- keep their issues listed,
- count as **healthy** in the score,
- stay dismissed across re-diagnosis and profile switches,
- save with the `.blend`.

Use it when a flagged "problem" is intentional.

## Footer

- **Fix All Safe** (Pro) — batch-applies every low-risk fix. See
  **[Tools & Fixes](tools.md#fix-all-safe)**.
- **Export Report** (Pro) — save the diagnosis as CSV.

## Preferences

**Edit → Preferences → Add-ons → Scene Doctor** exposes:

- **License Key** — optional, for support/updates only.
- **Transform Tolerance** — how far from identity a scale/rotation may be
  before it's flagged.
- **Poly Scan Cap** — meshes above this poly count are skipped by the
  heavy geometry checks (keeps diagnosis fast on huge scenes).
- **Doubles Merge Distance** — threshold for the Doubled Vertices check.
- **Degenerate Threshold** — size below which edges/faces count as
  degenerate.
