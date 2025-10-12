# ML Auto Shoot Feature - Usage Guide

## Overview
The ML Auto Shoot feature uses a simple neural network to predict enemy positions and automatically shoot when confidence is high enough. This provides more intelligent and predictive auto-shooting compared to basic methods.

## Features

### 1. Neural Network Architecture
- **Input Layer**: 6 neurons (posX, posY, posZ, velX, velY, velZ)
- **Hidden Layer**: 8 neurons with ReLU activation
- **Output Layer**: 3 neurons (predicted posX, posY, posZ)
- **Weight Initialization**: Xavier initialization for better convergence

### 2. Enemy Tracking System
- Automatically tracks position and velocity history for each enemy
- Stores up to 10 historical data points per enemy
- Automatic cleanup of stale data (older than 5 seconds)

### 3. Prediction Confidence
- Calculates confidence based on movement consistency
- Only shoots when confidence exceeds the configured threshold
- Falls back to simple linear prediction if not enough data is available

### 4. Configuration Options

#### Global Settings (in getgenv().mlAutoShootConfig):
```lua
ENABLED = false              -- Feature enabled/disabled
PREDICTION_FRAMES = 5        -- Frames ahead to predict (affects prediction time)
HISTORY_LENGTH = 10          -- Number of positions to track per enemy
LEARNING_RATE = 0.01         -- Future: for online learning
CONFIDENCE_THRESHOLD = 0.7   -- Minimum confidence to shoot (0.0-1.0)
UPDATE_INTERVAL = 0.05       -- Prediction update frequency (seconds)
SHOOT_DELAY = 0.01           -- Minimum delay between shots (seconds)
MAX_SHOOT_DISTANCE = 500     -- Maximum distance to attempt shooting
```

## UI Controls (in Misc Tab)

### ML Auto Shoot Toggle
- **Description**: Enable/disable the ML auto shoot feature
- **Default**: Off
- **Notification**: Shows "ML Auto Shoot activated/deactivated"

### ML Prediction Frames Slider
- **Range**: 1-20 frames
- **Default**: 5 frames
- **Description**: Controls how far ahead the network predicts enemy positions
- Higher values = more lead time but less accurate for erratic movement

### ML Confidence Threshold Slider
- **Range**: 0.0-1.0
- **Default**: 0.7
- **Description**: Minimum confidence required before shooting
- Lower values = more shots but potentially less accurate
- Higher values = fewer shots but more confident predictions

### ML Max Shoot Distance Slider
- **Range**: 100-1000 studs
- **Default**: 500 studs
- **Description**: Maximum distance at which the feature will attempt to shoot
- Shorter distances = better accuracy
- Longer distances = more coverage but reduced precision

## How It Works

1. **Data Collection**: The system continuously tracks enemy positions and velocities
2. **Neural Network Processing**: For each enemy, the network processes the latest position/velocity data
3. **Prediction**: The network outputs a predicted future position
4. **Confidence Calculation**: Movement consistency is analyzed to determine prediction reliability
5. **Target Selection**: The enemy with highest confidence above threshold is selected
6. **Shooting**: If a valid target is found within max distance, the gun is fired

## Integration with Existing Features

- **Team Check**: Respects the `teamCheckKill` setting (won't shoot teammates)
- **Gun Shoot Remote**: Uses the same `ReplicatedStorage:FindFirstChild("GunShoot")` as other features
- **Periodic Cleanup**: Automatically removes stale tracking data to prevent memory buildup

## Technical Details

### Fallback Behavior
If insufficient tracking data exists (less than 3 data points), the system falls back to simple linear extrapolation:
```lua
predictedPosition = currentPosition + velocity * predictionTime
confidence = 0.5  -- Medium confidence for fallback
```

### Confidence Calculation
Confidence is calculated based on velocity consistency:
```lua
confidence = 1.0 - (averageVelocityChange / 50)
confidence = clamp(confidence, 0.3, 0.95)
```

### Performance Considerations
- Update interval: 0.05s (20 updates per second)
- Cleanup interval: 1.0s (removes data older than 5 seconds)
- Minimal memory footprint: Stores only recent history per enemy
- Efficient forward propagation: O(n*m) where n=input size, m=hidden size

## Best Practices

1. **Start with default settings** and adjust based on gameplay
2. **Increase confidence threshold** if you're getting too many false shots
3. **Decrease prediction frames** for enemies with erratic movement
4. **Increase max distance** for long-range weapons, decrease for close-range
5. **Combine with other features** like ESP for visual confirmation of targets

## Future Enhancements
- Online learning to adapt weights based on hit/miss feedback
- Multiple prediction models for different enemy movement patterns
- Advanced features like obstacle avoidance in predictions
- Training mode to learn from player's own shooting patterns
