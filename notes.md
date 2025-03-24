
Let's say we have 2 enemy sprites that we want to display on the screen. We can use a table for this. In Pico 8, a table is similar to an array or a list in other programming languages. We'll start by creating a table called `enemies`:
<br>

```lua

```















<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

```lua
function _init()
  enemies = {
    { x=10, y=20, vx=1, vy=0, health=3, color=8 },
    { x=30, y=40, vx=-1, vy=0, health=3, color=10 }
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
    rectfill(enemy.x, enemy.y, enemy.x+7, enemy.y+7, enemy.color)
  end
end
```
* `ipairs` iterates over the `enemies` table in order.
* `enemy.x+7, enemy.y+7`: Draws an 8 pixel square.
<br>

```lua
function update_enemies()
  for i, enemy in ipairs(enemies) do
    --Update enemy position based on velocity
    enemy.x += enemy.vx
    enemy.y += enemy.vy

    --Boundary check
    if enemy.x < 0 or enemy.x > 120 then enemy.vx = -enemy.vx end
    if enemy.y < 0 or enemy.x > 120 then enemy.vy = -enemy.vy
  end
end
```
