# CadCraft add-ons

Add-ons are features you can switch on or off in the [CadCraft](https://getcadcraft.com) apps. An add-on extends an app
(CadCraft, BimCraft, ModelCraft and the rest of the eight); it is never an app of its own.

> **Status:** the add-on API (CadCraft 1.0, the shared API 1.0 in the other apps) and the directory exist in the CadCraft
> lab. The directory at getcadcraft.com/addons is not open to the public yet, and uploads are open to the CadCraft team
> only for now.

## What is in this repo

- `docs/GUIDE.md`: how to write one: the folder, `addon.json`, the API, objects of your own, data in DWG and DXF,
  testing, packing, review and signing.
- `template/`: a small working add-on (numbered note bubbles in CadCraft) to copy, with its own tests,
  `npm test` (a stand-in for the app, no dependencies) and `npm run pack` (the zip you upload).
- `examples/outline/`: a small, complete example for 2D work: a closed outline that carries a tag, with a grip on every
  corner, the tag in the Properties panel, area and perimeter, and an exporter (CSV). It saves in DWG and DXF with nothing
  extra to write. Start here for cutting, sign-making or space-planning add-ons. Same `npm test` and `npm run pack`.

- `docs/LAYOUTS.md`: **make your own workspace layout** — a data-only add-on of kind `workspace` (`<name>.ccworkspace.json`) that arranges
  the apps' building blocks (ribbon, toolbox, info box, palettes, view tabs…) in every app; `examples/layout-drawing-first/` is one, with
  its test.

`tools/` is the same in the template and in each code example (the layout example has its own, smaller tools).

## BimCraft visual-script add-on (fit check)

The BimCraft visual scripting add-on is a good **reference example**, but not a drop-in package for this repo's template:

- Source: `bimcraft/app/addons/visual-script/` in the BimCraft repo.
- Manifest/API: it targets BimCraft add-on API `1.1` with permissions `draw` and `model`.
- Scope: it depends on BimCraft model-edit APIs (`api.draw`, `api.model`) and node-graph behavior that CadCraft 1.0-only
  examples here do not expose.

So it is "suitable" to include as a documented example and design reference, but it should stay maintained in the
BimCraft repo where those APIs live.

## How this repo relates to the other CadCraft repos

- `bimcraft`: ships app-owned add-ons used by BimCraft itself (including `visual-script`).
- `studio`: packs browser editions from app repos into one suite folder for CadCraft Studio.
- `desktop-shell`: wraps one app edition (or a Studio suite) as desktop installers.
- `language-packs`: translation layers consumed by apps, Studio and add-ons.

## Start

```sh
cp -r template my-addon && cd my-addon
# change addon.json: id, name, author
npm test
npm run pack
```

## License

Apache-2.0 (`LICENSE`). Your own add-on may use any license the directory can sign: Apache-2.0, MIT, BSD-2-Clause,
BSD-3-Clause, ISC, 0BSD, Unlicense, Zlib or CC0-1.0.
