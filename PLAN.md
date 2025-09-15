# 🎮 Persona 5 Royal Wallpaper App — FULL Project Summary & To-Dos

## 1. Project Overview

You’re building a macOS wallpaper app based on Persona 5 Royal, featuring:

- Multiple iconic locations/scenes from the game  
- Character selection with multiple characters layered into scenes  
- Time-based variations for backgrounds (morning, evening, night)  
- Ambient micro-animations (coffee steam, light flickers) on otherwise static wallpapers  
- Dynamic wallpaper export in HEIC format with multiple frames/time slots  
- Random scene/character presets and a number selector for randomization  
- A modular, config-driven architecture for scalability  

---

## 2. Characters & Links

| Character           | Link                                                                 |
|---------------------|----------------------------------------------------------------------|
| Ren Amamiya         | https://megamitensei.fandom.com/wiki/Ren_Amamiya                    |
| Ryuji Sakamoto      | https://megamitensei.fandom.com/wiki/Ryuji_Sakamoto                 |
| Ann Takamaki        | https://megamitensei.fandom.com/wiki/Ann_Takamaki                   |
| Morgana             | https://megamitensei.fandom.com/wiki/Morgana                        |
| Yusuke Kitagawa     | https://megamitensei.fandom.com/wiki/Yusuke_Kitagawa                |
| Makoto Niijima      | https://megamitensei.fandom.com/wiki/Makoto_Niijima                 |
| Futaba Sakura       | https://megamitensei.fandom.com/wiki/Futaba_Sakura                  |
| Haru Okumura        | https://megamitensei.fandom.com/wiki/Haru_Okumura                   |
| Goro Akechi         | https://megamitensei.fandom.com/wiki/Goro_Akechi                    |
| Sumire Yoshizawa    | https://megamitensei.fandom.com/wiki/Sumire_Yoshizawa               |
| Igor                | https://megamitensei.fandom.com/wiki/Igor                           |
| Sojiro Sakura       | https://megamitensei.fandom.com/wiki/Sojiro_Sakura                  |
| Chihaya Mifune      | https://megamitensei.fandom.com/wiki/Chihaya_Mifune                 |
| Caroline & Justine  | https://megamitensei.fandom.com/wiki/Caroline_%26_Justine           |
| Munehisa Iwai       | https://megamitensei.fandom.com/wiki/Munehisa_Iwai                  |
| Tae Takemi          | https://megamitensei.fandom.com/wiki/Tae_Takemi                     |
| Sadayo Kawakami     | https://megamitensei.fandom.com/wiki/Sadayo_Kawakami                |
| Ichiko Ohya         | https://megamitensei.fandom.com/wiki/Ichiko_Ohya                    |
| Shinya Oda          | https://megamitensei.fandom.com/wiki/Shinya_Oda                     |
| Hifumi Togo         | https://megamitensei.fandom.com/wiki/Hifumi_Togo                    |
| Yuuki Mishima       | https://megamitensei.fandom.com/wiki/Yuuki_Mishima                  |
| Toranosuke Yoshida  | https://megamitensei.fandom.com/wiki/Toranosuke_Yoshida             |
| Sae Niijima         | https://megamitensei.fandom.com/wiki/Sae_Niijima                    |
| Takuto Maruki       | https://megamitensei.fandom.com/wiki/Takuto_Maruki                  |
| Jose                | https://megamitensei.fandom.com/wiki/Jose                           |

---

## 3. Scene & Folder Structure

```text
Scenes/
├── yongen-jaya/
│   ├── leblanc-coffee/
│   │   ├── door-view/
│   │   │   ├── breakfast/
│   │   │   │   ├── config.json
│   │   │   │   ├── assets/
│   │   │   │   │   ├── background.png
│   │   │   │   │   ├── steam.mov
│   │   │   │   │   ├── ren-amamiya.png
│   │   │   │   │   └── sojiro.png
│   │   │   ├── lesson/
│   │   ├── top-down-view/
│   │   └── thieves-den/
├── shibuya/
│   ├── shibuya-square/
│   │   ├── main-scene/
│   │   │   ├── morning/
│   │   │   ├── corrupted/
│   │   │   └── assets/
```

