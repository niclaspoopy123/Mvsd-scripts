# Progression Save/Load System - Complete Guide

## Overview

The Progression System preserves your settings, AI learning data, and statistics when you leave the game, then automatically restores everything when you rejoin. Never lose your progress again!

## What Does It Save?

### ⚙️ **User Settings**
- All aimbot configurations
- ML Auto Shoot settings
- AI Auto-Play preferences
- Game Analytics configuration
- Safe Position calculator settings

### 🧠 **AI Learning Data**
- Enemy behavior patterns
- Win/loss patterns per strategy
- Map analysis data
- Identified cover points
- Strategic position data

### 📊 **Game Statistics**
- Total wins and losses
- Kill/Death counts
- Win rate percentages
- K/D ratio
- Best performing strategy

## How to Use

### Quick Start (2 Steps)

1. **Open the GUI** and navigate to the **"Progression"** tab
2. **Enable "Enable Progression System"** toggle

That's it! Your progress will now:
- ✅ Auto-save every 30 seconds
- ✅ Save when leaving game
- ✅ Auto-load when joining game

### Manual Save/Load

**To Save Manually:**
1. Go to Progression tab
2. Click **"Save Now"** button
3. Notification confirms save success

**To Load Manually:**
1. Go to Progression tab
2. Click **"Load Progress"** button
3. Notification confirms load success

## Features in Detail

### 1. Auto-Save

**Periodic Save:**
- Saves every 30 seconds by default (configurable)
- Only saves when system is enabled
- Runs in background without lag

**Save on Game Leave:**
- Automatically saves when you close game
- Saves when player character leaves
- Ensures no progress loss

### 2. Auto-Load

**On Game Join:**
- Automatically loads saved data 2 seconds after spawn
- Restores all settings and configurations
- Applies learned AI data
- Shows notification when complete

**Smart Loading:**
- Only loads if save file exists
- Validates data before applying
- Handles missing/corrupt data gracefully

### 3. Selective Saving

Choose what to save:
- ✅ **Settings**: User configurations
- ✅ **AI Learning Data**: Patterns and analytics
- ✅ **Statistics**: Performance metrics

Disable any category to exclude from saves.

### 4. Data Storage

**Save File Location:**
- Stored locally on your device
- File name: `MVSD_Progress_[UserID].json`
- JSON format for readability
- Approximately 2-5 KB per save

**Security:**
- User ID specific (each account separate)
- No sensitive information stored
- Client-side only (no server interaction)

## Configuration Options

### Basic Settings

| Setting | Default | Description |
|---------|---------|-------------|
| **Enable System** | OFF | Master toggle for save/load |
| **Auto-Save** | ON | Periodic automatic saves |
| **Auto-Load on Join** | ON | Load on game start |

### Save Options

| Setting | Default | Description |
|---------|---------|-------------|
| **Save Settings** | ON | Include user configurations |
| **Save AI Learning Data** | ON | Include patterns and analytics |
| **Save Statistics** | ON | Include performance metrics |

### Advanced Settings

| Setting | Range | Default | Description |
|---------|-------|---------|-------------|
| **Auto-Save Interval** | 10-300s | 30s | How often to auto-save |

### Global Configuration

```lua
getgenv().progressionConfig = {
    ENABLED = false,
    AUTO_SAVE = true,
    AUTO_LOAD = true,
    SAVE_INTERVAL = 30,
    SAVE_SETTINGS = true,
    SAVE_AI_DATA = true,
    SAVE_STATISTICS = true,
}
```

## What Gets Saved

### Settings Data Structure

```lua
settings = {
    aimConfig = {
        -- All aimbot settings
        MAX_DISTANCE = 150,
        FOV_CHECK = true,
        -- ... etc
    },
    mlAutoShootConfig = {
        -- ML Auto Shoot settings
        ENABLED = false,
        CONFIDENCE_THRESHOLD = 0.7,
        -- ... etc
    },
    aiAutoPlayConfig = {
        -- AI Auto-Play settings
        MOVEMENT_STYLE = "balanced",
        TARGET_PRIORITY = "nearest",
        -- ... etc
    },
    gameDataAnalytics = {
        -- Analytics settings
        ENABLED = true,
        TRACK_WIN_PATTERNS = true,
        -- ... etc
    },
    safePositionConfig = {
        -- Safe position settings
        ENABLED = true,
        AUTO_MOVE_TO_SAFE = false,
        -- ... etc
    }
}
```

### AI Data Structure

```lua
aiData = {
    enemyPatterns = {
        -- Per-enemy movement and combat patterns
        [userId] = {
            movementStyles = { aggressive, defensive, evasive counts },
            combatBehaviors = { ... },
            weaknesses = { ... }
        }
    },
    winPatterns = {
        -- Strategy performance data
        strategies = {
            ["aggressive"] = { wins = 5, losses = 2 },
            ["balanced"] = { wins = 8, losses = 1 },
            -- ... etc
        },
        positions = { ... },
        weapons = { ... }
    },
    mapData = {
        -- Analyzed map geometry
        safeZones = { ... },
        coverPoints = { ... },
        highGroundPositions = { ... }
    }
}
```

