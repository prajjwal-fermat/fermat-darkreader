# Fermat Dark Reader

A personal neutral-charcoal theme for the Fermat dashboard.

<img width="1512" height="849" alt="image" src="https://github.com/user-attachments/assets/78737c13-d48c-4c32-9946-3157664dbeae" />


## Install

1. Install the official [Dark Reader extension](https://darkreader.org/).
2. Open the Fermat dashboard.
3. Select Dynamic mode in Dark Reader. (Inside the More tab)
<img width="1512" height="870" alt="image" src="https://github.com/user-attachments/assets/b11ee57a-9b67-438a-badf-aae4ddcff252" />

4. Inside More go to All settings, Advanced, then Dev tools.

5. Select Dynamic Theme Editor, then Per Site Editor.
<img width="794" height="600" alt="image" src="https://github.com/user-attachments/assets/ba50e2d4-186a-46a5-968c-d30a8866f468" />

6. Search for `app.fermatcommerce.com`.
7. If no entry exists, select Create new fix.
<img width="794" height="600" alt="image" src="https://github.com/user-attachments/assets/082564d5-53df-44a8-b6aa-8e138de41311" />

8. Replace that entry with the complete contents of [dashboard.config](dashboard.config).
9. Select Apply.

Now you will have dark theme for Fermat dashboard.
<img width="1512" height="849" alt="image" src="https://github.com/user-attachments/assets/56a91b82-b53e-44a6-94ca-6a0a8e994da2" />


The file includes production and Cloudflare preview domains.
The wildcard entry matches Cloudflare branch subdomains.
Other websites retain their existing Dark Reader settings.
Dark Reader's Import Settings button expects a different JSON format.

### Preserve published appearance

Templates and storefront previews must retain their original colors.
Dark Reader cannot reliably exclude a section of a page from Dynamic mode.
The safe fallback disables Dark Reader for the complete editor page, including its controls.
This also protects template galleries, the module library, and funnel review previews.

1. Open Dark Reader's Site list.
2. Select Not invert listed.
3. Add each line from [preview-exclusions.txt](preview-exclusions.txt) as a separate entry.
4. Keep any existing exclusions.
5. Reload an open editor after adding an exclusion.

These exclusions are separate extension settings.
Importing `dashboard.config` alone does not install them.
The list excludes editor routes without excluding analytics or dashboard routes.
The complete template editor stays light; this theme does not promise a dark editor around an unchanged preview.

Reference: [Dark Reader's section-exclusion limitation](https://github.com/darkreader/darkreader/issues/4144).

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
Sandboxed artifact documents retain their original design in the checked previews.
Their cards, headers, and controls still use the dark theme.
The custom CSS adds no filters to replay pixels.
Replay-player rendering still needs a separate visual check.

The custom CSS applies only while Dark Reader reports dark mode.
Turning Dark Reader off removes the fix.

## Personal adjustments

The first rule defines the palette.
Primary and muted text pass WCAG AA against all three theme backgrounds.
The lowest measured ratio is 7.32:1.

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
- A product-funnel template editor with Dark Reader excluded, including the original storefront colors.
- Existing investigation messages, artifact cards, and the composer.
- Workspace automation cards and the empty action-items page.
- Brand Settings details and media-library controls.
- Commerce Graph overview cards.

The remaining editor exclusions follow the application's route definitions.
They have not each received a visual check.
The media thumbnails, replay players, populated action items, and preview deployments remain unverified.

The token overrides also cover surfaces that use the same components.
This check does not claim that every route, feature flag, or customer document has identical rendering.
