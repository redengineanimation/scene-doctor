# Checks

Scene Doctor runs sixteen checks. Each has a **severity** (how much it
weighs on the [health score](health-score.md)), a **tier** (Lite or Pro),
and a **fix**. Any fix whose correct outcome is ambiguous is per-item
opt-in — never a blind batch — and destructive fixes confirm first.

!!! abstract "Core vs. advanced"
    The five **core** checks run in both Lite and Pro. The eleven
    **advanced** checks are Pro only.

---

## Core checks

### Unapplied Transforms

*Warning · Lite + Pro*

Flags objects whose **scale or rotation** isn't applied (not identity).
Unapplied scale breaks modifiers, physics, and exports; unapplied
rotation confuses normals and baking.

**Fix — Apply.** Applies rotation and scale. Objects that are **linked**,
share **multi-user data**, are **animated**, or have **children** are
skipped by default (applying their transform would shift dependents); a
redo-panel toggle lets you include parented objects.

---

### Ngons

*Warning · Lite + Pro*

Counts faces with **more than four sides**, and reports triangle counts
too. Ngons shade unpredictably and cause problems on subdivision and
export.

**Fix — Select.** Selects the offending objects so you can retopologize
or triangulate deliberately. Scene Doctor never auto-triangulates — that's
a modeling decision.

---

### Flipped Normals

*Warning · Lite + Pro*

Detects faces whose normals disagree with a consistent outward
recalculation.

**Fix — Recalc (per object).** On **closed** meshes the outward direction
is objective. On **open** meshes there is no defined inside/outside, so
those are flagged with a *"verify visually"* note and fixed **one object
at a time** — never in a blanket batch. (A fully-inverted open shell with
no correct neighbors can't be detected; only mixed winding shows up.)

---

### Orphan Datablocks

*Info · Lite + Pro*

Lists **zero-user** datablocks — meshes, materials, images and more that
nothing references. They bloat the file and clutter browsers.

**Fix — Purge.** Removes all zero-user data (recursive). Asks for
confirmation first, since purging clears undo history for that data.

---

### Missing Files

*Error · Lite + Pro*

Finds external file paths that don't resolve — textures, HDRIs, linked
libraries, fonts, sounds, caches. For missing **images** it also lists
which materials use them. UDIM tiles are handled.

**Fix (Pro).**

- **Search Folder** — point it at your project/asset root and Scene
  Doctor recursively finds the missing files by name and relinks them all
  (relative paths when the `.blend` is saved).
- **Locate** (per item) — pick a file on disk to relink one dependency.

---

## Advanced checks (Pro)

### Non-Manifold

*Warning (Error under 3D-Print profile) · Pro*

Counts **non-manifold edges** (three or more faces on one edge / interior
junctions) and non-manifold vertices per mesh. Boundary (open) edges are
reported in the detail but do **not** flag on their own — open meshes are
normal in real assets.

**Fix — Select.** Enters Edit Mode with the non-manifold elements
selected for manual cleanup. Never auto-fills holes.

---

### Doubled Vertices

*Warning · Pro*

Counts vertices within the **Doubles Merge Distance** (Preferences,
default `0.0001`) — coincident verts left by imports and boolean
operations.

**Fix — Merge All / per object.** Merges by distance at the chosen
threshold and reports how many verts collapsed. Eligible for Fix-All-Safe
**only** at the conservative default distance.

---

### sRGB Data Textures

*Error · Pro*

The high-value one. Finds image textures tagged **sRGB** that feed
**non-color (data)** inputs — roughness, metallic, normal maps, bump
height, displacement, and similar. sRGB on a data map silently corrupts
shading, and almost nobody catches it.

Scene Doctor traces the node graph (through pass-through nodes) to be
sure. An image used in **both** color and data contexts is flagged as
**MIXED** with a note and is **not** auto-changed.

**Fix — Fix All / per item.** Sets the image color space to **Non-Color**.
MIXED images are skipped — resolve those by hand.

---

### Missing UV Maps

*Warning · Pro*

Flags mesh objects that have a material **using UV coordinates** but no UV
layer. Fully procedural materials (Generated coordinates) are correctly
**not** flagged.

**Fix — Select** the objects for manual unwrap, or **Add empty UV layer**
(a clearly-labeled minor fix — it stops exporters erroring, it is *not* an
unwrap).

---

### Broken Drivers

*Error · Pro · differentiator*

Iterates every driver in the file and flags the broken ones: invalid
drivers, variable targets that don't resolve (deleted object, dead data
path), or empty/uncompilable expressions. Lists the owning datablock and
path.

**Fix — Select** the owner to repair by hand. Scene Doctor never
auto-deletes drivers — that's destructive and ambiguous.

---

### Broken Modifier Targets

*Error · Pro*

Finds modifiers whose **required** object or collection reference is
missing (a deleted Boolean operand, a gone Mirror object, etc.). Maintains
a per-modifier map of which targets are mandatory, verified per Blender
version.

**Fix — Select** the object to re-target the modifier. No auto-fix.

---

### Loose / Degenerate

*Warning · Pro*

Per mesh: **loose vertices**, **loose edges**, **zero-length edges**, and
**zero-area faces** — the invisible junk that trips up exporters and
booleans.

**Fix — Clean.** Deletes the loose/degenerate elements and reports counts.
Confirms first. Kept **out** of Fix-All-Safe by default — opt in per
object.

---

### Duplicate Materials

*Warning · Pro*

Finds materials that are **structurally identical** — same node graph and
key settings — usually surfaced as `Mat`, `Mat.001`, `Mat.002`. The name
suffix is a hint; the comparison is on structure, so similar-but-different
materials are **not** grouped.

**Fix — Merge.** Remaps all users to one canonical material and removes
the copies. Shows exactly what merges into what before committing. Kept
out of Fix-All-Safe (a false positive would change appearance).

---

### Naming Hygiene

*Info (Warning under Game-export profile) · Pro*

Flags **default primitive names** (`Cube`, `Sphere.001`, `Suzanne`…) and
`.00N` duplicate suffixes — names that flatten badly on export to game
engines.

**Fix — Select**, or **batch-rename to a preset**:

| Preset | Result |
|--------|--------|
| Unity | `PascalCase` |
| Unreal | `SM_` + `PascalCase` |
| Godot | `snake_case` |
| Export-Safe | `A–Z 0–9 _` only |

The Blender `.001` suffix is always dropped first, and collisions get a
clean two-digit suffix instead of Blender's `.001`.

---

### Visibility Mismatches

*Warning · Pro*

Catches silent render surprises: objects **hidden in the viewport but
still enabled for render**, and objects **visible but disabled for
render**.

**Fix — Reconcile (per item).** Match render visibility to the viewport,
or vice versa. Per-item because the "correct" state depends on intent.

---

### Empty Containers

*Info · Pro*

Lists **empty collections**, objects living loose in the scene root
(unorganized), and unused Empty objects.

**Fix — Select**, or **Clean Collections** to remove empty collections
(confirmed).
