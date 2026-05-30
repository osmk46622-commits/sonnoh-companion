# 🐱 Sonnoh AI Companion - Bedrock Edition

A feature-rich AI cat companion addon for Minecraft Bedrock Edition inspired by the character design reference image.

## 📋 Features

### Character Design
- **Model**: Quarter player size cat with fluffy features
- **Appearance**: 
  - Narrow eyes (Yellow & Red color variants)
  - Pink round nose
  - Muzzle-shaped head
  - Long fluffy ears with animated flicking & twitches
  - White fur base
  - Red shirt with bell and collar
  - Animated cute and cat like, very affectionate

### Core Mechanics

#### 🎮 Taming System
- Feed Sonnoh with fish or salmon to tame
- Tamed Sonnoh follows the player
- Shows affection through purring and animations
- Hugging animation when successfully tamed

#### 💕 Care Mechanics
- **Petting**: Right-click to pet (triggers happiness)
- **Bed**: Sonnoh sleeps on a designated cat bed
- **Grooming**: Use comb item for care
- **Toys**: Interactive toys to maintain happiness
- **Health Bar**: Visual care status

#### 😊 Emotional States
- **Happy**: Purrs, ear flicks, affectionate (health > 15)
- **Neutral**: Normal behavior (health 10-15)
- **Sad**: Neglected state, ignores some commands (health 5-10)
- **Angry**: Low care, hisses and refuses commands (health < 5)

#### 🎨 Six Personality Variants

1. **White Sonnoh** - Calm, friendly, helpful
2. **Blue Sonnoh** - Curious, playful, asks questions
3. **Red Sonnoh** - Protective, serious, warns of danger
4. **Green Sonnoh** - Nature-loving, comments on plants/animals
5. **Yellow Sonnoh** - Energetic, excited, reacts to movement
6. **Black Sonnoh** - Shy, quiet, warms up slowly

### 💬 Conversation System

#### Triggers
- Typing "Sonnoh" in chat
- Right-clicking entity
- Feeding fish
- Petting
- Entering underground lab
- Low health events
- Nighttime
- Rain
- Nearby mobs

#### Response Types
- Short chat replies with emojis
- Emotes (head tilts, ear flicks, tail wags)
- Sounds (purrs, chirps, meows)
- Movement (walks to player, circles, sits)

### ⚡ Fast Response System
- Pre-cached dialogue lines
- Lightweight triggers
- No processing delays
- Fully local (no internet required)
- Instant responses to player actions

## 🔴 Special: Underground Lab Event

When the player enters the underground lab:
- Red Sonnoh becomes alert
- Environmental changes (lights flicker)
- Dialogue: "you found me... i've been waiting."
- Extra loyalty if tamed
- Watchful behavior if untamed

## 📦 Installation

### Method 1: Automatic Install
1. Download the `.mcaddon` file from releases
2. Double-click the file
3. Minecraft Bedrock will open and ask to add to world
4. Select your world and confirm

### Method 2: Manual Install
1. Extract `.mcaddon` to behavior and resource pack folders:
   - Windows: `%APPDATA%\.minecraft\development_behavior_packs\`
   - Mac: `~/Library/Application Support/minecraft/development_behavior_packs/`
2. Load in world settings

## 🎯 Usage

### Taming
```
1. Find a wild Sonnoh in the world
2. Hold fish or salmon in your hand
3. Right-click the Sonnoh to feed
4. Watch the taming animation
5. Sonnoh now follows you!
```

### Caring
```
- Pet: Right-click when not holding items
- Feed: Give fish regularly to maintain health
- Groom: Use comb on tamed Sonnoh
- Play: Interact with toys
- Sleep: Place bed and wait (night time)
```

### Interacting
```
- Chat: Type "Sonnoh" in chat to trigger dialogue
- Commands: Right-click for quick interactions
- Follow: Tamed Sonnoh automatically follows within 8 blocks
- Sit: Right-click again to make sit down
```

## 🔧 File Structure

```
sonnoh-companion/
├── manifest.json
├── README.md
├── SETUP.md
├── behavior_pack/
│   ├── entities/
│   │   └── sonnoh.json
│   ├── animations/
│   │   └── sonnoh.animation.json
│   ├── animation_controllers/
│   │   └── sonnoh.animation_controller.json
│   └── dialogue/
│       └── sonnoh_dialogue.json
└── resource_pack/
    ├── entity/
    │   └── sonnoh.json
    ├── models/
    │   └── entity/
    │       └── sonnoh.geo.json
    ├── render_controllers/
    │   └── sonnoh.render_controller.json
    └── textures/
        └── entity/
            ├── sonnoh_white.png
            ├── sonnoh_blue.png
            ├── sonnoh_red.png
            ├── sonnoh_green.png
            ├── sonnoh_yellow.png
            └── sonnoh_black.png
