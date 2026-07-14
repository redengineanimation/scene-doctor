# FAQ

## There's no Uninstall button — how do I remove it?

The add-on was placed on disk manually instead of installed from the zip.
Disable it, quit Blender, and delete its folder — full steps in
**[Installation → No Uninstall button](installation.md#no-uninstall-button)**.
To avoid this, always **install the zip**, don't hand-copy the folder.

## Do I need the license key for it to work?

No. Scene Doctor works fully without a key. The key is only for support
and update eligibility.

## Can the health bar be green/yellow/red?

No. Blender's UI draws progress bars in the theme's accent color, with no
per-value color option — a true traffic-light bar would need custom GPU
drawing. The health box does turn **red** below 60.

## Why is a passing check still shown?

So you can trust the report is complete. Clean checks show a dim check
mark and sink to the bottom; failing checks rise to the top. Collapse the
**Diagnosis Results** group if you want them out of the way.

## A flagged "problem" is intentional. Can I hide it?

Yes — click the **eye** to dismiss that check. It stays listed but counts
as healthy in the score, and the dismissal saves with the `.blend`.

## Blender won't launch after installing an add-on.

Launch Blender with **factory settings** to get in, then remove the
culprit:

```
blender --factory-startup
```

Then disable/uninstall it. Installing add-ons from a **network drive
(NAS)** or hand-copying folders into the extensions directory are the
usual causes — install the zip to a local drive instead.

## Which Blender versions are supported?

Blender **4.2 and newer**, verified through 5.1. Version-specific APIs are
guarded so it degrades gracefully rather than crashing on the edges.

## Is my scene safe? Will fixes ruin my file?

Fixes use Undo, and anything destructive (purge, delete, merge) confirms
first. Ambiguous fixes are per-item, never a blind batch. Still — keep
backups of important files, as with any tool that edits data.

## Lite vs Pro?

See **[Lite vs Pro](tiers.md)**. Short version: Lite detects with five
core checks; Pro adds eleven more checks, every fix, profiles, batch
fixing, and CSV export.
