# Bus Catcher Simulator - 3D City Navigation Game

A complete 3D browser-based game built with Babylon.js 7+ and Havok Physics Engine where players navigate a procedurally generated city to reach the university before time runs out.

## 🎮 Game Overview

You play as a student who must navigate from home to the university within a 10-minute time limit. Travel on foot or catch buses to move faster through the randomly generated city!

## ✨ Features

### Procedural City Generation
- **20×20 block grid** with dynamic layout each time you load
- **Randomly generated buildings** with varying heights, widths, and colors
- **Road network** connecting all city blocks
- **Bus stops** at strategic intersections
- **Landmarks**: Home (start point) and University (goal)

### Player Mechanics
- **Third-person camera** that follows the player
- **Physics-based movement** using Havok Physics v2
- **WASD controls** for walking
- **Mouse look** with pointer lock support
- **Space to jump** with realistic gravity
- **Collision detection** with buildings and objects

### Bus System
- **Multiple bus routes** following looping grid paths
- **Automatic stops** at bus stops (8-12 seconds each)
- **Board/Exit** buses with the E key
- **Faster travel** than walking

### Game Objectives
- **10-minute countdown timer** displayed on screen
- **Reach the university** (green glowing building) to win
- **Time management** - walk or take buses strategically
- **Visual feedback** for timer warnings (yellow < 3min, red < 1min)

### Technical Features
- **Single HTML file** - no external dependencies except CDN
- **Havok Physics Engine** for realistic collisions and gravity
- **Babylon.js 7+** for 3D rendering
- **Responsive design** - adapts to window size
- **Loading screen** with progress updates
- **Background music** (optional city ambience)

## 🚀 How to Run

### Option 1: Direct Browser Open
1. Simply open `index.html` in any modern web browser (Chrome, Firefox, Edge, Safari)
2. The game will automatically load all dependencies from CDN
3. Wait for the loading screen to complete
4. Click on the canvas to start playing

### Option 2: Local Web Server
If you encounter CORS issues with direct file opening:

```bash
# Python 3
python -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080

# Node.js
npx http-server -p 8080
```

Then navigate to `http://localhost:8080/index.html`

## 🎯 Controls

| Key | Action |
|-----|--------|
| **W** | Move Forward |
| **A** | Move Left |
| **S** | Move Backward |
| **D** | Move Right |
| **Mouse** | Look Around |
| **Space** | Jump |
| **E** | Board/Exit Bus |
| **Click Canvas** | Enable Pointer Lock |

## 🏗️ Technical Architecture

### Core Classes

#### GameManager
- Central game coordinator
- Manages game state (LOADING, PLAYING, WIN, LOSE)
- Handles timer countdown
- Coordinates all game systems
- Detects win/lose conditions

#### CityGenerator
- Procedural city generation
- Creates ground plane with roads
- Places random buildings with physics
- Positions bus stops at intersections
- Generates bus routes
- Creates home and university landmarks

#### Player
- Physics-based character controller
- WASD + mouse look controls
- Jump mechanics with ground detection
- Bus boarding/exiting system
- Camera follow system

#### Bus
- Follows predefined routes
- Stops at bus stops automatically
- Kinematic physics body
- Passenger boarding system

### Physics System (Havok v2)
- **Gravity**: `Vector3(0, -9.81, 0)` (realistic Earth gravity)
- **Ground**: Static plane shape
- **Buildings/Stops**: Static box/cylinder shapes
- **Player**: Dynamic capsule with force-based movement
- **Buses**: Kinematic bodies with scripted movement

### UI System
- HTML overlay for HUD elements
- Real-time timer display
- Status indicators (On Foot / On Bus)
- Action prompts (Press E to Board)
- Win/Lose screens with restart option
- Control instructions

## 📦 Dependencies (Loaded from CDN)

All dependencies are loaded automatically from Babylon.js CDN:
- `babylon.js` - Core 3D engine
- `babylonjs.loaders.min.js` - Model loading support
- `babylon.gui.min.js` - UI system
- `HavokPhysics_umd.js` - Physics engine

