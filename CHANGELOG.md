# Changelog

Impact Atlas is versioned to match the version published to the Figma Community, which Figma assigns.
A design system update is committed without a release (`build: ds-core vX.Y.Z`) and ships with the next version published.

(Some earlier entries use decimals like `v5.1` for repo-only releases. That scheme was retired on 22 July 2026.)

### Not released yet

- The scan depth choice is built from the design system's radio, so it looks and behaves like every other radio in the design system.
- Every button that shows only an icon now has a name screen readers announce (Change scan type, Rescan, Focus on canvas, Copy report to clipboard, Graph view, List view, Place affected components on canvas), not only a tooltip.
- The tokens and components list is the design system's panel.
- Token and component names in the lists use the design system's line height, as in the design.
- A screen reader now announces the scan depth (Local, Extended or Full Scan) when it changes.

### v6 · 1 August 2026

- New feature: Place all components affected by a token on the canvas for easier review.
- Added a library icon to distinguish external items from local ones at a glance.
- Fixed an issue where local tokens were incorrectly labelled as external.
- Improved reopening speed and refined search.

### v5 · 22 July 2026
Published to Figma Community.
- Scan-depth radio rings are slightly heavier, matching the connector line.
- Scan-depth radio dots now line up with their labels.
- A chain with only alias tokens and no components keeps its column width, so
  nodes no longer stretch to fill the panel.
- Section dividers are 2px taller, matching a spacing change in the design system.
- The "Scanned …" bar and its rescan button now show after a local scan too.
  They previously only appeared once a canvas scan had run, so opening the
  plugin in a fresh file left you with no visible way to re-run it.
- Empty state uses the design system's object icons, and its icon colour now
  matches the DS in light mode (was too dark).
- Nodes that recede when another is selected use the real disabled tokens
  instead of being faded with opacity, so their colours match the design.
- Action buttons inside a node (focus / go to) keep their own colour rather
  than being dimmed along with the node.
- Disabled label and icon colours corrected against the DS.

Landed since publishing, and going out with the next Community release:
- Local variables are no longer mislabelled as coming from an external library.
  Figma's local-variable listing occasionally omits a genuinely local variable;
  when another local token aliased it, the plugin fetched it and marked it remote,
  so a real local token (for example advanced/buttonPrimary/border/top) showed the
  library icon and lost its canvas focus. It now trusts Figma's own remote flag
  and treats these recovered variables as local.
- Place affected components on canvas. From a token, one action drops live
  instances of every component it affects into a named, transparent Section on a
  plugin-owned "Impact Atlas Previews" page, so nothing lands on top of your work
  and no colour is added to your document. The Section is titled with the token and
  timestamp; repeat placements sit side by side. Because they're instances, editing
  the token updates them in place.
- Library components are included too: when a token affects a component from an
  external library, its live instance appears on the board alongside the rest.
  Library components are marked with a small library icon (no canvas focus, since
  their master lives in another file).
- Renaming a variable in a library file no longer makes it show up twice. Library
  variables live in another file, so the plugin had no way of knowing when one was
  renamed, deleted or republished there, so its cached copy still looked current. It
  now re-checks each cached library variable against the live library, takes the new
  name, and drops any that were deleted. If the library can't be reached it keeps
  what it had rather than clearing your results.
- Failures are reported as a toast in the corner instead of a red bar wedged into
  the panel. The old bar stayed on screen after the problem had passed.
- The search field's border was too dim in dark mode: it was using the divider
  line colour rather than the input colour. The two are identical in light mode,
  which is why it only ever looked wrong in dark.
- The action bar now uses its own design-system colours and gains a bottom rule,
  matching the design system. It had been borrowing the colour of Figma's own
  plugin titlebar, which has since diverged.
- The header of the library detail panel is now the design system's status bar,
  the same component the main status bar already used. It was a hand-built
  near-copy at its own size, so it is taller now and its divider is the right
  colour.
- Spacing throughout was snapped onto the design system's scale. A lot of it had
  been typed as loose numbers (6px, 10px, 7px) that exist nowhere in the system,
  so gaps and paddings now line up with the rest of the plugin.
- The level and priority dots take their size from a new design-system value
  instead of a fixed one, so they follow the system if it changes.
- Deleted components are no longer shown as coming from an external library. A
  component deleted while its instances stayed on the canvas still resolved through
  those instances, so it appeared with the library icon; it is now recognised as
  gone rather than remote.
- The library icon on component and token rows is no longer dimmed. Inside a list
  row it was picking up the row's muted icon colour instead of its own, so it read
  darker than it should.
- The "Place on canvas" button sits next to the "Affected components" heading
  instead of at the far right of the row, matching the design system.
- The info and library icons were redrawn in the design system; the plugin now
  matches (the info icon is a solid mark rather than an outline).
- The scan-type dialog now uses the design system's shared modal shell (overlay,
  card, title, footer and the open/close animation), supplying only its own scan
  options as the slot content. The shell moved out of the plugin into the design
  system so every plugin renders the same modal; nothing changed on screen.

### v4 · 17 July 2026
Published to Figma Community.