---

## 4. Scene Config (config.json)

Defines:

- Background image  
- Character layers & positions (with roles, e.g., “behind counter”)  
- Ambient FX overlays (video/sprite layers)  
- Allowed characters  
- Time-based variations (morning, noon, night)  
- Layer orders  

Example snippet:

```json
{
  "background": "background.png",
  "characters": [
    {
      "name": "sojiro",
      "position": {"x": 200, "y": 300},
      "role": "behind_counter",
      "asset": "sojiro.png"
    },
    {
      "name": "ren-amamiya",
      "position": {"x": 400, "y": 300},
      "role": "at_table",
      "asset": "ren-amamiya.png"
    }
  ],
  "ambientFX": [
    {
      "type": "video",
      "asset": "steam.mov",
      "position": {"x": 150, "y": 250}
    }
  ],
  "timeVariants": ["morning", "evening", "night"]
}
```

---

## 5. Technical Choices

| Topic               | Choice / Notes                                                                 |
|---------------------|---------------------------------------------------------------------------------|
| Output Format       | `.heic` dynamic wallpaper (with static + micro-animations)                      |
| Static/Animated Mix | Characters static; ambient FX (coffee steam, flickers) animated via overlays   |
| Asset Formats       | `.png` for images, `.mov` or `.webm` for small looping animations               |
| Framework           | SwiftUI + Core Animation + AVFoundation                                        |
| Scene Composition   | Layered stacking with config-driven positions                                  |
| Export              | Generate PNG frames + combine into `.heic` with time metadata                  |
| Randomization       | Random presets 0–99 + special Easter egg at 69                                 |
| Distribution        | `.app` packaged into `.dmg` installer                                           |
| Code Signing        | Optional for public release                                                    |

---

## 6. To-Do List

### ✅ Planning & Design

- [x] Define full character list & links  
- [x] Define scene folder & config structure  
- [x] Decide on output formats & technical approach  

### 🖼️ Asset Gathering

- [ ] Collect background images (HD, time variants)  
- [ ] Create / extract transparent character PNGs  
- [ ] Create ambient FX animations (e.g., steam loops)  
- [ ] Create city-wide background with day/night cycle  

### 💻 Development

#### Core Engine

- [ ] Build data model for scene config (Swift structs/classes)  
- [ ] Load scene config and assets in app  
- [ ] Implement layered scene renderer (background, characters, FX)  
- [ ] Implement character selection UI + multiple characters support  
- [ ] Implement preview screen with layered "next" effect  
- [ ] Implement time-based switching for backgrounds and FX  
- [ ] Implement random preset and number selector logic  

#### Exporting

- [ ] Export static PNG wallpapers  
- [ ] Export dynamic `.heic` wallpapers with multiple frames/time variants  
- [ ] Validate wallpaper appearance on macOS desktop  

### 📦 Packaging & Distribution

- [ ] Package `.app` using Xcode Archive  
- [ ] Create `.dmg` installer for distribution  
- [ ] (Optional) Code sign and notarize app for Gatekeeper  

### 🧪 Optional / Advanced

- [ ] Create a GUI drag-drop scene editor for easy scene building  
- [ ] Support `.mov` previews or animated wallpapers beyond `.heic`  
- [ ] Add sound effects (if desired)  
- [ ] Optimize ambient FX for performance & battery life  

---

## 7. Testing & Deployment

- Test all scenes locally in Xcode  
- Set exported wallpapers manually to desktop for QA  
- Build `.app` and test install/run on various macOS versions  
- Package `.dmg` and test install experience  
- If distributing widely, implement code signing and notarization  

---
