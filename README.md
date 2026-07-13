# Weissbart's Chauffeur v0.2.0-beta

Weissbart's Chauffeur helps UO Evolution players read SOS scrolls, plot them on the map, and pilot a boat toward the nearest SOS.

Created by Argus for Captain Weissbart, June 2026.

GitHub: [AirArgus/WeissbartChauffeur](https://github.com/AirArgus/WeissbartChauffeur)

## Requirements

- Ultima Online / UO Evolution installed.
- UOSteam running and logged in to the character you want to use.
- The UO Evolution folder must contain `map0.mul` and `radarcol.mul`.
- A key from Argus is required the first time you attach each character. Up to five character keys can be saved on one computer.

## First Run

1. Start UOSteam and log in to UO Evolution.
2. Start `WeissbartsChauffeur.exe`.
3. If prompted, select your UO Evolution folder. This is the folder that contains `map0.mul` and `radarcol.mul`.
4. Click `Attach to UO Client`.
5. Enter the key provided by Argus when prompted. If the account uses more than one character, each character needs its own key.
6. On first run, read the UOSteam SOS macro reminder. It appears once and is saved after you close it.
7. The first time you click `Auto Load SOS`, open one SOS gump when prompted and drag around the SOS gump area that contains the coordinate line. This is saved for future runs.

The program saves setup data here:

```text
C:\ProgramData\WeissbartsChauffeur\settings.json
```

## UOSteam SOS Macro

Create this macro in UOSteam and assign it to this hotkey. Press the Control key and the apostrophe key together; do not include the plus key.

```text
Control + apostrophe
```

Macro:

```text
clearignorelist
while @findtype 0x14ED 'any' 'backpack'
  useobject! 'found'
  ignoreobject 'found'
  pause 1500
endwhile
clearignorelist
```

Notes:

- SOS scroll item type is `0x14ED`.
- Opening the next SOS replaces the previous SOS gump.
- The first `Auto Load SOS` on a computer sets the SOS read area. Different game window sizes may need their own saved area.
- Keep SOS scrolls in your backpack before using `Auto Load SOS`.
- Do not use the mouse or close the gump while the program is reading SOS scrolls.
- Do not have anything over the upper-left corner of the UO client, as the program reads the SOS gump from that area.
- Wait for all SOS scrolls to open and disappear before clicking `Navigate to Nearest SOS`.
- Right-click the status window to copy the full status log for beta feedback.

## Loading SOS Scrolls

1. Put SOS scrolls in your backpack.
2. Click `Auto Load SOS`.
3. The program starts the UOSteam macro with Control + apostrophe.
4. Wait for the status box to show how many SOS scrolls were found.

The program watches the SOS gump and reads each distinct SOS view. If it reads zero scrolls, verify the UOSteam macro and hotkey.

## Navigating

1. Load one or more SOS scrolls.
2. Click `Navigate to Nearest SOS`.
3. The destination SOS is selected in the list.
4. Use `Pause Navigation` if you need to stop automation.
5. If the status box turns light red, the boat is boxed in or stuck. Steer the boat clear manually, then start navigation again.

The program sends boat commands through the UO client, including:

```text
forward
stop
turn left
turn right
one forward
one back
drop anchor
```

## Tips

- Keep the UO client restored, not minimized.
- Server lag can delay boat turns and movement reads.
- The navigator is best in open water and simple coast-following paths.
- Docks, tight corners, and heavy server lag may require manual steering.

## Grid Navigation Beta

Version `0.2.0-beta` adds an experimental navigation grid. The program divides the real UO map into `15 x 15` tile squares, marks each square as safe water, coast, or land, and saves the grid here:

```text
C:\ProgramData\WeissbartsChauffeur
```

When navigation starts, the program tries to plot a safe-water route from the boat to the selected SOS. The planned route is drawn as a blue dashed line on the map. If no safe route is found, the program falls back to the older reactive navigation behavior.

The grid route is still beta. If the boat is boxed in, the status box turns light red and asks the player to steer clear manually before starting navigation again.

## Key Generator

Argus can generate player keys.
