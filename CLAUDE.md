# Keyboard layout data

(Tags: keyboard, layout, overlay, KLE, keyboard-layout-editor)

Write the overlay as raw data for keyboard-layout-editor.com, matching the combinations in `kanata.kbd`.

- **Format**: Write the rows of an ANSI 60% board, ready to paste into the **Raw data** tab.
- **Legends**: Put the key name top-left, the hold modifiers bottom-left and the AltGr combination bottom-right.
- **Modifier names**: Abbreviate modifiers to ❖, C, A and S (Super, Ctrl, Alt and Shift), and join them with `+` in that order, e.g. `❖+S`, `C+A+S`.
- **Unicode**: Write every non-ASCII character as an HTML entity, e.g. `&#x2756;` for ❖ and `&#x2190;` for ←.
- **Colours**: Colour hold keys `#ffd28a`, AltGr-only keys `#a8d8ff`, disabled keys `#777777` and every other key `#cccccc`.
- **Disabled keys**: Label each disabled key with its abbreviation over `(off)`.
