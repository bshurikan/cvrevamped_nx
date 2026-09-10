<div align="center">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/45d72613-d8f7-4922-a78d-533f743aacf0" /> 
</div>

# Castlevania ReVamped - Nintendo Switch Port

Unofficial homebrew port of **Castlevania ReVamped** (Lv.4 Games, GameMaker Studio 2 YYC) for modded Nintendo Switch.

This release includes everything you need to play on Switch: the **homebrew wrapper**, **prep tools**, and a **Switch-patched Android APK** (YYC) with correct controls, no touch overlay, and full-speed performance.

## Installation

Download **both** release assets from [GitHub Releases](https://github.com/bshurikan/cvrevamped_nx/releases):

1. **`cvrevamped-switch-release.zip`** - wrapper + config + tools  
2. **`CastlevaniaReVamped-switch.apk`** - Switch-patched YYC build (required; do not substitute a stock Android APK)

---

### Method A - Automatic (Windows prep script)

Best if you are on Windows and the script runs successfully.

1. Extract **`cvrevamped-switch-release.zip`**.
2. Double-click **`tools/Prepare SD Card.bat`**.
3. Select **`CastlevaniaReVamped-switch.apk`** when prompted.
4. Copy the generated **`sd_card/cvrevamped_nx/`** folder to your SD card as **`switch/cvrevamped_nx/`**.

> If Method A doesn't work for you use **Method B** instead. 

---

### Method B - Manual (any OS)

1. Extract **`cvrevamped-switch-release.zip`**. You should have a **`cvrevamped_nx/`** folder with at least:
   - `cvrevamped_nx.nro`
   - `config.txt`
   - `gamecontrollerdb.txt`
   - `sdl2.txt`
2. Copy **`CastlevaniaReVamped-switch.apk`** into **`cvrevamped_nx/`** and rename to **`game.apk`**.
4. Open **`game.apk`** with any zip tool (7-Zip, WinRAR, macOS Archive Utility, etc.) and extract:
   - **`lib/arm64-v8a/libyoyo.so`** → place as **`cvrevamped_nx/libyoyo.so`**
   - The entire **`assets/`** folder → place as **`cvrevamped_nx/assets/`**
5. Copy **`sdl2.txt`** from the release folder into **`cvrevamped_nx/assets/sdl2.txt`** as well (overwrite if the APK already has one). This is required for Switch controls on the YYC build.
6. Confirm **`config.txt`** has **`input_profile 1`** (shipped default).
7. Copy the finished **`cvrevamped_nx/`** folder to your SD card as **`switch/cvrevamped_nx/`**.

Final layout:

```
sdmc:/switch/cvrevamped_nx/
├── cvrevamped_nx.nro
├── config.txt
├── gamecontrollerdb.txt
├── sdl2.txt
├── game.apk                 ← renamed Switch APK
├── libyoyo.so               ← from APK lib/arm64-v8a/
└── assets/                  ← from APK assets/ (+ sdl2.txt overwrite)
    ├── game.droid
    ├── sdl2.txt
    └── ...
```

## What's in the release

| File | What it is |
|------|------------|
| `cvrevamped-switch-release.zip` | Wrapper (`cvrevamped_nx.nro`), config, `gamecontrollerdb.txt`, prep tools |
| `CastlevaniaReVamped-switch.apk` | Switch-patched game (YYC) — B jump, A subweapon, axis-6 map, no touch UI |

The prep tool unpacks the APK into the layout the wrapper expects (`game.apk`, `libyoyo.so`, `assets/`) and sets `input_profile 1` automatically.

### Source

Switch-specific GML patches and the APK build recipe live in the fork:

- [cvrevamped-switch](https://github.com/bshurikan/cvrevamped-switch) (`switch-port` branch)

Base game: [Lv.4 Castlevania ReVamped OSE](https://github.com/LSDonkeyKong/Castlevania-ReVamped-Open-Source-Edition)

## SD card layout

```
sdmc:/switch/cvrevamped_nx/
  cvrevamped_nx.nro       ← wrapper (from release)
  config.txt              ← wrapper
  sdl2.txt                ← wrapper (YYC gamepad map)
  gamecontrollerdb.txt    ← wrapper
  game.apk                ← from Switch APK via prep tool
  libyoyo.so              ← from Switch APK via prep tool
  assets/                 ← from Switch APK via prep tool
```

## Controls

| Switch | Action |
|--------|--------|
| D-pad / Left stick | Move |
| **A** | Accept (menus) / **Subweapon** (gameplay) |
| **B** | Jump (gameplay) / Cancel (menus) |
| **Y** | Attack |
| **X** | Weapons / swap |
| **L / ZL** | Aim lock |
| **R / ZR** | Dash |
| **Minus (−)** | Map |
| **Plus (+)** | Pause |
| **L3 + R3** | **NX Options** menu |

Touch controls are disabled on Switch — physical gamepad only.

<img width="800" alt="Castlevania_ReVamped_20260910_033700_00" src="https://github.com/user-attachments/assets/59b297c7-b427-434c-a3a3-2da2ae0da454" />

## Configuration (`config.txt`)

| Key | Default | Notes |
|-----|---------|-------|
| `vsync` | `0` | Keep off — vsync hurts frame pacing |
| `show_fps` | `0` | Overlay off by default |
| `docked_clocks` | `1` | Higher clocks when docked |
| `input_profile` | `1` | YYC / Input 10 (set by prep tool) |
| `hide_touch` | `1` | Blocks Switch touchscreen from reaching the game |
| `screen_width/height` | `-1` | Auto (720p handheld, 1080p docked) |

In-game: press **L3 + R3** to open **NX Options**. Toggle FPS / coords / VSync / clocks / resolution, unstick, and warps - changes write to `config.txt`. Resolution needs an app restart.

## Performance

This port uses a **YYC** build at full native speed on Switch — same class of performance as the [MPO YYC port](https://github.com/bshurikan/mpo_nx). Expect smooth 60 fps in most areas; heavy rooms may dip slightly.

## Building from source

Requires [devkitPro](https://devkitpro.org/). See [BUILD.md](BUILD.md).

```bash
pacman -S --needed switch-dev switch-sdl2 switch-mesa switch-libdrm_nouveau switch-freetype switch-libpng switch-ffmpeg
make
```

Produces `cvrevamped_nx.nro`.

## Credits

- Wrapper based on the Android GameMaker loader pattern (How Many Dudes / fgsfds, Andy Nguyen) and the [MPO Switch](https://github.com/bshurikan/mpo_nx) project.
- **Castlevania ReVamped** by Lv.4 Games (fan project). Not affiliated with Lv.4, Nintendo, Konami, or YoYo Games.
- Switch input patches: B jump, A subweapon, Minus map via axis 6, touch overlay removed.
- YYC base: [xan1242/cvrevamped-optimized](https://github.com/xan1242/cvrevamped-optimized).

## License

Wrapper source: [MIT](LICENSE). Game assets and `libyoyo.so` are distributed under the community APK release; retain Lv.4 credits per the [OSE license](https://github.com/LSDonkeyKong/Castlevania-ReVamped-Open-Source-Edition).



