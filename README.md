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
