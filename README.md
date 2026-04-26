# Saint's Movement & Safety

A mod for Fallout: New Vegas and Tale of Two Wastelands that adds condition-based restrictions to saving and fast travel. Written in NVSE, theoretically ESPLess\* (read note below).

Allow preventing fast travel when the player has low health, has broken limbs, is irradiated, starving, dehydrated, or sleep deprived. Travel checks are only done once per Pip-Boy map menu open and restored after closing it. The mod will only disable fast travel if it was previously enabled and restore the prior state on menu close — if fast travel has already been disabled by a quest script, it will not be overridden.

Saving is set on a tick basis, conditions are checked every 60 frames. The mod can be configured to check if the player is in combat (either "Caution" or "Danger" state), or to only allow saving when sitting down (inspired by Carxt's "Save Restrictions" mod). It can also allow saving after sleeping (for a limited time after waking up).

## License

This mod was created by Saint for free use by the Fallout mod community under the MIT license. It may be shared, modified, or redistributed as part of mod packs with basic attribution.