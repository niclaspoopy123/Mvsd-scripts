# Testing the Dash Gun Re-Equip Fix

## Overview
This fix ensures that when you dash in MVSD Roblox and your gun gets unequipped, it will automatically re-equip after the dash completes.

## How to Test

### Prerequisites
1. Load the MVSD script in Roblox
2. Have a gun equipped
3. Have a dash ability available

### Test Case 1: Basic Re-Equip
1. **Setup**: Equip a gun/weapon
2. **Action**: Use your dash ability (usually bound to a key like Q or Shift)
3. **Expected Result**: The gun should automatically re-equip after a brief delay (0.1 seconds by default)
4. **Verify**: Check that the gun is in your hand and ready to fire

### Test Case 2: Toggle Feature Off
1. **Setup**: Open the script UI, go to Misc tab
2. **Action**: Toggle OFF "Auto Re-Equip Gun After Dash"
3. **Action**: Equip gun and dash
4. **Expected Result**: Gun stays unequipped (original behavior)
5. **Action**: Toggle ON "Auto Re-Equip Gun After Dash"
6. **Action**: Equip gun and dash again
7. **Expected Result**: Gun re-equips automatically

### Test Case 3: Adjust Delay
1. **Setup**: Open script UI, go to Misc tab
2. **Action**: Set "Re-Equip Delay" slider to 0.5 seconds
3. **Action**: Equip gun and dash
4. **Expected Result**: Gun re-equips after approximately 0.5 seconds (noticeable delay)
5. **Action**: Set delay back to 0.1 seconds
6. **Expected Result**: Gun re-equips almost instantly after dash

### Test Case 4: Multiple Dashes
1. **Setup**: Equip a gun
2. **Action**: Dash multiple times in quick succession
3. **Expected Result**: Gun should re-equip after each dash

### Test Case 5: Respawn Test
1. **Setup**: Enable auto re-equip
2. **Action**: Die and respawn
3. **Action**: Equip gun and dash
4. **Expected Result**: Feature still works after respawn

## Troubleshooting

### Gun Not Re-Equipping
- Check that "Auto Re-Equip Gun After Dash" toggle is ON in Misc tab
- Verify the gun is actually in your Backpack (not dropped or destroyed)
- Try adjusting the "Re-Equip Delay" slider to a slightly higher value

### Gun Re-Equips Too Slowly
- Lower the "Re-Equip Delay" value in the slider (minimum is 0 seconds)

### Gun Re-Equips During Dash Animation
- Increase the "Re-Equip Delay" value to allow the dash to complete first

## Technical Details

The fix works by:
1. Tracking which tool is equipped using Humanoid.ToolEquipped event
2. Detecting when the tool is unequipped using Humanoid.ToolUnequipped event
3. Waiting for the configured delay (to let dash animation complete)
4. Re-equipping the tool using humanoid:EquipTool() if it's in the Backpack

This approach is efficient and works with all tools/weapons, not just guns.
