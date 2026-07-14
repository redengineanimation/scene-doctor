# Quick Start

## Run your first diagnosis

1. Open a scene — a downloaded asset or an in-progress file works best.
2. In the 3D Viewport, press ++n++ and open the **Doctor** tab.
3. Click **Run Diagnosis**.

Scene Doctor scans the whole scene and fills the panel with results in a
second or two.

## Read the results

- The **Health score** (0–100) headlines how clean the scene is. It turns
  red below 60.
- Checks that **found problems** float to the top with their icon and a
  count. Clean checks show a dim check mark and sink to the bottom.
- Click a check row to **expand** it — you'll see the affected objects,
  extra stats, and any fix tools.

## Fix something

- Click a check's **fix button** (e.g. *Apply*, *Purge*, *Merge All*) to
  fix everything that check found.
- Or expand the row and fix items **one at a time** — useful when only
  some objects should be changed.
- Destructive fixes (purge, delete, merge) ask for confirmation first.

!!! tip "Fix All Safe"
    In Pro, the **Fix All Safe** button at the bottom applies every
    low-risk, reversible fix at once, after showing you exactly what it
    will change. See **[Tools & Fixes](tools.md#fix-all-safe)**.

## Dismiss what you don't care about

Click the **eye** icon on a check to dismiss it. Its issues stay listed
but count as healthy in the score — handy when a "problem" is
intentional. Dismissals persist with the `.blend`.

## Next steps

- Pick a **[Profile](profiles.md)** to focus the checks for game export,
  3D printing, or rendering.
- Read the full **[Checks](checks.md)** reference to understand what each
  one means.
