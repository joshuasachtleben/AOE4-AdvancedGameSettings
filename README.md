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
![image](resources\images\mod_settings-header.png)

* __City-State Wars__: Game mode that pitches players to fight without any civilization bonus. To obtain advantage players have to capture cities spread in a grid like shape around the map.
![image](resources\images\mod_selection-city_state_wars.png)

* __Nomad__: Game mode where players start out with villagers spread out across the map without a Town Center or Scout. They must build their first Town Center at no cost which becomes their landmark Town Center. The standard tech tree unlocks upon Town Center creation.
Additional Options for Nomad AGS.
  * __Spawn Scout (Scattered)__: This option allows a Scout to be spawned along with villagers on game start.

  ![image](resources\images\mod_selection-nomad.png)


## Settings
![image](resources\images\mod_settings.png)

## Feedback & Contribution & Donations:
Contribution in any form is welcomed. Be free to also provide ideas or requests via issues/tickets.

## Bug & other issues:
Verify that you are using mod published by Joshua Sachtleben.
![image](resources\images\mod_header.png)

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

> [!CAUTION]
> ### Known Issues
> #### AI
> Age of Empires IV does not have a dedicated API for AI. As a result, any issue related to AI behaviour cannot be fixed. Any behaviour such as AI aging up even if players can't or AI being slower then expected to age up or plays/behaves worse then in standard game is out of reach to fix with modded content currently.
>
> For some reason, AI doesn't like gamemode/script changes and plays worse then usual. The root cause of this is currently unknown. I suggest you to provide feedback to Relic, so they can improve AI or provide official API.
>
> #### King Unit
> Currently, there is issue where the King is T-Posing on death. This issue can't be fixed in the mod, as this is currently only Game Mode scripting.

## FAQ
* Can I use anything from this mod for another mod?
Yes as long as you are doing more than minimal amount of changes or your mod isn't suitable to be add to Advanced Game Settings as an option.

* I have this cool idea!
Create ticket, and let's coordinate!

* Mod Localization to other languages
If you can provide translation, it will be incorporated into the mod. Current english database is [here](https://github.com/joshuasachtleben/AOE4-AdvancedGameSettings/blob/master/assets/locdb/Advanced%20Game%20Settings_en.csv). If you want to test localization on local version of the mod, you can use this [cheatsheet image to add entry to localization database.](https://github.com/joshuasachtleben/AOE4-AdvancedGameSettings/blob/master/resources/GUIDE%20TO%20NEW%20LOCALIZATION.png)

* How does the vision work and which option affects it ?
Team Vision is currently still tied to Team Victory [Basically determined by who can win the game]
  - Team Victory -> FFA & Team Vision -> Any => Noone will have vision during treaty or during the game for any of their mutual "allies"
  - Team Victory -> Initial Teams & Team Vision -> Requires Market/Always => Only teams setup in lobby will share vision during the game, including treaty
  - Team Victory -> Dynamic Teams & Team Vision -> Requires Market/Always => everyone has vision during treaties and mutual allies see each other

* Age of Empires IV mod page link:
https://www.ageofempires.com/mods/details/224580/