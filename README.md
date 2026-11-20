# card-badge

The console badge shared by GizmoGoody Home Assistant cards. It prints a collapsed console group with the card icon, name, version, and "by GizmoGoody", and inside it the description, GitHub link, and issues link.

## Use in a card

Add the dependency to the card's `package.json`, pinned to a release tag:

```json
"dependencies": {
  "@gizmogoody/card-badge": "github:GizmoGoody/card-badge#v1.0.0"
}
```

Call it once, when the card registers:

```ts
import { printBadge } from '@gizmogoody/card-badge';

printBadge({
  icon: "👆🏼",
  name: "Touchpad Card",
  version: CARD_VERSION,
  description: "A tunable touchpad with 19 tap, linear, circular, and multi-touch interactions.",
  repo: "touchpad-card",
});
```

npm runs the `prepare` script when it installs this package from GitHub, which compiles it. The card's Rollup build then bundles it into the card file.

## Release a change

1. Change `src/index.ts` and bump `version` in `package.json`.
2. Publish a GitHub release with a matching tag, for example `v1.0.1`.
3. In each card, update the tag in `package.json` and refresh its lockfile.
