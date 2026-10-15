<div align="center">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/45d72613-d8f7-4922-a78d-533f743aacf0" /> 
</div>

# Castlevania ReVamped
### Unofficial Nintendo Switch Homebrew Port

A wrapper/port of the acclaimed [fan game by Lv.4 Games]([url](https://www.reddit.com/r/castlevania/comments/1bap416/castlevania_revamped_new_fan_game_out_now/)) (GameMaker Studio 2 YYC)*

## 💿 Installation

Download **both** release assets from the [Latest Release](https://github.com/bshurikan/cvrevamped_nx/releases):
1. **`cvrevamped-switch-release.zip`** - wrapper + config + tools  
2. **`CastlevaniaReVamped-switch.apk`** - Switch-patched YYC build (required; do not substitute a stock Android APK)

### Method A - Easy (Automatic prep script, Windows only)

1. Extract **`cvrevamped-switch-release.zip`**.
2. Double-click and run **`tools/Prepare SD Card.bat`**.
3. Select your **`CastlevaniaReVamped-switch.apk`** when prompted.
4. Copy the generated **`sd_card/cvrevamped_nx/`** folder to **`switch/cvrevamped_nx/`** on your SD card.

> If Method A doesn't work for you use **Method B** instead. 

---

### Method B - Moderate (Manual procedure, any OS)

1. Extract **`cvrevamped-switch-release.zip`**. You should have a **`cvrevamped_nx/`** folder with:
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

### Final layout:

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

## 🎮 Controls

| Switch | Action |
|--------|--------|
| **D-pad / Left stick** | Move |
| **A** | Accept (menus) / **Subweapon** (gameplay) |
| **B** | Jump (gameplay) / Cancel (menus) |
| **Y** | Attack |
| **X** | Weapons / swap |
| **L / ZL** | Aim lock |
| **R / ZR** | Dash |
| **Minus (−)** | Map |
| **Plus (+)** | Pause |
| **L3 + R3** | **NX Options** menu |
| **Right Stick** | Switch Whips |
| **R3** | Cycle Whips |

Touch controls are disabled on Switch - physical gamepad only.

<br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/295871a6-d09e-4530-9f7e-3e09d79c436d" />

> [!TIP]
> Press **L3 + R3** to open **NX Options**. Toggle FPS / Aspect Ratio / Mods and more (changes written to `config.txt`).

## 🔧 Configuration

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

## 👾 Credits

- Wrapper based on the Android GameMaker loader pattern (How Many Dudes / fgsfds, Andy Nguyen) and the [MPO Switch](https://github.com/bshurikan/mpo_nx) project.
- **Castlevania ReVamped** by Lv.4 Games (fan project). Not affiliated with Lv.4, Nintendo, Konami, or YoYo Games.
- Switch input patches: B jump, A subweapon, Minus map via axis 6, touch overlay removed.
- YYC base: [xan1242/cvrevamped-optimized](https://github.com/xan1242/cvrevamped-optimized).

## License

Wrapper source: [MIT](LICENSE). Game assets and `libyoyo.so` are distributed under the community APK release; retain Lv.4 credits per the [OSE license](https://github.com/LSDonkeyKong/Castlevania-ReVamped-Open-Source-Edition).
