# Saint's Movement & Safety

A mod for Fallout: New Vegas and Tale of Two Wastelands that adds condition-based restrictions to saving and fast travel. Written in NVSE, theoretically ESPLess\* (read note below).

## About

Allow preventing fast travel when the player has low health, has broken limbs, is irradiated, starving, dehydrated, or sleep deprived. Travel checks are only done once per Pip-Boy map menu open and restored after closing it. The mod will only disable fast travel if it was previously enabled and restore the prior state on menu close — if fast travel has already been disabled by a quest script, it will not be overridden.

Saving is set on a tick basis, conditions are checked every 60 frames. The mod can be configured to check if the player is in combat (either "Caution" or "Danger" state), or to only allow saving when sitting down (inspired by Carxt's "Save Restrictions" mod). It can also allow saving after sleeping (for a limited time after waking up).

## Important

This mod relies on two NVSE functions, `EnableFastTravel` and `ToggleDisableSaves`. 

`EnableFastTravel` can be called from any script but `ToggleDisableSaves` *requires* an owning plugin in the load order. Calling it from a script runner will not actually toggle the ability to save. For the save toggle to work, this mod requires a helper function hosted by a proper ESP/ESM plugin, as follows:

**SCTX - Script Source**

```
scn EnableSaves

begin function { short bEnable }
	if bEnable == 1
		ToggleDisableSaves 0
	elseif bEnable == 0
		ToggleDisableSaves 1
	endif
end
```

**SCDA - Compiled Source**

```
1D 00 00 00 10 00 0C 00 0D 00 40 00 00 00 01 01 01 00 01 00 16 00 0D 00 01 00 09 00 20 73 01 00 20 31 20 3D 3D 9E 31 07 00 01 00 6E 00 00 00 00 18 00 0D 00 01 00 09 00 20 73 01 00 20 30 20 3D 3D 9E 31 07 00 01 00 6E 01 00 00 00 19 00 00 00 11 00 00 00
```

You can either: 

1. Just load the included ESM plugin directly if you've got a slot to spare.
2. Merge the included ESM plugin into an existing plugin with *xEdit* or *zMerge*.
3. (Advanced) Create a new script record in any plugin and paste the above `SCTX` and `SCDA` into it.

## Petition

To remove the requirement for a helper function in a plugin, takes this as my public pledge for *Carxt* (Johnny Guitar NVSE), *JazziSparis* (JIP NVSE), *Demorome* (ShowOff NVSE), *Korri123* (xNVSE), or any of the other community developers of NVSE plugins to implement one of the following:

- Allow `ToggleDisableSaves` to be called from a script runner. Currently, this function is added by *JohnnyGuitar NVSE* but must be called from a plugin.
- Introduce a new `EnableSaves`/`EnableSaving` to mirror the existing `EnableFastTravel` (a vanilla F3 function).

## License

This mod was created by Saint for free use by the Fallout mod community under the MIT license. It may be shared, modified, or redistributed as part of mod packs with basic attribution.