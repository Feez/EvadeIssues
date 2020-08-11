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
_G.DreamEvade.IsPathSafe(path, speed)
```
Description:
- Returns whether a path is safe to travel upon.

Arguments:
- `path` : table of positions with `x`, `z` properties (most likely starting with `myHero.position`)
- `speed` : movement speed at which to travel the entire path (default `myHero.characterIntermediate.movementSpeed`)

Returns:
- `boolean`

# 

```lua
_G.DreamEvade.IsPositionSafe(position, delay)
```
Description:
- Returns whether given position is safe after delay.
    - **Note** - only checks the single position, not the path to get there.

Arguments:
- `position` : position with `x`, `z` properties
- `delay` : number representing delay before position arrive at position (default `0`)

Returns:
- `boolean`


# 

```lua
_G.DreamEvade.Update()
```
Description
- Used to tell DreamEvade that the situation has changed, it needs to reconsider
any movements & re-calc path. **Don't use this unless you are confident DreamEvade cannot detect change of
circumstance (i.e. if you are all of the sudden teleported to a different dimension with the same coordinates)**.
