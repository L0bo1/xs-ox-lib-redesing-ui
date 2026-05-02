# xs-ox-lib-redesing-ui
redesing for ox-lib
# XS Premium UI for ox_lib

Dark premium visual redesign for the FiveM `ox_lib` NUI.

This package keeps the original `ox_lib` logic, exports, events, callbacks, NUI payloads, and script compatibility. The changes are visual only: solid black panels, red borders, subtle animated red glow, local Teko font, and refreshed styling for the main UI modules.

> This is not an official Overextended release.

## Original Project

- Original project: https://github.com/overextended/ox_lib
- Original authors: Overextended
- Original documentation: https://overextended.dev/ox_lib

## What Changed

- Solid black UI backgrounds.
- Red borders and smooth red glow.
- Local `Teko-Medium.otf` font.
- Redesigned context menus.
- Redesigned list menus.
- Redesigned input dialogs and alert dialogs.
- Redesigned notifications.
- Redesigned progress bar and progress circle.
- Redesigned TextUI.
- Redesigned radial menu styling.
- No Lua API changes.
- No exports, events, callbacks, or payload names changed.

## Installation

1. Stop your server.
2. Back up your current `ox_lib`.
3. Replace your existing `ox_lib` folder with the included `ox_lib` folder.
4. Make sure your `server.cfg` has:

```txt
ensure ox_lib
```

5. Start your server or run:

```txt
restart ox_lib
```

## Important

The resource folder must still be named:

```txt
ox_lib
```

Many FiveM scripts depend on `@ox_lib/init.lua`, so renaming the resource can break compatibility.

## Testing Commands

Use these in a temporary client-side resource that includes:

```lua
shared_script '@ox_lib/init.lua'
```

### Context

```lua
RegisterCommand('testcontext', function()
    lib.registerContext({
        id = 'test_xs_context',
        title = 'XS Premium Context',
        options = {
            {
                title = 'Buy Clothing - $100',
                description = 'Pick from a wide range of items to wear',
                icon = 'shirt'
            },
            {
                title = 'Change Outfit',
                description = 'Pick from any of your currently saved outfits',
                icon = 'user'
            }
        }
    })

    lib.showContext('test_xs_context')
end)
```

### Input Dialog

```lua
RegisterCommand('testinput', function()
    lib.inputDialog('XS Input Dialog', {
        { type = 'input', label = 'Name', placeholder = 'Type here...' },
        { type = 'number', label = 'Amount', default = 1 },
        { type = 'checkbox', label = 'Confirm' },
        { type = 'slider', label = 'Level', min = 0, max = 100, default = 50 },
        { type = 'textarea', label = 'Notes', placeholder = 'Long text...' }
    })
end)
```

### Notification

```lua
RegisterCommand('testnotify', function()
    lib.notify({
        title = 'XS Notify',
        description = 'Testing the premium dark redesign',
        type = 'success',
        duration = 5000,
        position = 'top-right'
    })
end)
```

### Progress

```lua
RegisterCommand('testprogress', function()
    lib.progressBar({
        duration = 5000,
        label = 'Testing progress bar',
        canCancel = true
    })
end)

RegisterCommand('testcircle', function()
    lib.progressCircle({
        duration = 5000,
        label = 'Testing progress circle',
        position = 'bottom',
        canCancel = true
    })
end)
```

### TextUI

```lua
RegisterCommand('testtextui', function()
    lib.showTextUI('[E] Clothing Store - Price: $100', {
        position = 'right-center',
        icon = 'shirt'
    })

    Wait(5000)
    lib.hideTextUI()
end)
```

## Rebuilding the Web UI

If you edit the web source, rebuild from:

```txt
ox_lib/web
```

Recommended:

```powershell
bun run build
```

If Bun is not installed, the equivalent project script can be run with:

```powershell
npm run build
```

## License

This package preserves the original `ox_lib` LGPL-3.0-or-later license and notices.

Teko font files are distributed under the SIL Open Font License 1.1. See `THIRD_PARTY_NOTICES.md` and `OFL-1.1.txt`.

