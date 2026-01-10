# Age of Empires IV - Advanced Game Settings
Advanced Game Settings is a game mode for Age of Empires IV that provides new options for players to customize their games.

## Features:

**Regicide**
   * Each player starts with a king unit and goal is to protect player's king and defeat all other kings.

**Score**
   * Game lasts until timer reaches end or it was finished by any other win condition. Once timer reaches end, player with highest score will win.

**Conquest** (Originally named **Landmark**)
  * Defines buildings that are used as objectives for victory. If all objectives are destroyed, once at least one was built, the player will lose.

**Religious** (Originally named **Sacred Site**)

**Treaty**
  * The game starts with predefined timer, during which all players are allied. Once timer ends relations will turn to original one.

**Settlement**
  * Allows player to choose how they start/spawn into the game. Either with only units, units and town center or also with walls.*

**Team Victory**
  * Allows players to choose if game can be won as FFA, Team or with any dynamically formed team.

**Maintain Team Balance**
  * Whenever team loses player, remaning players will share his population and resources.

**Team Solidarity**
  * All players in team are elimianted if any of their teammates is eliminated.

**Enable AI Takeovers**
  * Whenever player drops or rage quits from the game, he will be controlled by the AI for the rest of
the match._
**Win Settings**
  * Customize certain rules and values for win conditions such as timers.

**Team Vision**
  * Changes how players vision is shared between allied players. Only team allies that can win together
can share vision._
**Diplomacy**
  * Allows players to change relations during the game via Players & Tributes.

**Empowered King**
  * King unit receives 4 additional active abilities: attack speed, production speed, attack damage, healing. Passive aura that boosts damage by 50% and 4 armor. Additional 800 health, 3.5 movement speed, 1 armor and 10 radius for vision.

**Tree Bombardment**
  * Makes all siege and ships with attack ground able to destroy trees.

**Treasures**
  * Search for small treasures around the map and claim them before your enemies.

**Double Production**
  * Speeds up production and reduces cost of economic units to help establish strong economy faster.

**Handicaps**
  * Provides percantage bonus to each player based on selected value. Economic bonuses are faster gather rates, larger carrying capacity and higher trade. Military bonuses include higher armor, health for all units and buildings. Buildings also receive higher production and research speed.

**Tournament Balance**
  * Nomad tournament adjustments:
    * **Mongols**: +100 Wood
    * **English**: +50 Wood
    * **Ottomans**: +50 Stone +50 Wood
    * **Chinese**: Main Town Center build time +100%
    * **All**: Outpost available only after first Town Center built.

## Game Modes

* __Advanced Game Settings__: Base mode selection
![mod settings header](resources/images/mod_settings-header.png)

* __City-State Wars__: Game mode that pitches players to fight without any civilization bonus. To obtain advantage players have to capture cities spread in a grid like shape around the map.
![image](resources/images/mod_selection-city_state_wars.png)

* __Nomad__: Game mode where players start out with villagers spread out across the map without a Town Center or Scout. They must build their first Town Center at no cost which becomes their landmark Town Center. The standard tech tree unlocks upon Town Center creation.
Additional Options for Nomad AGS.
  * __Spawn Scout (Scattered)__: This option allows a Scout to be spawned along with villagers on game start.

  ![image](resources/images/mod_selection-nomad.png)


## Settings
![image](resources/images/mod_settings.png)

## Development

### Adding New Civilization Variants

When Age of Empires IV releases new civilization variants (like Historical Adversary civilizations), you need to update the mod's blueprint files to support them. Here's how to do it:

#### Required Updates

##### 1. Update `ags_blueprints.scar`

This is the main file that needs to be updated. You'll need to add entries to **four different tables**:

###### A. AGS_ENTITY_TABLE
Add the new civilization entry with all building and unit blueprints:
```lua
civilization_name = {
    castle = "building_defense_keep_civ_variant",
    town_center_capital = "building_town_center_capital_civ_variant",
    town_center = "building_town_center_civ_variant",
    villager = "unit_villager_1_civ_variant",
    scout = "unit_scout_1_civ_variant",
    -- ... (continue with all required blueprints)
},
```

###### B. Civilization Constants
Add constants for the new civilization:
```lua
AGS_CIV_CIVILIZATION_NAME = "civilization_name"
```

###### C. AGS_CIV_PREFIXES
Add prefix mapping for the civilization:
```lua
civilization_name = "civ_prefix_",
```

