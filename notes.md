
Let's say we have 2 enemy sprites that we want to display on the screen. We can use a table for this. In Pico 8, a table is similar to an array or a list in other programming languages. We'll start by creating a table called `enemies` inside of the `_init()` function:
<br>

```lua
function _init()
  enemies = {

  }
end
```
<br>

Inside of the enemies table, we're going to create 2 additional tables that will contain some properties for each enemy:
* The `x` position of the enemy.
* The `y` position of the enemy.
* The velocity (speed) the enemy will travel horizontally across the screen (`x` speed).
* The velocity (speed) the enemy will travel vertically across the screen (`y` speed).
* The number of the sprite in Pico 8's sprite editor.
<br>
We can add more properties later but this is a good start. Enter the following code inside of the `enemies` table:
<br>

```lua
function _init()
  enemies = {
    { x=10, y=20, dx=1, dy=0, spr=1 }, --sprite number 1
    { x=30, y=40, dx=-1, dy=0, spr=2}  --sprite number 2
  }
end
```
<br>

The `x` and `y` values tell us where the sprites will be placed on the screen when the game starts. Sprite number 1 will travel horizontally toward the right side of the screen, so `dx` is set to a speed of `1`. Now we want sprite number 2 to move horizontally in the opposite direction (to the left side of the screen) so `dx` is set to `-1`. And finally we have the number of the sprite as it is in the sprite editor.

Since the `enemies` table is in the `_init()` function, the table and all of the values are created when the game first starts. 
















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
