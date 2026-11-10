# Fermat Dark Reader

A personal forest-charcoal theme for the Fermat dashboard.
Dark Reader Dynamic mode handles the full site.
The small override file improves shared surfaces, controls, chart labels, and Fermat 2.0 pages.

## Install

1. Install the official [Dark Reader extension](https://darkreader.org/).
2. Open the Fermat dashboard.
3. Select Dynamic mode in Dark Reader.
4. Open More, All settings, Advanced, then Dev tools.
5. Select Dynamic Theme Editor, then Per Site Editor.
6. Search for `app.fermatcommerce.com`.
7. If no entry exists, select Create new fix.
8. Replace that entry with the complete contents of [dashboard.config](dashboard.config).
9. Select Apply.

The file includes production and Cloudflare preview domains.
The preview domain also matches its branch subdomains.
Other websites retain their existing Dark Reader settings.
Dark Reader's Import Settings button expects a different JSON format.

## Coverage

The site-level engine handles existing pages and new routes automatically.
The overrides cover:

- Shared Chakra backgrounds, text, borders, forms, dialogs, menus, and tooltips.
- Fermat 2.0 workspace dashboards, including metric cards, charts, tables, and filters.
- Workspace setup, briefs, investigations, automation panels, and artifact library chrome.
- Behavior Graph pages that use the shared `cg-tangent` tokens.
- Legacy app pages, including product funnels, analytics, media, and settings.
- Recharts axes, grids, and tooltips.

The overrides keep the existing fonts and layout.
They do not assign colors to chart series or status indicators.
Only the dark Fermat wordmark needs an explicit inversion.
Its selector uses the logo's SVG viewBox, not a generated class.
Images, video, canvas, and embedded previews receive no blanket inversion.
Sandboxed artifact documents can retain their original light design.
Their cards, headers, and controls still use the dark theme.
Replay pixels retain their original rendering.

The custom CSS applies only while Dark Reader reports dark mode.
Turning Dark Reader off removes the fix.

## Personal adjustments

The first rule defines the palette.
Primary and muted text pass WCAG AA against all three theme backgrounds.
The lowest measured ratio is 7.70:1.

Dark Reader generates the `--darkreader-bg--`, `--darkreader-text--`, and `--darkreader-border--` variables.
These overrides keep Chakra and the styled islands on the same palette.
The config uses semantic tokens, not generated Emotion class names.

For local Fermat development, replace the domain lines with `localhost:3000` in a separate site entry.
Remove that entry when the port serves another project.

## Update or remove

The repository stores the configuration; Dark Reader does not fetch updates from this repository.
Repeat the installation steps after changing the file.
To remove the custom theme, delete only the Fermat entry in Per Site Editor.
Dark Reader then resumes its default styling for Fermat.

No application deployment or dashboard code change is required.

Reference: [Dark Reader site fixes](https://github.com/darkreader/darkreader/blob/main/CONTRIBUTING.md#how-to-use-the-dev-tools).

## Visual checks

Checked in Chrome with the extension enabled:

- Collapsed and expanded sidebar.
- App home and Agent Workspaces.
- Product-funnel lists and legacy analytics cards, plots, and tables.
- Fermat 2.0 dashboard charts, legends, axes, and controls.
- Artifact cards, document chrome, and the sharing popover.

The token overrides also cover surfaces that use the same components.
This check does not claim that every route, feature flag, or customer document has identical rendering.
