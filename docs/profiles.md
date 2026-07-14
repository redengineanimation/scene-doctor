# Profiles

*Pro feature.*

A **profile** runs a focused subset of checks with severities tuned for a
specific workflow. Pick one from the dropdown at the top of the panel;
running a diagnosis then runs only that profile's checks. The active
profile saves with the `.blend`.

## General

Every check, default severities. The default — equivalent to no profile.

## Game Export (UE)

Tuned for the send2ue → Unreal pipeline.

Runs: **Unapplied Transforms · Ngons · Non-Manifold · Missing UV Maps ·
sRGB Data Textures · Naming Hygiene** (raised to *Warning* here).

Use before exporting static meshes so bad transforms, missing UVs, and
default names don't follow the asset into the engine.

## 3D Print

Tuned for watertight, printable geometry.

Runs: **Non-Manifold** (raised to *Error* — holes mean it won't print) ·
**Doubled Vertices · Flipped Normals · Loose / Degenerate**.

## Render

Tuned for a pre-render sanity pass.

Runs: **sRGB Data Textures · Missing Files · Broken Drivers · Broken
Modifier Targets · Visibility Mismatches**.

Catches the things that silently ruin a render — wrong color spaces, pink
missing textures, dead drivers, objects that render when they shouldn't.

!!! tip
    Switching profiles keeps your dismissals. A check you dismissed under
    *General* stays dismissed when it appears in *Render*.
