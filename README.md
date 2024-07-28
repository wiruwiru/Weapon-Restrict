# Weapon Restrict
The plugin allows you to restrict the use of certain weapons depending on the players in the teams or the total number of players, as well as the number of specified weapons. You can also set administrators' immunity to restrictions

## Installation
1. Install [CounterStrike Sharp](https://github.com/roflmuffin/CounterStrikeSharp) and [Metamod:Source](https://www.sourcemm.net/downloads.php/?branch=master)

2. Download [Weapon_Restrict.zip](https://github.com/wiruwiru/Weapon-Restrict/releases) from the releases section.

3. Unzip the archive and upload it to the game server

4. Start the server and wait for the Config.json and RestrictConfig.json files to be generated.

- Configuration files will be generated after the plugin is launched in the folder `addons/counterstrikesharp/plugins/Weapon_Restrict`:
	- `Config.json`				- Common settings
	- `RestrictConfig.json`		- Restrictions settings

## Configs

### Config.json
```
{
	"Tag": "{GOLD}[WeaponRestrict] ",		// Tag before text of plugin
	"DestinationTypeRestrictMessage": 1,	// Specifies how the prohibition message will be displayed	[ 1 - chat | 2 - center]
	"DestinationTypeRefundMessage": 1,	// Specifies how the refund message will be displayed
	"RestrictMessageText": "{TAG}{DEFAULT}Weapon {OLIVE}{WEAPON}{DEFAULT} is {DARKRED}restricted{DEFAULT} to {GREEN}{COUNT}{DEFAULT} at the moment", // Restrict message
	"RestrictMessageStatus": true,					// Indicates whether the restrict message is enabled		[ true - on | false - off]
	"RefundMessage": "{TAG}Money redunded {GOLD}{MONEY}",	// Refund message
	"RefundMessageStatus": true,						// Indicates whether the refund message is enabled			[ true - on | false - off]
	"RestrictMethod": 2,								// Method of restricting [ 1 - by players of team | 2 - by weapons count | 3 - by total players ]
	"AdminImmunityFlag": "@css/root"				// Admin-flag to enable immunity for player. Admin list can be finded here:`addons/counterstrikesharp/configs/admins.json`
}
```
### RestrictConfig.json
```
{
	"Weapon": "weapon_deagle",	// weapon class for restriction
	"WeaponQuota": {			// using this method if RestrictMethod = 2. Calculated by total weapon count in team
		"CT": 1,					// Allowed deagles to CT-team to 1
		"T": 4						// Allowed deagles to T-team to 4
	},
	"PlayersInTeamQuota": {			// using this method if RestrictMethod = 1. Calculated by players for each team 
		"CT": [					// team
			{
				"4": 0,				// Allowed deagles to CT-team to 0 for 4-7 players
				"8": 4,				// Allowed deagles to CT-team to 4 for 8-15 players
				"16": 7				// Allowed deagles to CT-team to 7 for 16-... players
				// here can add more player conditions using ","
			}
		],
		"T": [					// team
			{
				"4": 3,               // Allowed deagles to T-team to 3 for 4-7 players
				"8": 4,               // Allowed deagles to T-team to 4 for 8-15 players
				"16": 9               // Allowed deagles to T-team to 9 for 16-... players
				// here can add more player conditions using ","
			}
		]
	},
	"PlayersAllQuota": {			// using this method if RestrictMethod = 3. Calculated by Total players in both teams 
		"4": 1,						// Allowed deagles to 1 for 4-7 players
		"8": 2,						// Allowed deagles to 2 for 8-15 players
		"16": 3						// Allowed deagles to 3 for 16-... players
	}
}
// here can add more weapons using ","
```
```diff
- Do not try to copy this jsons into your config. Json does not support commenting! Comments have been added here for your convenience.
```