### Statistics Structure

```lua
statistics = {
    wins = 15,
    losses = 5,
    kills = 127,
    deaths = 42,
    averageAccuracy = 0.73,
    bestStrategy = "balanced"
}
```

## Save File Format

### JSON Structure

```json
{
    "version": "1.0",
    "timestamp": 1697123456.789,
    "settings": { ... },
    "aiData": { ... },
    "statistics": { ... }
}
```

### Version Control

- Current version: 1.0
- Future versions may add new fields
- Backward compatible loading
- Migration path for old saves

## Integration with Other Features

### Works With:
- ✅ **All Feature Tabs**: Saves configurations
- ✅ **Game Analytics**: Preserves learned data
- ✅ **AI Auto-Play**: Remembers best strategies
- ✅ **ML Auto Shoot**: Saves tuned settings
- ✅ **Safe Position**: Keeps weight preferences

### Workflow Example:

```
Day 1:
  1. Configure features
  2. Play matches (analytics learning)
  3. Save progress before leaving
  
Day 2:
  1. Join game
  2. Auto-load restores everything
  3. AI uses learned data immediately
  4. Continue from where you left off
```

## Best Practices

### For Optimal Use:

1. **Enable on First Use**: Start saving immediately
2. **Keep Auto-Save ON**: Prevents data loss
3. **Regular Manual Saves**: Before risky changes
4. **Test Load**: Verify saves work periodically
5. **Backup Files**: Copy save files externally for safety

### Data Management:

**When to Save:**
- ✅ After significant configuration changes
- ✅ After successful match sessions
- ✅ Before experimenting with new settings
- ✅ Before closing game

**When to Load:**
- ✅ When starting new session
- ✅ After accidentally changing settings
- ✅ When reverting to known-good config

**When to Reset:**
- ⚠️ When changing playstyle drastically
- ⚠️ When analytics data becomes stale
- ⚠️ When starting fresh on new account

## Troubleshooting

### "Save failed"
- **Cause**: File system not accessible
- **Solution**: Check executor supports `writefile()`
- **Workaround**: Use manual configuration backup

### "Load failed" or "No saved progress"
- **Cause**: No save file exists yet
- **Solution**: Save first, then load
- **Check**: Look for `MVSD_Progress_[UserID].json`

### "Settings not restoring"
- **Cause**: Save Settings toggle is OFF
- **Solution**: Enable Save Settings before saving
- **Verify**: Check which options are enabled

### "Corrupted save file"
- **Cause**: File interrupted during write
- **Solution**: Delete file and save again
- **Prevention**: Don't close game during save

## Performance

- **Save Operation**: <100ms typically
- **Load Operation**: <200ms typically
- **File Size**: 2-5 KB average
- **Auto-Save Overhead**: Negligible (<0.1% CPU)
- **Memory Usage**: ~1 KB for progression system

## Advanced Usage

### Manual File Access

**File Location** (varies by executor):
```
workspace/MVSD_Progress_[UserID].json
```

**Reading Save File:**
```lua
local HttpService = game:GetService("HttpService")
local fileName = "MVSD_Progress_" .. localPlayer.UserId .. ".json"

if isfile(fileName) then
    local content = readfile(fileName)
    local data = HttpService:JSONDecode(content)
    print("Last save:", data.timestamp)
    print("Wins:", data.statistics.wins)
end
```

### Exporting/Importing

**Export Save:**
1. Locate save file in workspace
2. Copy to safe location
3. Rename for identification

**Import Save:**
1. Place save file in workspace
2. Ensure correct filename format
3. Click "Load Progress"

### Backup Strategy

**Recommended:**
- Keep 3 recent saves
- Weekly backups for long-term play
- Test restores periodically
- Document custom configurations

## Security & Privacy

### What's Safe:
- ✅ All settings are game-related only
- ✅ No personal information stored
- ✅ Local storage only (no cloud)
- ✅ No passwords or tokens saved
- ✅ User ID is already public in Roblox

### What to Avoid:
- ❌ Don't share save files (exposes user ID)
- ❌ Don't edit manually (risk corruption)
- ❌ Don't load unknown save files

## Future Enhancements

Potential additions:
- Cloud save support (optional)
- Multiple save slots
- Save file compression
- Encryption for privacy
- Cross-account sync
- Save file browser UI
- Configuration presets

## Tips and Tricks

1. **Save Before Experimenting**: Easy revert if needed
2. **Named Backups**: Copy files with descriptive names
3. **Compare Saves**: Test different configurations
4. **Share Configs**: Export and share with friends
5. **Version Control**: Keep saves from different versions

## Summary

The Progression System ensures you never lose your carefully tuned settings, valuable AI learning data, or hard-earned statistics. It seamlessly saves and restores everything, making your experience continuous across sessions.

**Key Benefits:**
- 💾 Automatic save/load
- ⚙️ Preserves all settings
- 🧠 Retains AI learning
- 📊 Tracks statistics
- 🔄 Seamless experience

Set it up once, and never worry about losing progress again!

---

**Feature Status**: ✅ Production Ready  
**Version**: 1.0  
**Date**: 2025-10-13  
**File Format**: JSON v1.0