###### D. AGS_UPGRADE_CORRECTION_TABLE
Add an entry (can be empty initially):
```lua
civilization_name = {
    -- Add any upgrade corrections if needed
},
```

###### E. AGS_UPGRADE_TABLE
Add upgrade structure for all ages:
```lua
civilization_name = {
    AGE_DARK = {
        -- Add Dark Age upgrades
    },
    AGE_FEUDAL = {
        -- Add Feudal Age upgrades
    },
    AGE_CASTLE = {
        -- Add Castle Age upgrades
    },
    AGE_IMPERIAL = {
        -- Add Imperial Age upgrades
    },
},
```

#### Important Naming Guidelines

1. **Consistency**: The civilization name key must match exactly what the game expects
2. **Alphabetical Order**: Insert new civilizations in alphabetical order within each table
3. **Blueprint Naming**: Follow the existing pattern for blueprint names
4. **Variants**: Historical Adversary civilizations typically use `_ha_` suffix (e.g., `byzantine_ha_mac`)

#### Example: Adding "Golden Horde" (mongol_ha_gol)

```lua
-- In AGS_ENTITY_TABLE
mongol_ha_gol = {
    castle = "building_defense_keep_control_nov_ha_gol",
    town_center_capital = "building_town_center_capital_mon_ha_gol",
    villager = "unit_villager_1_mon_ha_gol",
    -- ... continue with all blueprints
},

-- Constants
AGS_CIV_MONGOL_HA_GOL = "mongol_ha_gol"

-- Prefixes
mongol_ha_gol = "mon_ha_gol_",

-- Upgrade tables (both correction and main)
mongol_ha_gol = {
    -- Empty or with specific upgrades
},
```

#### Debugging Tips

1. **Build Errors**: Check the Content Editor output panel for build errors
2. **Runtime Errors**: Look for "attempt to index a nil value" errors - these usually indicate missing table entries
3. **Blueprint Names**: Verify blueprint names match the game's internal names
4. **Case Sensitivity**: Ensure exact case matching for all civilization names

#### Files to Update

- **Primary**: `assets/scar/helpers/ags_blueprints.scar`
- **Testing**: Use Content Editor's "Build and Launch" or build manually and test in-game

This process ensures the Advanced Game Settings mod remains compatible with new AOE4 content updates.

### Debugging the Mod

#### Prerequisites

1. **Enable Developer Mode**: Add `-dev` as a launch parameter in Steam
   - Right-click Age of Empires IV in Steam Library
   - Select "Properties"
   - In "Launch Options" field, add: `-dev`
   - Click "OK"

#### Setting Up Debugging Environment

##### 1. Content Editor Setup
1. **Open your mod project** in the Age of Empires IV Content Editor
2. **Load all SCAR files** you want to debug
3. **Set breakpoints** by clicking in the left margin of any line in your SCAR files
   - A red dot will appear indicating the breakpoint is set
   ![alt text](resources/images/content-editor-debug-breakpoint.png)
   - You can set multiple breakpoints across different files

##### 2. Building the Mod
1. In Content Editor, go to **Build menu**
2. Select **"Build Mod"** (not "Build and Launch" - this can be unreliable)
3. Check the **Output panel** for any build errors
4. Fix any errors before proceeding

##### 3. Installing the Local Mod
1. **Launch Age of Empires IV** normally through Steam
2. Create a custom game
3. Select the Mods tab
4. Look for your mod in the list - it will have a **red icon** indicating it's a local/development mod
5. Select your local mod

#### Live Debugging Process

##### Prerequisites ####

To enable the menu buttons for attaching a debug session and controlling execution, right-click the menu bar whitespace and ensure ScriptEditor.Debugging is enabled.

  ![alt text](resources/images/content-editor-menu-debugging.png)

##### 1. Setting Up a Debug Session
1. **Create a custom game** with your mod enabled
2. **Configure game settings** to trigger the code you want to debug
3. **Start the game**
4. When execution hits your breakpoints:
   - Game will pause
   - Content Editor will become active
   - You can inspect variables and step through code

##### 2. Attach to the Live Game Session
1. After launching the game with the `-dev` launch parameter, click the Attach debug menu button to attach to the local Lua console:

    ![alt text](resources/images/content-editor-attach-button.png)

