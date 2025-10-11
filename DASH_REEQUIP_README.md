# Auto Re-Equip After Dash Feature

## What This Feature Does

When you use the dash ability in MVSD, your equipped weapon (gun, knife, etc.) automatically gets unequipped. This feature **automatically re-equips your weapon** after the dash completes, so you can immediately continue fighting without manually selecting it again.

## How to Use

### Default Behavior
The feature is **enabled by default** with a 0.1 second delay. You don't need to do anything - just play normally and your weapon will automatically re-equip after dashing.

### Customizing the Feature

#### To Enable/Disable:
1. Open the script UI
2. Click on the **"Misc"** tab
3. Find **"Auto Re-Equip Gun After Dash"** toggle
4. Click to enable (✓) or disable (✗)

#### To Adjust the Delay:
1. Open the script UI
2. Click on the **"Misc"** tab
3. Find **"Re-Equip Delay"** slider
4. Drag to adjust the delay:
   - **0 seconds**: Instant re-equip (might interrupt dash animation)
   - **0.1 seconds**: Default, works well for most situations
   - **0.5+ seconds**: Noticeable delay, use if you prefer manual control

## When to Adjust Settings

### If weapon re-equips too fast (during dash):
- **Increase** the "Re-Equip Delay" to 0.2-0.3 seconds
- This gives the dash animation more time to complete

### If weapon re-equips too slow:
- **Decrease** the "Re-Equip Delay" to 0.05 seconds or even 0
- This makes it almost instant

### If you prefer manual control:
- **Disable** the "Auto Re-Equip Gun After Dash" toggle
- Your weapon will stay unequipped after dash (original behavior)

## Frequently Asked Questions

**Q: Does this work with all weapons?**  
A: Yes! It works with guns, knives, and any other tool you equip.

**Q: Does this work after I die and respawn?**  
A: Yes! The feature automatically sets itself up when you respawn.

**Q: Will this get me banned?**  
A: This is a client-side feature that only affects your local experience. It doesn't give you any unfair advantages - it just saves you the hassle of manually re-equipping.

**Q: What if I manually unequip my weapon?**  
A: The feature is smart - it only re-equips weapons that were unequipped by abilities (like dash). If you manually unequip, it stays unequipped.

**Q: Can I use this with other features in the script?**  
A: Yes! This feature works alongside all other features like aimbot, ESP, cooldown adjustments, etc.

**Q: What's the performance impact?**  
A: Minimal! The feature uses efficient event listeners and only activates when you equip/unequip tools.

## Tips

- **For fast-paced combat**: Use 0.1 second delay (default)
- **For smoother animations**: Use 0.2-0.3 second delay
- **For maximum speed**: Use 0 second delay
- **For learning**: Disable the feature while learning dash mechanics

## Troubleshooting

### Weapon not re-equipping?
1. Check that the toggle is **enabled** in the Misc tab
2. Make sure your weapon is in your Backpack (not dropped)
3. Try increasing the delay to 0.2 seconds

### Weapon re-equips at wrong time?
1. Adjust the "Re-Equip Delay" slider
2. If it's too fast, increase the delay
3. If it's too slow, decrease the delay

### Want to go back to original behavior?
1. Simply toggle OFF "Auto Re-Equip Gun After Dash"
2. Or close and reopen the script

## Visual Guide

```
┌─────────────────────────────────────┐
│         MVSD Script - Misc          │
├─────────────────────────────────────┤
│                                     │
│ ☑ Auto Re-Equip Gun After Dash     │
│   Automatically re-equip weapon     │
│   when unequipped by dash/ability   │
│                                     │
│ Re-Equip Delay          [●─────]    │
│ 0.1 seconds                         │
│ Delay before re-equipping           │
│                                     │
└─────────────────────────────────────┘
```

## Support

If you encounter any issues:
1. Check this README first
2. Try adjusting the delay settings
3. Toggle the feature off and on again
4. Review TESTING.md for test cases
5. Check IMPLEMENTATION_SUMMARY.md for technical details

Enjoy smoother combat with automatic weapon re-equipping! 🎮
