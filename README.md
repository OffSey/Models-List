- **Want to see image previews?** Visit [https://my.xionshield.eu/models](https://my.xionshield.eu/models)

---

# FiveM Models Browser

A clean, single-file web tool to browse all **FiveM / GTA V** registered models - vehicles, peds, weapons, objects and explosions - with a built-in **JOAAT Hash Converter**.

Built by **OffSey** for [XionShield](https://xionshield.eu).

---

## Features

- Browse **all FiveM registered models** from a JSON dataset
- Filter by category - Vehicles, Peds, Weapons, Objects, Explosions
- Search by **name**, **model string** or **hash**
- Paginated grid with **image previews** where available
- Click any card to open a **detailed modal** with all hash values
- Built-in **JOAAT Hash Converter** (Signed, Unsigned, Hex)
- Shortcut `Ctrl+H` to open the hash converter instantly
- "Search in models" button inside the hash converter
- Animated particle background matching the XionShield design
- No framework dependencies - pure HTML, CSS & JS

---

## Usage

1. Clone or download this repository
2. Make sure `models.json` is present (see [Data Format](#data-format) below)
3. Open `index.html` in any modern browser

or: 

1. Go to: https://offsey.github.io/Models-List/ or [https://my.xionshield.eu/models](https://my.xionshield.eu/models)

---

## Data Format

The page loads `models.json` from:

```
https://raw.githubusercontent.com/OffSey/FiveM-Models/main/models.json
```

Expected structure:

```json
{
  "vehicles": {
    "Adder": {
      "model": "adder",
      "hash": "-1629920505",
      "intHash": "2665046791",
      "hexHash": "0x9F29ABCF"
    }
  },
  "weapons": { ... },
  "peds":    { ... },
  "objects": { ... },
  "explosions": { ... }
}
```

---

## Image Previews

Images are loaded from a CDN you configure yourself.

> **You must replace the placeholder URLs before deploying.**
> Open `index.html` and go to lines **657-660** inside the `imgSrc()` function.

```js
// line 657
if (model.cat === "weapons")  return `https://YOURURL/data/weapons/${model.name}.png`;
// line 658
if (model.cat === "vehicles") return `https://YOURURL/data/vehicles/${n}.png`;
// line 659
if (model.cat === "peds")     return `https://YOURURL/data/peds/${n}.webp`;
// line 660
if (model.cat === "objects")  return `https://YOURURL/data/objects/${n}.png`;
```

Replace `YOURURL` with your own CDN base domain. If you have no image hosting, set each line to `return null;` - a "No preview available" placeholder will be shown instead.

| Category | Format | Example path |
|---|---|---|
| Weapons | `.png` | `/data/weapons/weapon_pistol.png` |
| Vehicles | `.png` | `/data/vehicles/adder.png` |
| Peds | `.webp` | `/data/peds/mp_m_freemode_01.webp` |
| Objects | `.png` | `/data/objects/prop_bench_01a.png` |

---

## JOAAT Hash Converter

| Format | Example (`adder`) |
|---|---|
| Signed (Int32) | `-1629920505` |
| Unsigned (UInt32) | `2665046791` |
| Hexadecimal | `0x9F29ABCF` |

The input string is automatically lowercased before hashing, matching FiveM's internal behavior.

---

## What is JOAAT?

**Jenkins One-at-a-Time (JOAAT)** is a hash function used by Rockstar Games in GTA V and FiveM to identify game entities such as vehicle models, weapon names, peds, and more.

---

## Credits

Created by **OffSey** for [xionshield.eu](https://xionshield.eu).
The tool is fully open-source and available for everyone to use, modify, and integrate into their own projects.
