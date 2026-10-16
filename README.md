<div align="center">
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/45d72613-d8f7-4922-a78d-533f743aacf0" /> 

# Castlevania ReVamped
### Unofficial Nintendo Switch Homebrew Port

*A wrapper/port of the acclaimed [fan game by Lv.4 Games](https://www.reddit.com/r/castlevania/comments/1bap416/castlevania_revamped_new_fan_game_out_now/) (GameMaker Studio).*
</div>

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

> [!NOTE]
> Touch controls are disabled on Switch - physical gamepad only.

<br>
<img width="700" alt="image" src="https://github.com/user-attachments/assets/295871a6-d09e-4530-9f7e-3e09d79c436d" />

> [!TIP]
> Press **L3 + R3** to open **NX Options**. Toggle Cheats / Visuals & Performance options / QOL Mods and more (changes written to `config.txt`).

## 🔧 Configuration

| Key | Default | Notes |
|-----|---------|-------|
| `show_fps` | `1` | On-screen FPS |
| `vsync` | `1` | Harmless |
| `hide_touch` | `1` | Hides touch overlay on switch |
| `docked_clocks` | `1` | Higher GPU in handheld when allowed |
| `aspect_ratio` | `1` | 0=Original 4:3 (letterboxed) 1=Stretched 16:9 (distorted) |
| `handheld_docked` | `1` | Force official docked 768 MHz while undocked |
| `rumble_strength` | `50` | Adjust strength of controller rumble |
| `menu_bg` / `menu_transparency` | Falling Embers / 3 | NX Options backdrop |
| `reveal_breakables` | `0` | reveal breakable tiles when in range |
| `map_unretrieved` | `0` | shows cyan markers on tiles with unretrieved items |
| `whip_rstick` | `0` | quick toggle whips with right stick or cycle with R3 |
| `input_profile` | `1` | YYC / Input 10 |

## 🌡 Performance

This port uses a **YYC** build at full native speed on Switch — same class of performance as the [MPO YYC port](https://github.com/bshurikan/mpo_nx). Expect smooth 60 fps in most areas; heavy rooms may dip slightly.

## 👾 Credits

- **Castlevania ReVamped** is by [Lv.4 Games](https://github.com/LostDonkeyKong/Castlevania-ReVamped-Open-Source-Edition). Per OSE terms, original credits are retained below.
- Wrapper based on the Android GameMaker loader pattern (How Many Dudes / fgsfds, Andy Nguyen) and [MPO Switch](https://github.com/bshurikan/mpo_nx)
- Game APK: Android **YYC** export of [Lv.4 OSE](https://github.com/LostDonkeyKong/Castlevania-ReVamped-Open-Source-Edition) with Switch-specific patches ([cvrevamped-switch](https://github.com/bshurikan/cvrevamped-switch))

Special Thanks to: 
 - [xan1242/cvrevamped-optimized](https://github.com/xan1242/cvrevamped-optimized) for an early YYC Android starting point (this project moved to a direct OSE source export when that path proved hard to iterate on)
- Thanks [eboody's Android OSE fork](https://github.com/eboody/Castlevania-ReVamped-Open-Source-Edition) for community Android porting inspiration

<table>
  <thead>
    <tr><th colspan="2" align="left">Castlevania ReVamped Original Credits (OSE)</th></tr>
  </thead>
  <tbody>
    <tr><td><strong>Game design &amp; production</strong></td><td>William “Lv.4 WALL” Perez</td></tr>
    <tr><td><strong>Flavor text</strong></td><td>Ivan Perez</td></tr>
    <tr><td><strong>Map &amp; layout</strong></td><td>Lv.4 WALL</td></tr>
    <tr><td><strong>Graphic artists</strong></td><td>Hansungkee · ZeroSaberGreen · Murphmario · Mister Mike · Badbatman3 · SmithyGCN · Lexou Duck · Stardust Nova</td></tr>
    <tr><td><strong>Musicians</strong></td><td>Raspberry Oatshark · Shimoine</td></tr>
    <tr><td><strong>Special thanks</strong></td><td>WarMachine Studios · Mr. P’s Castlevania Realm · The Castlevania Dungeon</td></tr>
    <tr><td><strong>Testing</strong></td><td>Jack Beauchamp · Marilyn Hannan · Max Morrone · Ivan Perez · Robert “subledger” Hyatt · JupiterClimb · Spriven</td></tr>
    <tr><td colspan="2" align="center"><em>All other assets are derived work of Konami</em><br><strong>Presented by Lv.4 GAMES, 2024</strong></td></tr>
  </tbody>
</table>

## License

Wrapper source: [MIT](LICENSE). Game assets and `libyoyo.so` are distributed under the community APK release; retain Lv.4 credits per the [OSE license](https://github.com/LSDonkeyKong/Castlevania-ReVamped-Open-Source-Edition).