## 🎨 Game Design

### Color Coding
- **Yellow Building** = Home (start)
- **Green Building** = University (goal)
- **Blue Spheres** = Bus stops
- **Orange/Blue Buses** = Different routes
- **Red Character** = Player

### Timer Colors
- **Green** (10:00 - 3:00) = Plenty of time
- **Orange** (3:00 - 1:00) = Warning
- **Red** (< 1:00) = Danger (pulsing)

## 🔧 Customization

You can modify game parameters by editing the `GAME_CONFIG` object in the JavaScript:

```javascript
const GAME_CONFIG = {
    GRID_SIZE: 20,              // City grid size
    BLOCK_SIZE: 40,             // Size of each block
    ROAD_WIDTH: 8,              // Width of roads
    GAME_DURATION: 600,         // Game time in seconds
    PLAYER_SPEED: 8,            // Player movement speed
    PLAYER_JUMP_FORCE: 12,      // Jump strength
    BUS_SPEED: 15,              // Bus movement speed
    BUS_STOP_DURATION: 10,      // How long buses stop
    BOARDING_DISTANCE: 5,       // Distance to board bus
    WIN_DISTANCE: 10            // Distance to university to win
};
```

## 🌐 Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Edge 90+
- ✅ Safari 14+
- ✅ Opera 76+

**Requirements:**
- WebGL 2.0 support
- Modern JavaScript (ES6+)
- Pointer Lock API support

## 🎵 Audio

The game includes optional background city ambience music from Freesound.org (CC0 license). Audio will play automatically when the game starts if enabled.

## 🐛 Troubleshooting

### Game won't load
- Check browser console for errors
- Ensure you have a stable internet connection (for CDN resources)
- Try a different browser
- Clear browser cache

### Can't move the camera
- Click on the canvas to enable pointer lock
- Check if your browser supports Pointer Lock API
- Try pressing ESC and clicking again

### Physics not working
- Ensure browser supports WebAssembly (required for Havok)
- Check console for physics initialization errors
- Try refreshing the page

### Performance issues
- Close other browser tabs
- Lower your browser zoom level
- Try on a device with better GPU
- Reduce city size in GAME_CONFIG (if customizing)

## 📝 License

This game is created as a demonstration project. The code is free to use and modify.

### Third-Party Assets
- **Babylon.js**: Apache License 2.0
- **Havok Physics**: Available via Babylon.js CDN
- **Audio**: CC0 from Freesound.org

## 🎓 Educational Purpose

This project demonstrates:
- Modern JavaScript game development
- 3D graphics with Babylon.js
- Physics simulation with Havok
- Procedural generation techniques
- Game state management
- Browser API usage (Pointer Lock, etc.)
- Single-file web application architecture

## 🔮 Future Enhancements

Potential improvements:
- More bus routes and complex schedules
- Weather effects (rain, fog)
- Day/night cycle
- Traffic system with cars
- NPCs walking around
- Multiple difficulty levels
- Achievements system
- High score tracking
- Mobile touch controls
- VR support

## 👨‍💻 Development

The entire game is contained in a single `index.html` file for maximum portability and ease of deployment. No build process or package management required!

**File Structure:**
```
bus_catcher_sim/
├── index.html          # Complete game (HTML + CSS + JavaScript)
└── readme.md          # This file
```

**Code Structure within index.html:**
1. HTML structure (canvas + UI overlays)
2. CSS styling (responsive design)
3. CDN script includes
4. JavaScript game logic:
   - Constants and utilities
   - CityGenerator class
   - Player class
   - Bus class
   - GameManager class
   - Initialization code

## 🎯 Game Tips

1. **Plan your route** - Look for the green university building
2. **Use buses strategically** - They're faster but follow fixed routes
3. **Watch the timer** - Don't wander too far without a plan
4. **Explore carefully** - The city layout is different each time
5. **Jump on buildings** - Sometimes shortcuts are possible
6. **Bus stops have blue spheres** - Easy to spot from a distance

Enjoy the game! 🎮🚌🏫
