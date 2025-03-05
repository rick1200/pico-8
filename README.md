# Pico-8

### How to cycle through frames for animation

```lua
function _update()
  -- Increment the frame timer by one on every frame update.
  player.frame_timer = player.frame_timer + 1
  
  -- Check if enough frames have passed to change the animation frame.
  if player.frame_timer >= player.frame_delay then
    -- Increase the frame index by 1.
    -- The modulo operator (%) ensures that after frame 3, the index wraps around to 0.
    player.frame = (player.frame + 1) % 4
    
    -- Reset the frame timer so the delay can start over.
    player.frame_timer = 0
  end
end
```
<br>

### Basic game loop and sprite movement

```lua
-- initialize player table with position and speed
player = {
  x = 64,
  y = 64,
  speed = 1
}

-- _update is called every frame to update game logic
function _update()
  -- btn(index) returns true if a button is held down
  if btn(0) then player.x -= player.speed end
  if btn(1) then player.x += player.speed end
  if btn(2) then player.y -= player.speed end
  if btn(3) then player.y += player.speed end
end

-- _draw is called every frame to render the screen
function _draw()
  cls()              -- clear the screen
  spr(1, player.x, player.y)  -- draw sprite number 1 at player's position
end

```
<br>

### Collision detection

```lua
-- Collision Detection Example

function _init()
  player = { x = 60, y = 60, w = 8, h = 8, speed = 2 }
  enemy = { x = 80, y = 80, w = 8, h = 8 }
end

-- Function to check for collision between two rectangles
function check_collision(a, b)
  return a.x < b.x + b.w and
         b.x < a.x + a.w and
         a.y < b.y + b.h and
         b.y < a.y + a.h
end

function _update()
  if btn(0) then player.x -= player.speed end
  if btn(1) then player.x  += player.speed end
  if btn(2) then player.y -= player.speed end
  if btn(3) then player.y += player.speed end
  
  if check_collision(player, enemy) then
    -- Print a collision message; note that print draws text for one frame only
    print("Collision!", 40, 60, 8)
  end
end

function _draw()
  cls(0)
  -- Draw player (color 11)
  rectfill(player.x, player.y, player.x + player.w, player.y + player.h, 11)
  -- Draw enemy (color 8)
  rectfill(enemy.x, enemy.y, enemy.x + enemy.w, enemy.y + enemy.h, 8)
end

```
<br>

### Playing a sound effect

```lua
-- Sound Effect Example

function _init()
  player = { x = 60, y = 60, w = 8, h = 8, speed = 2 }
end

function _update()
  if btn(0) then player.x = player.x - player.speed end
  if btn(1) then player.x = player.x + player.speed end
  if btn(2) then player.y = player.y - player.speed end
  if btn(3) then player.y = player.y + player.speed end
  
  -- Check if player touches the screen boundaries (0 to 128 for Pico-8)
  if player.x < 0 or player.x > 120 or player.y < 0 or player.y > 120 then
    sfx(0)  -- play sound effect with ID 0
  end
end

function _draw()
  cls(0)
  rectfill(player.x, player.y, player.x + player.w, player.y + player.h, 10)
end

```
