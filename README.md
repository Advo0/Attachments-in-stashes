# Attachments in Stashes Mod v1.4.2
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
- **Guaranteed to contain**:
  - Exactly **3 Scopes** and **2 Silencers**
  - Items are guaranteed to be unique (no duplicates in the same stash).
  - Has an 80% chance to spawn upon reaching the threshold. If it fails, it will roll the 80% chance again on every subsequent quest completion until it succeeds.
- The stash attachment tiers depend on the **current map tier**:

| Map | Tier | Attachment Quality |
|-----|------|--------------------|
| Cordon, Great Swamps, Garbage, Dark Valley, Darkscape, Meadows | 1-2 | Basic (OKP, Kobra, etc.) |
| Rostok, Agroprom, Truck Cemetery, Dead City, Army Warehouses, Radar | 2-3 | Medium (ACOG, PSO, etc.) |
| Yantar, Jupiter, Red Forest, Zaton, Pripyat and others | 3-5 | High-End (RMR, Aimpoint, Marchf, etc.) |

---

### 3. Light Blue Rare Stash - every 20-25 quests
- Every **20-25 completed quests**, a **light blue stash** appears instead.
- **Guaranteed to contain**:
  - Exactly **4 Scopes** and **3 Silencers** (all unique, no duplicates)
  - **100% chance** for a Grenade Launcher if the map is Tier 3 or above (Radar, Red Forest, Pripyat, etc.)
  - A Tactical/Combo Gun Kit (e.g., BaS kits)
  - A Weapon Upgrade Part
  - An Armor Upgrade Part
  - A progressive Toolkit cycle: `Drug Making Kit` -> `Gunsmithing Tools` -> `Basic/Advanced/Expert Toolkits`. The cycle never resets. It will dynamically skip the first two stages if you already have the Drug Kit or Gunsmithing Tools in your inventory!

---

### 4. Enemy Corpse Looting & PDAs
- **Looting**: You have a customizable chance (1-5% by default based on rank) to discover blue stash coordinates directly when looting enemy corpses.
- **PDAs**: You have a universal customizable chance (3% by default) to extract blue stash coordinates when viewing a decrypted/unlocked PDA in your inventory.
- **Exploit Protection**: The PDA extraction rolls exactly once per physical PDA item to prevent spamming.
- All chances are fully configurable via the **MCM Menu**.

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

### 1.4.2
- **NEW**: Added a chance to discover blue stash coordinates directly from extracting data from decrypted/unlocked PDAs in your inventory.
- **NEW**: Full MCM integration for customizing drop rates from both Dead Stalkers (based on their rank) and PDAs.
- **IMPROVED**: The corpse looting mechanic now properly scales drop chances based on enemy rank (Rookie/Novice to Expert/Legend) and is fully adjustable via MCM.
- **ANTI-EXPLOIT**: PDA stash extraction rolls exactly once per physical PDA item. Spamming the "View" button or clicking on locked PDAs will not grant extra chances or waste your roll.

### 1.4.1
- **STABILITY**: Added protection against companion inventory corruption. The mod will now skip inventory cleaning if the trader is identified as a companion.

### 1.4.0
- **ECONOMY OVERHAUL**: Reduced the base cost (selling price) of all mid-to-high tier scopes, silencers, and kits by exactly 4x. This prevents the player from becoming unreasonably wealthy from selling stash loot in the mid-to-late game. The low-tier (T1) items sold by specific traders retain their original prices.
- **BALANCED**: Dark Blue Stashes now drop exactly 3 scopes and 2 silencers. Light Blue Stashes drop 4 scopes and 3 silencers.
- **BALANCED**: Implemented item uniqueness check inside stash generation so you never receive duplicate attachments in the same stash box.
- **NEW**: Light Blue Stashes now have a 100% drop rate for Grenade Launchers, provided the stash spawns in a Tier 3 or higher zone. Dark Blue stashes no longer drop Grenade Launchers at all. Grenade launchers are also now distributed down to Tier 3 zones.
- **NEW**: The Light Blue Stash toolkit cycle has been massively improved for logic and quality of life. It progresses: `Drug Making Kit -> Gunsmithing Tools -> Toolkits (Forever)`. It also checks the player's inventory on stash generation; if the player already holds a Drug Making Kit or Gunsmithing Tools, it skips that cycle step automatically.

### 1.3.1 
- **IMPROVED**: Switched trader filtering from a blacklist to a Strict Whitelist system. Only explicitly listed main faction quartermasters (e.g., Sidorovich, Petrenko, Dushman, etc.) are allowed to have and sell attachments and upgrade kits. This permanently fixes issues with dynamic/generic traders (Bandits, Medics, Mechanics, Forester, Spirit, etc.) bypassing the filter.
- **IMPROVED**: Added dynamic duplicate cleaning in `clean_trader_inventory`. If a valid trader somehow receives multiple copies of the exact same injected attachment, the script instantly deletes the duplicates upon opening the UI.
- **FIXED**: Ecologists are now explicitly completely banned from having any scopes, silencers, or kits.

### 1.3.0 
- **NEW**: Faction-specific T1 weapon upgrade kits injection! Now when T1 attachments are allowed at traders, they will also sell basic pistol/gun kits depending on their faction (e.g. Duty gets PM, PB, PL-15, SR1MP kits; Mercenaries get Mod9, M9, Tikka kits).

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
