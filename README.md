<div align="center">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/45d72613-d8f7-4922-a78d-533f743aacf0" /> 
</div>

# Castlevania ReVamped - Nintendo Switch Port

Unofficial homebrew port of **Castlevania ReVamped** (Lv.4 Games, GameMaker Studio 2 YYC) for modded Nintendo Switch.

This release includes everything you need to play on Switch: the **homebrew wrapper**, **prep tools**, and a **Switch-patched Android APK** (YYC) with correct controls, no touch overlay, and full-speed performance.

## Quick start (Windows)

1. Download the latest **[cvrevamped-switch-release.zip](https://github.com/bshurikan/cvrevamped_nx/releases)** from GitHub Releases.
2. Download **[CastlevaniaReVamped-switch.apk](https://github.com/bshurikan/cvrevamped_nx/releases)** from the same release (Switch-patched YYC build).
3. Extract the zip.
4. Double-click **`tools/Prepare SD Card.bat`**.
5. Select **`CastlevaniaReVamped-switch.apk`** when prompted.
6. Copy the generated **`sd_card/cvrevamped_nx/`** folder to your SD card as **`switch/cvrevamped_nx/`**.
7. Launch **`cvrevamped_nx.nro`** with **full RAM** (hold **R** while opening a title, or use a forwarder).

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

Touch controls are disabled on Switch — physical gamepad only.

## Configuration (`config.txt`)

| Key | Default | Notes |
|-----|---------|-------|
| `vsync` | `0` | Keep off — vsync hurts frame pacing |
| `show_fps` | `0` | Overlay off by default |
| `docked_clocks` | `1` | Higher clocks when docked |
| `input_profile` | `1` | YYC / Input 10 (set by prep tool) |
| `hide_touch` | `1` | Blocks Switch touchscreen from reaching the game |
| `screen_width/height` | `-1` | Auto (720p handheld, 1080p docked) |

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