##### 3. Debugging Controls
- **Step Over (F10)**: Execute current line and move to next
- **Step Into (F11)**: Enter function calls to debug them
- **Step Out (Shift+F11)**: Exit current function
- **Continue (F5)**: Resume execution until next breakpoint
- **Stop Debugging**: End the debug session

#### Common Debugging Scenarios

##### Runtime Errors
```lua
-- Add debug prints to trace execution
AGS_Print("Debug: player_civ = " .. tostring(player_civ))
AGS_Print("Debug: bp_type = " .. tostring(bp_type))

-- Check for nil values before using them
if AGS_ENTITY_TABLE[player_civ] ~= nil then
    return BP_GetEntityBlueprint(AGS_ENTITY_TABLE[player_civ][bp_type])
else
    AGS_Print("ERROR: Unknown civilization: " .. tostring(player_civ))
end
```

##### Table Inspection
Set breakpoints and use the **Locals** panel to inspect any local variables within the scope of any breakpoint. You can also use the Globals panel and set Watch variables where desired.

##### Log File Analysis
If debugging doesn't work, check log files:
- **Warnings**: `%USERPROFILE%\Documents\My Games\Age of Empires IV\warnings.log`
- **SCAR logs**: `%USERPROFILE%\Documents\My Games\Age of Empires IV\LogFiles\`


## Feedback & Contribution & Donations:
Contribution in any form is welcomed. Be free to also provide ideas or requests via issues/tickets.

## Bug & other issues:
Verify that you are using mod published by Joshua Sachtleben.
![image](resources/images/mod_header.png)

Once you have verified that you are using correct version of the mod and issue persists.
Create a issue and try to provide as much information as possible.
Ideally all of the following:
- [ ] Platform (PC, Xbox, etc.)
- [ ] Amount of PLAYERS & AI's and their teams.
- [ ] Map, seed, biome, gamemode (as there is multiple AGS gamemodes).
- [ ] **All OPTIONS used in the match.**
- [ ] Tuning pack used.
- [ ] What happened before the crash or bug.

In case of any crash, the `C:\Users\%USERNAME%\Documents\My Games\Age of Empires IV\warnings.log` file contains report from scar (script) crashes and will help resolve the issue. Optionally, the `C:\Users\%USERNAME%\Documents\My Games\Age of Empires IV\LogFiles` directory contains logs that, in some cases, might contain additional information that might help for a problem to be resolved. Most information is logged in scarlog and warnings.

### Known Issues

#### AI

Age of Empires IV does not have a dedicated API for AI. As a result, any issue related to AI behaviour cannot be fixed. Any behavior such as AI aging up even if players can't, AI being slower then expected to age up, AI plays/behaves worse then in standard game, etc. is not possible to address with modded content currently.

For some reason, AI doesn't like gamemode/script changes and plays worse then usual. The root cause of this is currently unknown. I suggest you to provide feedback to Relic, so they can improve AI or provide official API.

#### King Unit

Currently, there is issue where the King is T-Posing on death. This issue can't be fixed in the mod, as this is currently only Game Mode scripting.

## FAQ
* Mod Localization

  If you can provide translation, it will be incorporated into the mod. Current english database is [here](https://github.com/joshuasachtleben/AOE4-AdvancedGameSettings/blob/master/assets/locdb/Advanced%20Game%20Settings_en.csv). If you want to test localization on local version of the mod, you can use this [cheatsheet image to add entry to localization database.](https://github.com/joshuasachtleben/AOE4-AdvancedGameSettings/blob/master/resources/GUIDE%20TO%20NEW%20LOCALIZATION.png)

* How does the vision work and which option affects it ?

  Team Vision is currently still tied to Team Victory [Basically determined by who can win the game]
    - __Team Victory__ > __FFA & Team Vision__ > __Any__:

      No one will have vision during treaty or during the game for any of their mutual "allies"

  - __Team Victory__ > __Initial Teams & Team Vision__ > __Requires Market/Always__:
  
    Only teams setup in lobby will share vision during the game, including treaty

  - __Team Victory__ > __Dynamic Teams & Team Vision__ > __Requires Market/Always__:
  
    Everyone has vision during treaties and mutual allies see each other

## Resources

* Age of Empires IV Mod Page:

  https://www.ageofempires.com/mods/details/224580/

* Age of Empires Modding Discord:

  https://discord.gg/h8FX9Uq3vG
