# 🛠️ Sonnoh Companion - Setup & Customization Guide

## Initial Setup

### Prerequisites
- Minecraft Bedrock Edition (latest version, 1.19.0+)
- A text editor (VS Code recommended for JSON editing)
- Optional: Blockbench for editing models

### Step 1: Install the Addon

#### Windows
```
1. Download sonnoh-companion.mcaddon
2. Double-click the file
3. Minecraft Bedrock will open
4. Select your world to add the addon
5. Confirm and load world
```

#### Mac
```
1. Download sonnoh-companion.mcaddon
2. Right-click and select "Open With" > Minecraft
3. Select your world
4. Confirm and load world
```

#### Mobile (iOS/Android)
```
1. Download sonnoh-companion.mcaddon
2. Tap to open with Minecraft
3. Select your world
4. Confirm and load world
```

### Step 2: Verify Installation

1. Load your world
2. Run command: `/summon sonnoh:sonnoh`
3. You should see a white fluffy cat appear
4. Try right-clicking it to interact

### Step 3: Configure World Settings

1. **Behavior Packs**: Ensure "Sonnoh AI Companion" is enabled
2. **Resource Packs**: Ensure resource pack is above behavior pack
3. **Cheats**: Enable to use `/summon` commands (optional)

## Customization Guide

### 1. Edit Personality Traits

**File**: `behavior_pack/entities/sonnoh.json`

Find the component groups section and modify:

```json
"sonnoh:personality": "white"  // Change to: blue, red, green, yellow, or black
```

Each personality affects:
- Dialogue responses
- Behavior patterns
- Interaction responses
- Movement speed

### 2. Modify Dialogue

**File**: `behavior_pack/dialogue/sonnoh_dialogue.json`

Add new dialogue scenes:

```json
{
  "name": "sonnoh_custom_response",
  "participants": [
    {"name": "sonnoh"},
    {"name": "player"}
  ],
  "lines": [
    {
      "speaker": "sonnoh",
      "text": "your custom text here! 🐱"
    }
  ]
}
```

### 3. Adjust Care Thresholds

**File**: `behavior_pack/animation_controllers/sonnoh.animation_controller.json`

Modify health values for emotional states:

```json
"happy": "query.health > 15"                    // Happiness threshold
"sad": "query.health < 10 && query.health > 5"  // Sadness threshold
"angry": "query.health < 5"                     // Anger threshold
```

### 4. Edit Animations

**File**: `behavior_pack/animations/sonnoh.animation.json`

Example: Speed up walking animation

```json
"animation.sonnoh.walk": {
  "anim_time_update": "query.modified_move_speed * 1.5",  // Increased speed
  "loop": true,
  ...
}
```

### 5. Modify Model Geometry

**File**: `resource_pack/models/entity/sonnoh.geo.json`

Edit bone positions and sizes:

```json
"cubes": [
  {
    "origin": [-3, 8, -6],        // Position [X, Y, Z]
    "size": [6, 8, 10],           // Size [width, height, depth]
    "uv": [0, 0]                  // Texture coordinates
  }
]
```

**Size Formula**:
- Origin: Top-left corner position
- Size: Dimensions in blocks
- Example: `[6, 8, 10]` = 0.6 blocks wide × 0.8 tall × 1.0 deep

### 6. Create Custom Textures

**Files**: `resource_pack/textures/entity/sonnoh_*.png`

**Requirements**:
- **Resolution**: 64×64 pixels (standard for Bedrock)
- **Format**: PNG with transparency (RGBA)
- **Color Space**: RGB 8-bit

**Texture UV Mapping**:
```
Face:     0-24 (width) × 24-32 (height)
Body:     0-16 (width) × 0-18 (height)
Head:     0-24 (width) × 24-40 (height)
Ears:     40-56 (width) × 16-24 (height)
Legs:     40-56 (width) × 32-50 (height)
Tail:     56-64 (width) × 16-24 (height)
Bell:     56-64 (width) × 0-8 (height)
```

**Texture Creation Steps**:
1. Create 64×64 PNG image
2. Paint white base for fur
3. Add variant colors (blue, red, green, yellow, black accents)
4. Draw eyes (yellow/red with narrow shape)
5. Add pink nose
6. Paint red shirt and bell
7. Save as PNG with transparency

### 7. Adjust Entity Behavior

**File**: `behavior_pack/entities/sonnoh.json`

Modify behavior priorities (lower number = higher priority):

```json
"minecraft:behavior.follow_owner": {
  "priority": 4,
  "speed_multiplier": 1.0,      // 1.0 = same as player speed
  "start_distance": 8,          // Start following at 8 blocks
  "stop_distance": 2            // Stop following at 2 blocks
}
```

### 8. Add New Animation Events

**File**: `behavior_pack/entities/sonnoh.json`

Add to events section:

```json
"sonnoh:my_custom_event": {
  "add": {
    "component_groups": ["sonnoh_custom_state"]
  },
  "remove": {
    "component_groups": ["sonnoh_old_state"]
  }
}
```

## Advanced Customization

### Changing Spawn Biomes

