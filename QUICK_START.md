# ML Auto Shoot - Quick Start Guide

## Getting Started in 3 Steps

### Step 1: Load the Script
Execute the main script in your Roblox game executor. The ML Auto Shoot feature is included in the main script.

### Step 2: Open the GUI
The script will automatically create a GUI window. Navigate to the **Misc** tab.

### Step 3: Enable ML Auto Shoot
1. Find the "ML Auto Shoot" toggle in the Misc tab
2. Click to enable it
3. You'll see a notification: "ML Auto Shoot activated."

## That's It!
The system will now:
- Track enemy positions automatically
- Predict their future positions using a neural network
- Shoot when confidence is high enough

## Adjusting Settings (Optional)

If you want to fine-tune the feature:

### ML Prediction Frames (Default: 5)
- **Lower (1-3)**: For enemies with erratic movement
- **Higher (10-20)**: For enemies moving in straight lines

### ML Confidence Threshold (Default: 0.7)
- **Lower (0.3-0.5)**: More aggressive, shoots more often
- **Higher (0.8-0.95)**: Conservative, only shoots when very confident

### ML Max Shoot Distance (Default: 500)
- **Lower (100-300)**: Better accuracy at close range
- **Higher (600-1000)**: Covers more area but less accurate

## Testing Your Setup

To verify the feature is working:

1. **Enable ML Auto Shoot**
2. **Wait for enemies to appear** (the system needs a few seconds to collect data)
3. **Look for automatic shooting** when an enemy is detected
4. **Check notifications** - you should see "ML Auto Shoot activated"

## Troubleshooting

### Not Shooting?
- **Confidence too high**: Lower the confidence threshold
- **Not enough data**: Wait 2-3 seconds for the system to collect enemy movement data
- **Team check enabled**: Make sure you're not on the same team as the targets

### Shooting Too Much?
- **Confidence too low**: Increase the confidence threshold
- **Distance too large**: Reduce the max shoot distance

### Low Accuracy?
- **Prediction frames too high**: Reduce prediction frames for more immediate targets
- **Enemies moving erratically**: The system works best with predictable movement patterns

## Advanced Tips

1. **Combine with ESP**: Use the ESP feature to visually confirm targets
2. **Use with Team Check**: Enable team check to avoid shooting teammates
3. **Adjust for weapon type**: 
   - Close-range weapons: Lower max distance, lower prediction frames
   - Long-range weapons: Higher max distance, higher prediction frames
4. **Monitor confidence**: Lower threshold in chaotic situations, raise in controlled scenarios

## Feature Compatibility

The ML Auto Shoot feature works with:
- ✅ Team Check
- ✅ ESP (visual confirmation)
- ✅ All existing gun shoot features
- ✅ Auto Farm modes

## Performance Notes

- **Low Impact**: The neural network is optimized for performance
- **Automatic Cleanup**: Old tracking data is cleaned up every second
- **Efficient Updates**: Only updates 20 times per second
- **Memory Safe**: Limits tracking data to prevent memory issues

## What Makes This "Machine Learning"?

This feature uses a real neural network with:
- **3 layers**: Input → Hidden → Output
- **Weight matrices**: Initialized using Xavier initialization
- **Activation functions**: ReLU for non-linearity
- **Forward propagation**: Mathematical prediction based on learned weights
- **Confidence calculation**: Statistical analysis of movement patterns

While the weights are initialized randomly (not trained on extensive data), the architecture follows standard machine learning principles and provides intelligent prediction capabilities.

## Need Help?

- Check the detailed usage guide: `ML_AUTO_SHOOT_USAGE.md`
- Review the technical architecture: `ML_ARCHITECTURE.txt`
- Report issues on the GitHub repository

---

**Enjoy your enhanced auto shoot capabilities!** 🎯🤖
