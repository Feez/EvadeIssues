# DreamEvade (Alpha) API 

```lua
_G.DreamEvade.IsEvadeEnabled()
```
Description:
- Returns whether DreamEvade is currently enabled from the menu settings.

Returns:
- `boolean`

# 

```lua
_G.DreamEvade.HasPath()
```
Description:
- Returns whether DreamEvade is currently following a path to evade skillshots.

Returns:
- `boolean`

# 

```lua
_G.DreamEvade.IsPathSafe(path, speed, delay)
```
Description:
- Returns whether a path is safe to travel upon.

Arguments:
- `path` : table of positions with `x`, `z` properties (most likely starting with `myHero.position`)
- `speed` : movement speed at which to travel the entire path (default `myHero.characterIntermediate.movementSpeed`)
- `delay` : delay (seconds) before beginning path travel (default `0`)

Returns:
- `boolean` : whether is safe (given current evade settings)
- `table (array)` : table of *unique* spells that hit

# 

```lua
_G.DreamEvade.IsPositionSafe(position, delay)
```
Description:
- Returns whether given position is safe after delay.
    - **Note** - only checks the single position, not the path to get there.

Arguments:
- `position` : position with `x`, `z` properties
- `delay` : delay (seconds) before position arrive at position (default `0`)

Returns:
- `boolean` : whether is safe (given current evade settings)
- `table (array)` : table of *unique* spells that hit


# 

```lua
_G.DreamEvade.Update()
```
Description
- Used to tell DreamEvade that the situation has changed, it needs to reconsider
any movements & re-calc path. **Don't use this unless you are confident DreamEvade cannot detect change of
circumstance (i.e. if you are all of the sudden teleported to a different dimension with the same coordinates)**.

#

```lua
_G.DreamEvade.ActiveSpells -- Spell[]
_G.DreamEvade.DangerousSpells -- Spell[]
```
Description:
- Active spells : all active spells (even far away)
- Dangeorus spells : all spells that evade has not figured out how to dodge (colored red)

# Spell API #

```lua
local Spell = class()

--////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
--////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

--[[ Functions you might use ]]

function Spell:IsEvadeEnabled()
end

function Spell:IsActive()
end

---@param pos Vector
---@param time_to_point Delay before hero arrives at position
---@param hero_ms Movement speed of hero (used for determining if can get out of spell area)
function Spell:IsSafe(pos, time_to_point, hero_ms)
end

function Spell:GetDangerLevel()
end

---@param pos Vector
function Spell:IsPositionInSpellArea(pos)
end

function Spell:IsCC()
end

--////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
--////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

--[[ Extras ]]

function Spell:IsFOWMissileEnabled()
end

function Spell:IsFOWParticleEnabled()
end

function Spell:MatchesMissileName(name)
end

function Spell:ForceDisable(bool)
end

function Spell:IsForceDisabled()
end

function Spell:IsWall()
end

function Spell:IsSkillshot()
end

function Spell:IsMissile()
end

-- Marks a skillshot as red
function Spell:OhShit(bool)
end

-- Marks a skillshot as yellow
function Spell:SetIgnore(bool)
end

-- Is skillshot yellow
function Spell:IsIgnored()
end

-- Is skillshot red
function Spell:IsOhShit()
end
```
