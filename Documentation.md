# File Summary

## Purpose
This file contains a packed representation of the entire repository's contents.
It is designed to be easily consumable by AI systems for analysis, code review,
or other automated processes.

## File Format
The content is organized as follows:
1. This summary section
2. Repository information
3. Directory structure
4. Multiple file entries, each consisting of:
  a. A header with the file path (## File: path/to/file)
  b. The full contents of the file in a code block

## Usage Guidelines
- This file should be treated as read-only. Any changes should be made to the
  original repository files, not this packed version.
- When processing this file, use the file path to distinguish
  between different files in the repository.
- Be aware that this file may contain sensitive information. Handle it with
  the same level of security as you would the original repository.

## Notes
- Some files may have been excluded based on .gitignore rules and Repomix's configuration
- Binary files are not included in this packed representation. Please refer to the Repository Structure section for a complete list of file paths, including binary files
- Files matching patterns in .gitignore are excluded
- Files matching default ignore patterns are excluded
- Security check has been disabled - content may contain sensitive information

## Additional Info

# Directory Structure
```
docs/
  intellisense.lua
README.md
```

# Files

## File: docs/intellisense.lua
```lua
----------------------------------------
--- // Info
----------------------------------------

--[[
    This file contains every Addon Lua function, callback, and type.
    Simply put this file in your code workspace and you should have intellisense support (auto-completion, etc) for Addon Lua.

    This extension is required: https://marketplace.visualstudio.com/items?itemName=sumneko.lua

    Created by: @nameouschangey (GitHub) and @Toast732 (GitHub)
    Maintained by: @Cuh4 (GitHub)

    Repo: https://github.com/Cuh4/StormworksAddonLuaDocumentation
]]

----------------------------------------
--- // Changelog
----------------------------------------

--[[
    Last updated for game version: v1.13.4 (The Viewing Scope Update)
        Note that even if the above version is outdated, updates to this may still be applied (usually corrections).

    The following changelog entries are in DD/MM/YY format.

    -- 15/01/2024
        - Added `group_id` return value to `server.spawnAddonVehicle` and `server.spawnVehicle` as the new game update v1.13.4 now returns the vehicle group ID with the aforementioned functions.

    -- 30/10/2024
        - Fix `server.getVehicleSign` and `server.getVehicleSeat` having their `name` parameter hinted as a number instead of a string

    -- 02/09/2024
        - Fix `server.spawnVolcano` having an invalid number of arguments too (again, `magnitude` argument doesn't exist)
        - Fix `server.spawnTornado` having an invalid number of arguments (`magnitude` argument doesn't exist)

    -- 28/08/2024
        - `SWGameSettingEnum` and `SWGameSettings` are now up-to-date
        - Fixed `SWGameSettingEnum` using `---@class` instead of `---@alias`

    -- 17/08/2024
        - Fixed up `server.setAIState` `AI_STATE` parameter description. It didn't cover all AI states
        - Made `server.setCreatureTooltip` an alias instead of it having its own function

    -- 14/08/2024
        - Added the new lobsters and crabs to `SWEquipmentTypeEnum`
        - Fixed incorrect `SWNotificationTypeEnum` names
        - Fixed `SWNotificationTypeEnum` being spelt as `SWNotifiationTypeEnum`

    -- 03/08/2024
        - Changed overall structure for tidying reasons.

    -- 02/08/2024
        - Updated SWRopeTypeEnum.
        - Added description comments to server, property, debug, etc

    -- 04/07/2024
        - Replaced "--- " with "-- ". Personal preference yet again

    -- 03/07/2024
        - Replaced "-- @" with "---@" as it's my personal preference and it's pretty much the standard
        - Added server.getVehiclesByName()
        - Added SWVehicleAuthor class
        - Updated vehicle class for v1.11.6 (add "name" and "authors" field)

    -- 19/06/2024
        - Fixed matrix.rotationToFaceXZ return type should be SWMatrix

    -- 14/06/2024
        - Added missing fluid types to SWTankFluidTypeEnum

    -- 07/06/2024
        - Added `---@meta _` see https://luals.github.io/wiki/annotations/#meta

    -- 12/05/2024
        - Switched around server.setCharacterSeated and server.setSeated (server.setSeated is no longer an alias but the actual thing)
        - Added server.setCreatureSeated as an alias of server.setSeated

    -- 08/05/2024
        - Added descriptions for server.spawnTornado, server.spawnMeteor, server.spawnMeteorShower, server.spawnVolcano, server.getVolcanos, server.spawnWhirlpool, server.spawnTsunami
        - Added server.getFishData, server.getFishHotspots
        - Added SWFishData and SWFishHotSpotData classes
        - Int states for fish equipment types are now shown in the equipment type description

    -- 06/05/2024
        - Rename SWOreTypeEnum to SWResourceTypeEnum
        - Add missing resources to SWResourceTypeEnum (solid_propellant and fishes)

    -- 05/05/2024
        - Fix description for server.getWeather

    -- 26/04/2024
        - General formatting fixes

    -- 25/04/2024
        - Add ---@deprecated tag to all undocumented hidden alias functions

    -- 24/04/2024
        - Added creature_type, interactable, and animal_type fields to SWAddonComponentData (From v1.10.10 update)

    -- 23/04/2024
        - Added server.setSeated alias for server.setCharacterSeated
        - Removed function descriptions for alias functions

    -- 19/04/2024
        - Fixed SWVehicleComponents class

    -- 12/04/2024
        - Add solid_propellant parameter to server.setTileInventory()
        - Added missing argument for server.spawnMeteor(), is_spawn_tsunami

    -- 28/03/2024
        - Added documentation for server.clearOilSpill()
        - Added documentation for callback onClearOilSpill()
        - Added solid_propellant return annotation for server.getTileInventory()

    -- 02/03/2024
        - Fix return annotation for server.spawnVehicle (group_id --> primary_vehicle_id)

    -- 21/02/2024
        - Add missing documentation for server.spawnMeteorShower

    -- 15/02/2024
        - Documented hidden undocumented functions. They are mainly aliases of existing functions
            These undocumented functions are untested. I found them in "_ENV.server", but I've never used them.
            This means they might not even be callable, they do nothing, or I may have aliased it to the wrong function
            
        - Removed "BUG REPORT" text, couldn't find hyperlink for it

    -- 01/02/2024
        - Added drill_rod and fishing_lure to object type enum
        - Added new map label types to map label type enum
        - Added new equipment types to equipment type enum

    -- 02/01/2024
        - Added missing object_id attribute to the SWPlayer class.

    -- 18/12/2023
        - Fixed return annotation for server.spawnAddonVehicle being "group_id" and not "vehicle_id"
        - Added missing is_success return annotation for server.getVehicleGroup

    -- 12/12/2023
        - Added server.dlcSpace(), forgot to add it earlier

    -- 30/11/2023
        - Fixed server.spawnAddonVehicle docs
        - Fixed server.spawnVehicle docs
        - Removed server.getVehicleName
]]

----------------------------------------
--- // Main
----------------------------------------

---@meta _

-------------------
-- Definitions
-------------------

--[[
    A table containing most of addon lua's functions.

    server.announce("Server", "Hello World")
]]
server = {}

--[[
    A table containing functions that can be used for making your addon easily customizable by the user.<br>
    Functions in this table must be saved in g_savedata.

    g_savedata = {
        example = property.checkbox("Example", false), -- defaults to false, name is "Example"
        ... -- anything else you want in g_savedata
    }
]]
property = {}

--[[
    A table containing functions that can be used for creating and manipulating matrices.<br>

    local myMatrix = matrix.translation(0, 0, 0)
    local x, y, z = matrix.position(myMatrix)

    print(x, y, z) -- 0, 0, 0
  ]]
matrix = {}

--[[
    A table containing debug-related functions. Only `debug.log` exists for now.<br>

    debug.log("Hello World")
]]
debug = {}

--[[
    A table used for saving numbers, strings, and booleans across addon reloads and sessions.<br>
    Only access g_savedata after `onCreate` is called, otherwise values won't be what is expected.

    g_savedata = {
        example = "Hello World"
    }
    
    function onCreate(is_create)
        print(g_savedata.example) -- "Hello World"
    end
]]
g_savedata = {}

-------------------
-- Matrices
-------------------

---@class SWMatrix
---@field [1] number
---@field [2] number
---@field [3] number
---@field [4] number
---@field [5] number
---@field [6] number
---@field [7] number
---@field [8] number
---@field [9] number
---@field [10] number
---@field [11] number
---@field [12] number
---@field [13] number x
---@field [14] number y
---@field [15] number z
---@field [16] number

-- Multiplies two matrices together
---@param matrix1 SWMatrix
---@param matrix2 SWMatrix
---@return SWMatrix matrix
function matrix.multiply(matrix1, matrix2) end

-- Inverts the matrix
---@param matrix SWMatrix
---@return SWMatrix matrix
function matrix.invert(matrix) end

-- Transposes a matrix
---@param matrix SWMatrix
---@return SWMatrix matrix
function matrix.transpose(matrix) end

-- Returns an identity matrix
---@return SWMatrix matrix
function matrix.identity() end

-- Converts radians to the x axis rotation in a matrix. Doesn't rotate the orientation. Rotates the point around the center of the world (0,0,0)
---@param radians number The angle in radians you want to convert
---@return SWMatrix matrix
function matrix.rotationX(radians) end

-- Converts radians to the y axis rotation in a matrix
---@param radians number The angle in radians you want to convert
---@return SWMatrix matrix
function matrix.rotationY(radians) end

-- Converts radians to the z axis rotation in a matrix
---@param radians number The angle in radians you want to convert
---@return SWMatrix matrix
function matrix.rotationZ(radians) end

-- Returns your x,y,z points as a matrix
---@param x number
---@param y number
---@param z number
---@return SWMatrix matrix
function matrix.translation(x, y, z) end

-- Returns x,y,z when given a matrix
---@param matrix SWMatrix returns the location tuplets from the matrix provided. this is the same as MATRIX[13],MATRIX[14],MATRIX[15]
---@return number x, number y, number z
function matrix.position(matrix) end

-- Returns the distance in meters between two matrices in 3D space
---@param matrix1 SWMatrix The first matrix
---@param matrix2 SWMatrix The second matrix
---@return number dist
function matrix.distance(matrix1, matrix2) end

-- Multiplies a matrix by a vec 4.
---@param matrix1 SWMatrix The matrix to multiply
---@param x number
---@param y number
---@param z number
---@param w number
---@return number out_x, number out_y, number out_z, number out_w
function matrix.multiplyXYZW(matrix1, x, y, z, w) end

-- Returns the rotation required to face an X Z vector
---@param x number
---@param z number
---@return SWMatrix required_rotation
function matrix.rotationToFaceXZ(x, z) end

-------------------
-- Callbacks
-------------------

-- Called when all oil spills are cleared
function onClearOilSpill() end

-- called every game tick
---@param game_ticks number the number of ticks since the last onTick call (normally 1, while sleeping 400.)
function onTick(game_ticks) end

-- Called when the script is initialized (whenever creating or loading a world.)
---@param is_world_create boolean Only returns true when the world is first created.
function onCreate(is_world_create) end

-- Called when the world is exited.
function onDestroy() end

-- Called when a command is entered into chat, does not trigger if sent by server.
---@param full_message string The full message that was sent
---@param peer_id number The peer ID of the player who sent the message
---@param is_admin boolean If the player who entered the command has admin
---@param is_auth boolean If the player who entered the command is authenticated
---@param command string The command the player sent (ex: player entered "?help me", command will be "?help")
---@param ... string The rest of the args of the command, can be packed into a table with "arg = table.pack(...)" and referenced with "arg[1]", "arg[2]", ect
function onCustomCommand(full_message, peer_id, is_admin, is_auth, command, ...) end

-- Called when a message is sent to the chat, does not trigger if sent by server.
---@param peer_id number The peer ID of the player who sent the message
---@param sender_name string The name of the player who sent the message
---@param message string The message that was sent
function onChatMessage(peer_id, sender_name, message) end

-- Called when a player joins the game.
---@param steam_id number The player's Steam ID (convert to string as soon as possible to prevent loss of data)
---@param name string The player's name
---@param peer_id number The player's peer ID
---@param is_admin boolean If the player has admin
---@param is_auth boolean If the player is authenticated
function onPlayerJoin(steam_id, name, peer_id, is_admin, is_auth) end

-- Called when a player sits in a seat.
---@param peer_id number The peer ID of the player who sat in the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onPlayerSit(peer_id, vehicle_id, seat_name) end

-- Called when a player gets out of the seat.
---@param peer_id number The peer ID of the player who got out of the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onPlayerUnsit(peer_id, vehicle_id, seat_name) end

-- Called when any character (including players) sits in a seat.
---@param object_id number The object ID of the character which sat in the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onCharacterSit(object_id, vehicle_id, seat_name) end

-- Called when any character (including players) get out of a seat.
---@param object_id number The object ID of the character which sat in the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onCharacterUnsit(object_id, vehicle_id, seat_name) end

-- Called whenever any character (including players) picks up a character (including players).
---@param object_id_actor number the object id of the object which picked up the character
---@param object_id_target number the object id of who was picked up
function onCharacterPickup(object_id_actor, object_id_target) end

-- Called when any creature sits in a seat.
---@param object_id number The object ID of the creature which sat in the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onCreatureSit(object_id, vehicle_id, seat_name) end

-- Called when any creature gets gets out of a seat.
---@param object_id number The object ID of the character which sat in the seat
---@param vehicle_id number The vehicle ID of the vehicle which the seat belongs to
---@param seat_name string The name of the seat
function onCreatureUnsit(object_id, vehicle_id, seat_name) end

-- Called whenever any character (including players) pick up a creature.
---@param object_id_actor number the object id of the object which picked up the creature
---@param object_id_target number the object id of who was picked up
function onCreaturePickup(object_id_actor, object_id_target) end

-- Called when a character (including players) picks up an equipment item
---@param character_object_id number the object_id of the character
---@param equipment_object_id number the object_id of the equipment item
---@param EQUIPMENT_ID SWEquipmentTypeEnum the equipment_id of the item which was picked up.
function onEquipmentPickup(character_object_id, equipment_object_id, EQUIPMENT_ID) end

-- Called when a character (including players) drops an equipment item
---@param character_object_id number the object_id of the character
---@param equipment_object_id number the object_id of the equipment item
---@param EQUIPMENT_ID SWEquipmentTypeEnum the equipment_id of the item which was dropped.
function onEquipmentDrop(character_object_id, equipment_object_id, EQUIPMENT_ID) end

-- Called whenever a player respawns.
---@param peer_id number The peer ID of the player who respawned
function onPlayerRespawn(peer_id) end

-- Called when a player leaves the game.
---@param steam_id number The player's Steam ID (convert to string as soon as possible to prevent loss of data.)
---@param name string The player's name.
---@param peer_id number The player's peer ID.
---@param is_admin boolean If the player had admin.
---@param is_auth boolean If the player was authenticated.
function onPlayerLeave(steam_id, name, peer_id, is_admin, is_auth) end

-- Called when a player opens/closes the map.
---@param peer_id number The player's peer ID
---@param is_open boolean false if the map was closed, true if the map was opened
function onToggleMap(peer_id, is_open) end

-- Called when a player dies.
---@param steam_id number The player's Steam ID (convert to string as soon as possible to prevent loss of data.)
---@param name string The player's name.
---@param peer_id number The player's peer ID.
---@param is_admin boolean If the player has admin.
---@param is_auth boolean If the player is authenticated.
function onPlayerDie(steam_id, name, peer_id, is_admin, is_auth) end

-- Called when a vehicle is spawned.
---@param vehicle_id number The vehicle ID of the vehicle that was spawned.
---@param peer_id number The peer ID of the player who spawned the vehicle, -1 if spawned by the server.
---@param x number The x coordinate of the vehicle's spawn location relative to world space.
---@param y number The y coordinate of the vehicle's spawn location relative to world space.
---@param z number The z coordinate of the vehicle's spawn location relative to world space.
---@param group_cost number The cost of the group this vehicle belongs to.
---@param group_id number The ID of the group this vehicle belongs to
function onVehicleSpawn(vehicle_id, peer_id, x, y, z, group_cost, group_id) end

-- Called when a group is spawned.
---@param group_id number The group_cost ID of the group that was spawned.
---@param peer_id number The peer ID of the player who spawned the group, -1 if spawned by the server.
---@param x number The x coordinate of the group's spawn location relative to world space.
---@param y number The y coordinate of the group's spawn location relative to world space.
---@param z number The z coordinate of the group's spawn location relative to world space.
---@param group_cost number The cost of the group
function onGroupSpawn(group_id, peer_id, x, y, z, group_cost) end

-- Called when a vehicle is despawned.
---@param vehicle_id number the vehicle ID of the vehicle that was despawned.
---@param peer_id number The peer ID of the player who despawned the vehicle, -1 if despawned by the server.
function onVehicleDespawn(vehicle_id, peer_id) end

-- Called when a vehicle is loaded 
