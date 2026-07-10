# Test-driven Development for shared components

## AppShell
- Must have a `TopBar` and a `SideNav`.
- `TopBar` must have a burger menu that on trigger, pops up the `SideNav` from the left side of the screen.

## DataTable
- Must display data in rows.
- Must have sortable columns, row selection, sticky header, server-side pagination
- Must have the default empty state (e.g. we can't fetch the data right now, please try again).
- On row selection, pops up the DetailDrawer.

## DetailDrawer
- Must pop up on the right side.
- Basic layout: should have a title on the top, with content as the children right underneath.

## StatusBadge
- Accurately display the color based on the given value (e.g. StatusENUM.IN_PROGRESS = Yellow)
- Single source of truth for status colors (see §5) in this document: https://docs.google.com/document/d/1Z0xoWFNRV_T5TTVVEtQAGmInfKAlDmMRqkaqtH5gw1o/edit?tab=t.0

 
## Modal
- Have a curved border (with ratio of 0.01% of the screen width), and have a default gradient color (start with #000068, 15% opacity)
- Returns `children` as the content.
- Must have 2 buttons at the bottom corner by default, with the `Ok` button having customizable title and action.

## Card
- Have a curved border (with ratio of 0.01% of the screen width), and have a default gradient color (start with #000068, 15% opacity)
- Returns `children` as the content.


## Toast/Snackbar
- Have a curved border (with ratio of 0.01% of the screen width), and have a default SUCCESS variant
- Have 3 variants:
    - SUCCESS: Green Background, tickbox icon on the left, text content on the right, and close button.
    - WARNING: Yellow Background, warning icon on the left, text content on the right, and close button.
    - ERROR: Red Background, X icon on the left, text content on the right, and close button.