```

## 🎨 Customization

Edit these files to customize:
- **Emotions**: Modify `health` thresholds in animation controller
- **Dialogue**: Add/edit lines in `dialogue/sonnoh_dialogue.json`
- **Personality**: Adjust behavior in behavior pack entity file
- **Textures**: Replace PNG files with your own variants
- **Animations**: Modify animation timing and keyframes
- **Size**: Edit model geometry in `sonnoh.geo.json`

See **SETUP.md** for detailed customization guide.

## 🐾 Animation List

- `idle` - Standing still, looking around
- `walk` - Moving around with leg animation
- `sit` - Sitting position
- `pet` - Reacting to being petted
- `hug` - Hugging animation (taming complete)
- `ear_flick` - Ear twitching and flicking
- `sleep` - Sleeping on bed

## 📝 Version

- **Version**: 1.0.0
- **Format**: Bedrock `.mcaddon`
- **Min Engine**: 1.19.0+
- **Compatibility**: Minecraft Bedrock Edition (all platforms)

## 🎬 Events

### Entity Events
- `minecraft:entity_spawned` - Random variant assignment
- `sonnoh:on_tame` - Taming event (triggers hugging animation)
- `sonnoh:on_pet` - Petting event (triggers happiness)
- `sonnoh:on_neglect` - Neglect event (sad emotional state)
- `sonnoh:on_low_care` - Low care event (angry emotional state)

## 💡 Tips

1. **Multiple Variants**: Find different colored Sonnoh for different personalities
2. **Underground Lab**: Seek out the red variant in the lab for special interactions
3. **Happiness**: Keep Sonnoh happy by petting and feeding regularly
4. **Following**: Tamed Sonnoh will follow within 8 blocks
5. **Sleep**: Sonnoh needs rest - provide a bed and let them sleep at night
6. **Emotional Bonding**: Different variants respond differently to the same actions
7. **Protective Nature**: Red Sonnoh warns you of nearby mobs
8. **Curious Blue**: Will ask you questions about your activities

## 🐛 Troubleshooting

**Sonnoh not spawning?**
- Check that the addon is enabled in world settings
- Ensure you're in a suitable environment with enough space
- Try using `/summon sonnoh:sonnoh` command

**Sonnoh not responding?**
- Make sure the entity is tamed first (feed with fish)
- Check care levels (might be too neglected - pet and feed)
- Try right-clicking directly on the entity
- Ensure chat messages contain "Sonnoh" keyword

**Animations not playing?**
- Update to Minecraft 1.19.0 or higher
- Disable and re-enable the addon
- Check that resource pack is loaded after behavior pack

**Low FPS with Sonnoh?**
- Disable animation controller complexity
- Reduce number of spawned Sonnoh
- Lower render distance

## 🏆 Credits

**Inspired by**: Reference character design with orange/blue coloring, fluffy ears, and affectionate nature

**Created for**: Minecraft Bedrock Edition community

**Features**: AI dialogue, emotional states, care mechanics, taming system, multi-variant personalities

## 📄 License

This addon is provided as-is for personal use in Minecraft Bedrock Edition. Feel free to modify and customize for your own worlds.

---

**Enjoy your new fluffy companion! 🐱💕**

For detailed setup and customization instructions, see **SETUP.md**
