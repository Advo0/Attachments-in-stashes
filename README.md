# Attachments in Stashes Mod v1.2.2
### S.T.A.L.K.E.R. GAMMA / Anomaly addon

---

## Features

### 1. Traders NO LONGER SELL attachments
- All traders (suppliers, barmen, mechanics, medics) will **no longer sell**:
  - Scopes (night vision scopes, optics, red dots, etc.)
  - Silencers
  - Weapon upgrade kits (`upgr_w_*`)
  - Outfit/armor upgrade kits (`upgr_o_*`)
- These items can **only be obtained from blue reward stashes** or by looting enemies.

---

### 2. Dark Blue Reward Stash - every 10-12 quests
- Every **10-12 completed quests**, a **dark blue marker** appears on the map — a special stash.
- The stash contents depend on the **current map tier**:

| Map | Tier | Attachment Quality |
|-----|------|--------------------|
| Cordon, Great Swamps, Garbage, Dark Valley, Darkscape, Meadows | 1-2 | Basic (OKP, Kobra, etc.) |
| Rostok, Agroprom, Truck Cemetery, Dead City, Army Warehouses, Radar | 2-3 | Medium (ACOG, PSO, etc.) |
| Yantar, Jupiter, Red Forest, Zaton, Pripyat and others | 3-5 | High-End (RMR, Aimpoint, Marchf, etc.) |

- Each stash will contain **scopes, silencers, and a chance for weapon/outfit upgrades**.
- Has an 80% chance to spawn upon reaching the threshold. If it fails, it will roll the 80% chance again on every subsequent quest completion until it succeeds.

---

### 3. Light Blue Rare Stash - every 20-25 quests
- Every **20-25 completed quests**, a **light blue stash** appears instead.
- **Guaranteed to contain**:
  - A Tactical/Combo Gun Kit (e.g., BaS kits)
  - A Weapon Upgrade Part
  - An Armor Upgrade Part
  - A Toolkit cycle (Drug kit -> Ammo kit -> Basic/Advanced/Expert toolkit depending on map tier)
  - Multiple scopes and silencers.
- This provides an alternative progression path for upgrades without relying on traders.

---

### 4. Enemy Corpse Looting
- There is a very small chance (0.02% to 2% depending on rank) to find these blue stash coordinates directly from looting enemy corpses.

---

## Installation (GAMMA / MO2)

1. Ensure the mod folder is in your `C:\GAMMA\mods\` directory (as `Attachments in stashes`).
2. Open **Mod Organizer 2**.
3. Find `Attachments in stashes` in your mod list and **enable it** ✓.
4. Load it **after** `60- Stash Overhaul - Grokitach` and **after** `212- Trader Destockifier`.
5. Launch the game.

---

## Compatibility
- Stash Overhaul (Grokitach) - compatible (supplements, does not override).
- Trader Destockifier - compatible (both restrict traders).
- GAMMA Dynamic Loot Balance.
- Harukas Skill System.

---

## Technical Details
- **Scripting**: Lua (Anomaly 1.5.1+ / GAMMA).
- **MCM Support**: Allows tweaking of quest thresholds and trader bans.
- **Save variables**: `qrs_quest_count`, `qrs_last_attach`, `qrs_last_kit`, etc.
- **Save Compatibility**: Safe to install mid-playthrough.
- **Console**: Run `qrs_reset_thresholds()` in-game to reset thresholds to current defaults.

---

## Changelog

### v1.2.2
- **FIXED**: Improved trader UI detection hook by utilizing `trader_autoinject.get_trader_type()`. Faction traders like Petrenko or Dushman will now instantly have their inventories cleaned upon opening the trade window, resolving the bug where disabled items lingered until their next restock cycle.


### v1.2.1
- **FIXED**: Removed `cut_kit` from the Tier 3 pool which was causing "Not Used" broken items to spawn in stashes.
- **IMPROVED**: Dark Blue Stash 80% chance logic: If you miss the 80% chance at the threshold, it no longer resets the counter. Instead, it will retry the 80% chance on every subsequent quest until you succeed.
- **TWEAK**: Grenade Launchers are now exclusively restricted to Tier 4 and Tier 5 maps to reflect their end-game value.

### v1.2.0
- **FIXED**: Critical bug where Boomsticks and Sharpsticks scopes (e.g., OKP, Kobra) were immediately deleted after being successfully injected into trader inventories because their internal class differs from vanilla scopes. Now using specific item blacklisting bypassing native classes.
- **IMPROVED**: T1 trader whitelist injection logic is now bulletproof and directly bypasses generic class filters.
- **VERIFIED**: Confirmed compatibility and integration of new gun kits from Boomsticks and Sharpsticks and GIMP.

### v1.1.0
- Fixed crash (`KITS_BY_TIER` nil error) when talking to traders in Dead City with T1 attachments enabled.
- T1 trader whitelist now correctly allows both attachments AND gun kits when option is enabled.
- Changed default Dark Blue stash threshold: **12-15 → 10-12** quests.
- Changed default Light Blue stash threshold: **35-40 → 20-25** quests.
- Added `qrs_reset_thresholds()` console command to apply new defaults without deleting saves.

### v1.0.0
- Initial release.
