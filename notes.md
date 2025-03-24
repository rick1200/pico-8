
```lua
function _init()
  enemies = {
    { x=10, y=20, vx=1, vy=0, health=3 },
    { x=30, y=40, vx=-1, vy=0, health=3 }
  }
end
```
* `x` and `y`: Starting coordinates.
* `vx` and `vy`: Velocity (speed).
* `health`: Enemy health.
<br>

```lua
function _update()
  update_enemies()
end
```
* Update enemy positions every frame.
<br>

```lua
function _draw()
  cls()
  --Draw enemies as rectangles
  for i, enemy in ipairs(enemies) do
    rectfill(enemy.x, enemy.y, enemy.x+7, enemy.y+7, 10)
  end
end
```
* `ipairs` iterates over the `enemies` table in order.
* `enemy.x+7, enemy.y+7`: Draws an 8 pixel square.
<br>

```lua
function update_enemies()
  for i, enemy in ipairs(enemies) do
    --Update enemy position
    enemy.x += enemy.vx
    enemy.y += enemy.vy

    --Boundary check
    if enemy.x < 0 or enemy.x > 120 then enemy.vx = -enemy.vx end
  end
end
```
