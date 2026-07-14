# Tools & Fixes

Beyond the per-check fixes, Pro adds three cross-cutting tools.

## Fix All Safe

*Pro.* One button that applies **only** the fixes that are reversible via
undo, unambiguous, and low false-positive risk.

**Included by default:**

- Apply Transforms (with the usual skip rules for linked / multi-user /
  animated / parented objects)
- sRGB Data Textures → Non-Color (MIXED-use images are never touched)
- Merge Doubled Vertices — **only** at the conservative default distance

**Never included** (always manual / per-item): orphan purge, flipped-
normal recalc, duplicate-material merge, driver and modifier repairs,
loose/degenerate deletion, renames, collection cleanup, missing-file
relink.

Before it runs, Fix All Safe shows a **pre-run summary** of exactly what
it will change and how many items, and asks once. Afterward it reports a
per-category result.

!!! info "Why so conservative"
    A batch button should never surprise you. Anything whose outcome
    depends on judgment — is this normal really flipped? are these
    materials truly the same? — stays out, so you decide it per item.

## Export Report (CSV)

*Pro.* Saves the current diagnosis to a CSV for studio QC or handoff.
Columns: `check_id, severity, item, detail, count, status`. It respects
the **active profile** and marks **dismissed** checks as such. Written
through a normal file-save dialog.

## Naming Presets

*Pro.* When the **[Naming Hygiene](checks.md#naming-hygiene)** check flags
default or suffixed names, batch-rename the flagged objects to an engine
convention:

| Preset | Example: `my rock.001` → |
|--------|--------------------------|
| Unity (PascalCase) | `MyRock` |
| Unreal (`SM_` + PascalCase) | `SM_MyRock` |
| Godot (snake_case) | `my_rock` |
| Export-Safe | `my_rock` (illegal chars → `_`) |

The Blender `.001` suffix is always dropped first, and any name collision
gets a clean `_NN` suffix rather than Blender re-introducing `.001`.

## Folder Search (missing files)

*Pro.* On the **[Missing Files](checks.md#missing-files)** check, point
**Search Folder** at your project or asset root. Scene Doctor walks it
recursively, matches the missing files by name (case-insensitive,
UDIM-aware), and relinks everything it finds in one pass.