Add to behavior_pack/entities/sonnoh.json:

```json
"minecraft:behavior.spawn": {
  "priority": 1,
  "biomes": ["forest", "jungle", "plains", "taiga"]
}
```

### Adding New Variant Colors

**Step 1**: Create texture file
- Create `sonnoh_purple.png` (64×64 PNG)

**Step 2**: Add to entity JSON textures
```json
"textures": {
  "default": "textures/entity/sonnoh_white",
  ...
  "purple": "textures/entity/sonnoh_purple"
}
```

**Step 3**: Add to spawn event randomize
```json
{
  "weight": 1,
  "add": {
    "component_groups": ["sonnoh_purple", "sonnoh_wild", "sonnoh_neutral"]
  }
}
```

**Step 4**: Add to dialogue system
```json
{
  "name": "sonnoh_greet_purple",
  "lines": [
    {
      "speaker": "sonnoh",
      "text": "meow! 💜"
    }
  ]
}
```

### Custom Items (Toys, Comb, Bed)

Create behavior file: `behavior_pack/items/sonnoh_toy.json`

```json
{
  "format_version": "1.17.0",
  "minecraft:item": {
    "description": {
      "identifier": "sonnoh:cat_toy",
      "category": "miscellaneous"
    },
    "components": {
      "minecraft:icon": "sonnoh_toy",
      "minecraft:max_stack_size": 64
    }
  }
}
```

### Sound Integration

Add to entity JSON:

```json
"minecraft:sound": {
  "sound_definition": "entity.sonnoh.purr",
  "volume": 1.0,
  "pitch": 1.0
}
```

## Testing Changes

### Quick Test Commands

```
# Summon Sonnoh
/summon sonnoh:sonnoh

# Summon specific variant
/summon sonnoh:sonnoh ~ ~1 ~ blue

# Set health (emotional state)
/entitydata @e[type=sonnoh:sonnoh] {Health: 5}

# Clear all Sonnoh
/kill @e[type=sonnoh:sonnoh]

# Enable debug
/gamerule debug true
```

### Validation

**Check JSON Syntax**:
1. Use [JSONLint.com](https://jsonlint.com/)
2. Paste your JSON code
3. Check for errors

**Check Minecraft Logs**:
- Windows: `%APPDATA%\.minecraft\logs\`
- Look for error messages

**Test in Safe World**:
1. Create test world with addon
2. Use `/reload` to reload packs
3. Test summon command
4. Check for animation/dialogue issues

## Performance Optimization

### Reduce Animation Complexity

```json
"loop": true,
"anim_time_update": "query.modified_move_speed"
```

### Limit AI Goals

Keep behavior priority list under 15 for optimal performance.

### Texture Optimization

- Use 64×64 instead of larger resolutions
- Compress PNG files with online tools
- Remove unused texture layers
- Use solid colors instead of gradients where possible

## Troubleshooting

### Entity Not Appearing

```
# Check if pack is loaded
/reload

# Verify UUID in manifest matches entity JSON
# Check for JSON syntax errors using JSONLint
```

### Animation Not Playing

```
# Verify animation name matches exactly
# Check animation controller references animation
# Ensure bones exist in model with exact names
# Check bone pivot points are correct
```

### Dialogue Not Showing

```
# Verify dialogue scene names are correct
# Check interaction triggers in entity JSON
# Ensure entity is spawned and tamed
# Type "Sonnoh" in chat to trigger dialogue
```

### Texture Not Showing

```
# Check PNG file is 64×64
# Verify texture path in entity JSON
# Ensure PNG has proper transparency
# Check UV coordinates in geometry
```

### Low FPS with Sonnoh

```
# Reduce animation frame complexity
# Limit number of spawned Sonnoh
# Disable ear flick animation if needed
# Lower render distance
# Disable debug mode
```

## Version Updates

### Updating the Addon

1. Backup existing world
2. Replace files with new version
3. Update version numbers in `manifest.json`:
   ```json
   "version": [1, 0, 1]  // Increment patch number
   ```
4. Run `/reload` in world
5. Test all features

### Breaking Changes

- Model changes require texture updates
- Animation changes need controller updates
- Dialogue changes require restart
- UUID changes reset existing entities

## Resources

- **[Blockbench](https://blockbench.net/)** - 3D Model Editor for Bedrock
- **[Microsoft Wiki](https://wiki.bedrock.dev/)** - Official Bedrock Documentation
- **[JSON Validator](https://jsonlint.com/)** - Online JSON syntax checker
- **[PNG Compressor](https://tinypng.com/)** - Compress texture files
- **[Bedrock Docs](https://learn.microsoft.com/en-us/minecraft/creator/documents/)** - Microsoft Creator Documentation

## Tips & Tricks

1. **Use VS Code** with JSON extension for easier editing
2. **Test frequently** after each change
3. **Keep backups** of working versions
4. **Comment your code** in JSON using description fields
5. **Use exact file paths** - case sensitivity matters
6. **Reload packs** with `/reload` to test changes
7. **Create variants** to test different features

---

**Need help? Check the README.md for more info! 🐱**
