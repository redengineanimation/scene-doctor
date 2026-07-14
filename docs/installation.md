# Installation

Blender 4.2 or newer.

!!! warning "Install the zip — don't hand-copy it"
    Always install the **zip file**. Do not unzip it into Blender's
    add-on folders manually — a hand-placed folder has no Uninstall
    button and can misbehave.

## Install

=== "Drag & drop"

    1. Drag `scene_doctor-x.x.x.zip` onto the Blender window.
    2. Confirm the install prompt.
    3. The add-on enables automatically.

=== "From Preferences"

    1. **Edit → Preferences → Add-ons**.
    2. Top-right **⌄** dropdown → **Install from Disk…**
    3. Select `scene_doctor-x.x.x.zip`.
    4. Tick the **Scene Doctor** checkbox to enable it.

Open the panel: in the 3D Viewport press ++n++ to show the sidebar, then
click the **Doctor** tab.

## Update

Install the newer zip the same way, over the top. Blender replaces the
previous version.

## Uninstall

1. **Edit → Preferences → Add-ons**.
2. Find **Scene Doctor**, click the **⌄** expand arrow on its row.
3. Click **Uninstall**.

### No Uninstall button?

That means the add-on was placed on disk manually instead of installed
from the zip. Remove it by hand:

1. Untick it in Preferences to disable.
2. **Quit Blender.**
3. Delete this folder (`<version>` = your Blender version, e.g. `4.5`):

    | OS | Path |
    |----|------|
    | Windows | `%APPDATA%\Blender Foundation\Blender\<version>\extensions\user_default\scene_doctor` |
    | macOS | `~/Library/Application Support/Blender/<version>/extensions/user_default/scene_doctor` |
    | Linux | `~/.config/blender/<version>/extensions/user_default/scene_doctor` |

4. Relaunch Blender.

## License key

If you have a license key, enter it in the add-on's Preferences. Scene
Doctor works fully without it — the key is only for support and update
eligibility.
