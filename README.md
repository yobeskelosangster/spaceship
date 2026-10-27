# COM415 Game Development Assignment
## 3D Space Flight Game: EverSpace 2 Style

**Student Name:** Yobe Skelo Makobiri  
**Registration Number:** BSC-COM-19-21  
**Course:** COM415 Game Development  
**Tutor:** Francis Kambili-Mzembe  
**Engine:** Godot Engine 4.7 (Forward+ / Mobile)  
**Language:** GDScript  

---

## 1. Project Overview & Architecture
This project is a 3D space flight combat game inspired by **EverSpace 2**, developed for Android and PC using the Godot Engine and GDScript.

### Core Systems & Directory Structure:
- `res://scripts/game_manager.gd`: Autoload singleton controlling game state, ship selection, level transitions, mission timer, and global audio.
- `res://scripts/player/player_ship.gd`: 3D player flight controller featuring smooth arcade physics, dual laser cannons, roll banking, thruster particle effects, and dynamic camera trailing.
- `res://scripts/ai/steering_behaviors_3d.gd`: Autonomous 3D steering behaviors implementing Reynolds Seek, Wander, Path Following, and Raycast Obstacle Avoidance.
- `res://scripts/ai/enemy_ship.gd`: Flying enemy AI controlled by a Finite State Machine (FSM) transitioning between **Wandering**, **Chasing**, and **Attacking**.
- `res://scripts/ui/virtual_joystick.gd`: Multi-touch virtual joystick designed for mobile steering (pitch, yaw, and banking).
- `res://scripts/ui/touch_button.gd`: High-responsiveness on-screen touch buttons for laser firing and afterburner boosting.
- `res://scripts/ui/hud.gd`: In-game heads-up display showing hull integrity, mission objectives, live mission timer, screen reticle, and 3D distance target icons.
- `res://scripts/ui/main_menu.gd`: Main menu system with submenus for vehicle selection (with full attribute displays) and level selection.

---

## 2. Assignment Task Fulfillment

### Task 1: The Game Flow [15 Marks]
- **Main Menu with Sub-menus**:
  - `START MISSION`: Launches the active mission immediately.
  - `SELECT SPACE SHIP`: Submenu displaying 3 playable ships (Striker, Challenger, Bob) with stats for Maximum Speed, Acceleration, and Hull Durability.
  - `SELECT LEVEL`: Submenu allowing the player to select between **Level 1: Deep Space** and **Level 2: Planet Surface**.
- **Gameplay Completion**:
  - Eliminating required hostiles activates the designated **Extraction Beacon**.
  - Flying into the extraction zone stops the clock and reveals the **Mission Accomplished** overlay showing total completion time (`MM:SS.ms`).
  - Offers immediate options to **Replay Level** or **Return to Main Menu**.
- **Game Over**:
  - Hull integrity reaching 0 triggers a destruction sequence and opens the **Game Over** prompt to continue (restart) or quit to menu.

### Task 2: User Interface / HUD [10 Marks]
- Real-time hull integrity bar and numeric HP counter.
- Touch-input indicators: On-screen virtual joystick nub and pad on the bottom-left with touch guidance, plus dedicated touch buttons for **FIRE** and **BOOST** on the bottom-right.
- Enemy tracking: 3D-to-2D projected HUD markers tracking distant hostiles with distance in meters and their current AI behavior state.

### Task 3: The Game World [5 Marks]
- **Level 1 (Deep Space)**: Set in an orbital asteroid belt featuring floating rocky asteroids (`Rock_Large_1`, `Rock_Large_2`), orbital space stations (`Base_Large`), and distant celestial planets (`Planet_2`, `Planet_7`).
- **Level 2 (Planet Surface)**: Set on an alien planetary surface featuring canyon obstacles, alien flora (`Tree_Light_1`, `Tree_Spikes_1`), research domes (`GeodesicDome`, `Roof_Radar`), and atmospheric sunset lighting with distance fog.

### Task 4: The Player [15 Marks]
- **3 Playable Spaceships**:
  1. **Striker Interceptor**: Max Speed: 48 m/s, Acceleration: 55 m/s², Max Health: 80 HP.
  2. **Challenger Assault**: Max Speed: 34 m/s, Acceleration: 36 m/s², Max Health: 160 HP.
  3. **Bob Fighter**: Max Speed: 40 m/s, Acceleration: 44 m/s², Max Health: 110 HP.
- Attributes are visually previewed with progress meters and units on the selection screen.

### Task 5: Input [5 Marks]
- Multi-touch virtual joystick input supporting mobile touch drag and desktop mouse emulation.
- Dedicated touch firing button and afterburner boost button.
- Menu navigation fully interactive via touchscreen taps.

### Task 6: Camera [5 Marks]
- Perspective camera with smooth trailing spring mechanics inspired by EverSpace 2.
- Dynamic field-of-view expansion when boosting and camera shake upon receiving damage.

### Task 7: AI and Enemies [25 Marks]
- **Two Enemy Ship Types**:
  1. `Imperial`: Heavy gunship (high armor, twin lasers, slower maneuverability).
  2. `Insurgent`: Fast scout interceptor (high speed, rapid-fire blaster, nimble turns).
- **Finite State Machine (FSM)**:
  - `WANDER`: Patrols waypoints and wanders smoothly when the player is out of detection range (>220m).
  - `CHASE`: Pursues player position using Seek steering behavior when within detection range (<220m).
  - `ATTACK`: Faces the player, leads the firing solution, and shoots red laser projectiles when in combat range (<75m).
- **Steering Behaviors**:
  - Path following (patrol sequence).
  - Wander behavior (Reynolds displacement sphere).
  - Seek / Pursuit behavior.
  - Obstacle avoidance using forward physics raycast sweeps.

### Task 8 & 9: Aesthetics & Audio [10 Marks]
- Dynamic lighting, bloom glow on energy blasters and thrusters, explosion particle fireballs, and projectile impact sparks.
- Sound effects for laser firing, mechanical impacts, and explosions.
- Multi-channel background music loops by Florian Stracker.

---

## 3. Citations & References
- Godot GDScript Style Guide: https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html
- GDQuest Steering AI Framework: https://github.com/GDQuest/godot-steering-ai-framework
- KidsCanCode 3D Shooting & Spaceship Recipes: https://kidscancode.org/godot_recipes/3.x/3d/
- Assets: Kenney Sci-Fi Audio, Kenney UI Pack, Kenney Crosshair Pack, and Kenney Mobile Controls (licensed CC0).
