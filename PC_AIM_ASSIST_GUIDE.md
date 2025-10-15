# PC Aim Assist Feature Guide

## Overview
The PC Aim Assist feature provides advanced targeting capabilities for PC players, including automatic mouse tracking and hitbox expansion to make targeting enemies easier.

## Features

### 1. Mouse Tracking
- Automatically tracks the nearest enemy player with your camera/mouse
- Smooth interpolation for natural-looking movement
- Configurable tracking distance (100-1000 studs)
- Works in real-time at ~60 FPS

### 2. Hitbox Expansion
- Expands enemy hitboxes from 0 to 30 studs
- Makes enemies easier to hit
- Invisible expansion (doesn't affect visuals)
- Dynamically updates for all enemies

### 3. Auto-Reload Per Round
- Automatically re-enables aim assist at the start of each round
- Persists until manually disabled
- Monitors game state to detect round changes

## How to Use

### Enabling PC Aim Assist
1. Open the script GUI
2. Navigate to the "Aim Bot" tab
3. Scroll down to the "PC Aim Assist" section
4. Toggle "Enable PC Aim Assist" to ON

### Configuring Settings

#### Mouse Tracking
- **Toggle**: Enable/disable automatic mouse tracking
- **When enabled**: Your camera will automatically follow the nearest enemy

#### Hitbox Expansion
- **Slider Range**: 0-30 studs
- **0**: No expansion (default)
- **30**: Maximum expansion
- **Recommended**: Start with 5-10 studs for subtle assistance

#### Tracking Smoothness
- **Range**: 0.1 (instant) to 1.0 (very smooth)
- **Default**: 0.5
- **Lower values**: More responsive but less natural
- **Higher values**: Smoother but slower to react

#### Mouse Sensitivity
- **Range**: 0.1x to 3.0x
- **Default**: 1.0x
- **Higher values**: Faster tracking
- **Lower values**: Slower, more precise tracking

#### Tracking Distance
- **Range**: 100-1000 studs
- **Default**: 500 studs
- **Purpose**: Maximum distance to track enemies
- **Higher values**: Track enemies from further away

#### Auto-Reload Per Round
- **Toggle**: Enable/disable automatic re-enabling per round
- **When enabled**: Aim assist will automatically turn back on each new round
- **Useful for**: Continuous gameplay without manual re-enabling

## Configuration Examples

### Aggressive Setup
```
Enable PC Aim Assist: ON
Mouse Tracking: ON
Hitbox Expansion: 20 studs
Tracking Smoothness: 0.2
Mouse Sensitivity: 2.0x
Tracking Distance: 800 studs
Auto-Reload Per Round: ON
```

### Balanced Setup (Recommended)
```
Enable PC Aim Assist: ON
Mouse Tracking: ON
Hitbox Expansion: 10 studs
Tracking Smoothness: 0.5
Mouse Sensitivity: 1.0x
Tracking Distance: 500 studs
Auto-Reload Per Round: ON
```

### Subtle Assistance
```
Enable PC Aim Assist: ON
Mouse Tracking: ON
Hitbox Expansion: 5 studs
Tracking Smoothness: 0.8
Mouse Sensitivity: 0.8x
Tracking Distance: 300 studs
Auto-Reload Per Round: OFF
```

## Technical Details

### Performance
- Updates at ~60 FPS (every 0.016 seconds)
- Minimal performance impact
- Efficient enemy distance calculations
- Dynamic hitbox management

### Compatibility
- Works with existing aimbot features
- Compatible with ESP features
- Team check respects existing settings
- Clean integration with WindUI

### Safety Features
- Automatic cleanup when disabled
- Proper memory management
- No server-side modifications
- Client-side only implementation

## Troubleshooting

### Mouse tracking not working
- Ensure "Enable PC Aim Assist" is ON
- Verify "Mouse Tracking" toggle is enabled
- Check that there are enemies within tracking distance
- Try increasing tracking distance

### Hitboxes not expanding
- Verify hitbox expansion is set above 0
- Ensure enemies are within range
- Check that the feature is enabled

### Auto-reload not working
- Confirm "Auto-Reload Per Round" is toggled ON
- Feature monitors the Match attribute
- May require a complete round cycle to activate

## Best Practices

1. **Start Conservative**: Begin with lower settings and gradually increase
2. **Test in Safe Mode**: Try settings in casual matches first
3. **Adjust for Playstyle**: Aggressive players may prefer higher sensitivity
4. **Balance is Key**: Too much assistance can be counterproductive
5. **Monitor Performance**: Lower settings if you experience lag

## Notes

- This feature is designed for PC players
- Works best with mouse and keyboard input
- Respects team check settings from other features
- Can be combined with other aim features for maximum effectiveness
- Auto-reload monitors game state changes automatically

## Support

For issues or questions:
- Check console for error messages
- Verify all dependencies are loaded
- Report bugs at: https://github.com/goose-birb/lua-buffoonery/issues
