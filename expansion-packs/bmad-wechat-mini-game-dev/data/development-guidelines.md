# Game Development Guidelines (WeChat Mini Game, JavaScript)

## Overview

This document establishes coding standards, architectural patterns, and development practices for game development using the WeChat Mini Game framework with JavaScript. These guidelines ensure consistency, performance (60+ FPS target), maintainability, and enforce Test-Driven Development (TDD) across all game development stories.

## Performance Philosophy

- **"Measure, don't guess"** - Profile everything with the WeChat Mini Game profiler
- **"Focus on what matters: framerate and responsiveness"** - 60+ FPS is the minimum, not the target
- **"The best code is no code"** - Simplicity beats cleverness
- **"Think about cache misses, not instruction counts"** - Memory access patterns matter most

## JavaScript Standards

### Naming Conventions

**Classes and Scripts:**

- PascalCase for class names: `PlayerController`, `GameData`, `InventorySystem`
- Snake_case for file names: `player_controller.js`, `game_data.js`
- Descriptive names that indicate purpose: `GameStateManager` not `GSM`

**Functions and Methods:**

- camelCase for functions: `calculateDamage()`, `processInput()`
- Descriptive verb phrases: `activateShield()` not `shield()`
- Private methods prefix with underscore: `_updateHealth()`

**Variables and Properties:**

- camelCase for variables: `playerHealth`, `movementSpeed`
- Constants in UPPER_SNAKE_CASE: `MAX_HEALTH`, `GRAVITY_FORCE`
- Boolean variables with is/has/can prefix: `isAlive`, `hasKey`, `canJump`
- Event names in snake_case: `health_changed`, `level_completed`

## WeChat Mini Game Architecture Patterns

### Object-Based Architecture

**Scene Composition Over Inheritance:**

```javascript
// Player.js - Single responsibility component
class PlayerHealth {
    constructor(maxHealth) {
        this.maxHealth = maxHealth;
        this.currentHealth = maxHealth;
    }

    takeDamage(amount) {
        this.currentHealth = Math.max(0, this.currentHealth - amount);
        if (this.currentHealth === 0) {
            // emit 'died' event
        }
    }
}
```

### Event-Based Communication

**Decouple Systems with Events:**

```javascript
// GameManager.js - Global manager
class GameManager {
    constructor() {
        this.score = 0;
        this.currentLevel = 1;
    }

    startGame() {
        this.score = 0;
        this.currentLevel = 1;
        // emit 'game_started' event
    }
}

// Player.js - Connects to events
class Player {
    constructor(gameManager) {
        gameManager.on('game_over', this._onGameOver.bind(this));
    }

    _onGameOver() {
        // Stop player movement
    }
}
```

### JSON-Based Data Management

**Use JSON for Game Data:**

```javascript
// weapon_data.json
{
    "weaponName": "Sword",
    "damage": 10,
    "attackSpeed": 1.0,
    "sprite": "images/sword.png"
}

// Weapon.js - Uses the data
class Weapon {
    constructor(weaponData) {
        this.weaponData = weaponData;
    }

    attack() {
        return this.weaponData ? this.weaponData.damage : 0;
    }
}
```

## Performance Optimization

### Object Pooling (MANDATORY for Spawned Objects)

```javascript
// ObjectPool.js - Generic pooling system
class ObjectPool {
    constructor(scene, initialSize) {
        this.scene = scene;
        this._pool = [];

        for (let i = 0; i < initialSize; i++) {
            let instance = this.scene.create();
            instance.visible = false;
            this._pool.push(instance);
        }
    }

    getObject() {
        for (let obj of this._pool) {
            if (!obj.visible) {
                obj.visible = true;
                return obj;
            }
        }

        // Expand pool if needed
        let newObj = this.scene.create();
        this._pool.push(newObj);
        return newObj;
    }

    returnObject(obj) {
        obj.visible = false;
    }
}
```

### Process Optimization

**Use Appropriate Process Methods:**

```javascript
// For physics calculations (fixed timestep)
function _physics_process(delta) {
    // Movement, collision detection
}

// For visual updates and input
function _process(delta) {
    // Animations, UI updates
}

// Use timers or events instead of checking every frame
function _ready() {
    // Use setTimeout or setInterval
}
```

### Memory Management

**Prevent Memory Leaks:**

```javascript
// Clean up event listeners
function _destroy() {
    gameManager.off('score_changed', this._onScoreChanged);
}
```

## Test-Driven Development (MANDATORY)

### JavaScript Testing

**Write Tests FIRST:**

```javascript
// test/unit/test_player_health.js
const assert = require('assert');
const PlayerHealth = require('../../js/player/player_health.js');

describe('PlayerHealth', function() {
    let playerHealth;

    beforeEach(function() {
        playerHealth = new PlayerHealth(100);
    });

    it('should reduce health when taking damage', function() {
        playerHealth.takeDamage(30);
        assert.strictEqual(playerHealth.currentHealth, 70);
    });

    it('should not go below zero health', function() {
        playerHealth.takeDamage(120);
        assert.strictEqual(playerHealth.currentHealth, 0);
    });
});
```

## Input Handling

### WeChat Mini Game Input System

```javascript
// Handle touch events
wx.onTouchStart(function(res) {
    // Handle touch start
});

wx.onTouchMove(function(res) {
    // Handle touch move
});

wx.onTouchEnd(function(res) {
    // Handle touch end
});
```

## Scene Management

### Scene Loading and Transitions

```javascript
// SceneManager.js - Global manager
class SceneManager {
    constructor() {
        this.currentScene = null;
    }

    changeScene(path) {
        // Unload current scene
        // Load new scene
    }
}
```

## Project Structure

```
WeChatMiniGameProject/
├── images/             # Image assets
├── js/                 # JavaScript scripts
│   ├── libs/           # Third-party libraries
│   ├── base/           # Base classes
│   ├── player/         # Player-related scripts
│   ├── enemies/        # Enemy scripts
│   ├── systems/        # Game systems
│   ├── ui/             # UI scripts
│   └── utils/          # Utility scripts
├── audio/              # Audio assets
├── game.js             # Game entry point
├── game.json           # Game configuration
├── project.config.json # Project configuration
└── project.private.config.json # Private project configuration
```

## Development Workflow

### TDD Story Implementation Process

1. **Read Story Requirements:**
   - Understand acceptance criteria
   - Identify performance requirements (60+ FPS)

2. **Write Tests FIRST (Red Phase):**
   - Write failing unit tests
   - Define expected behavior
   - Run tests to confirm they fail

3. **Implement Feature (Green Phase):**
   - Write minimal code to pass tests
   - Follow WeChat Mini Game patterns and conventions

4. **Refactor (Refactor Phase):**
   - Optimize for performance
   - Clean up code structure
   - Ensure 60+ FPS maintained
   - Run profiler to validate

5. **Integration Testing:**
   - Test scene interactions
   - Validate performance targets
   - Test on all platforms

6. **Update Documentation:**
   - Mark story checkboxes complete
   - Document performance metrics
   - Update File List

### Performance Checklist

- [ ] Stable 60+ FPS achieved
- [ ] Object pooling for spawned entities
- [ ] No memory leaks detected
- [ ] Draw calls optimized
- [ ] Appropriate process methods used
- [ ] Events properly connected/disconnected
- [ ] Tests written FIRST (TDD)
- [ ] 80%+ test coverage

## Performance Targets

### Frame Rate Requirements

- **Mobile**: 60 FPS on mid-range devices
- **Frame Time**: <16.67ms consistently

### Memory Management

- **Scene Memory**: Keep under platform limits
- **Texture Memory**: Optimize imports, use compression
- **Object Pooling**: Required for bullets, particles, enemies
- **Reference Cleanup**: Prevent memory leaks

### Optimization Priorities

1. **Profile First**: Use the WeChat Mini Game profiler to identify bottlenecks
2. **Optimize Algorithms**: Better algorithms beat micro-optimizations
3. **Reduce Draw Calls**: Batch rendering, use atlases

## General Optimization

### Anti-Patterns

1. **Security Holes**
   - Unvalidated user input
   - Memory disclosure

2. **Platform Sabotage**
   - Fighting the WeChat Mini Game's scene system
   - Reimplementing platform features
   - Ignoring hardware capabilities

## JavaScript Optimization

### Performance Destroyers

1. **Allocation Disasters**
   - Creating Arrays/Objects in loops
   - String concatenation with +
   - Unnecessary object instantiation
   - Resource loading in game loop
   - Event connections without caching

2. **Process Method Abuse**
   - Frame-by-frame checks for rare events
   - Unnecessary process enabling

### JavaScript Death Sentences

```javascript
// CRIME: String concatenation in loop
for (let i = 0; i < 1000; i++) {
    text += i;  // Dies. Use Array.join()
}

// CRIME: Creating objects in loop
for (const enemy of enemies) {
    let bullet = new Bullet();  // Dies. Object pool
}

// CRIME: Checking rare conditions every frame
function _process(delta) {
    if (playerDied) {  // Dies. Use events
        gameOver();
    }
}

// CRIME: Object creation without pooling
function spawnParticle() {
    let p = new Particle();  // Dies. Pool everything spawned
    this.addChild(p);
}
```

### The Only Acceptable JavaScript Patterns

```javascript
// GOOD: Cached object references
let scoreLabel = this.getChildByName('score');

// GOOD: Object pooling
let bulletPool = [];
function _ready() {
    for (let i = 0; i < 50; i++) {
        let bullet = new Bullet();
        bullet.visible = false;
        bulletPool.push(bullet);
    }
}

// GOOD: Efficient string building
function buildText(count) {
    let parts = [];
    for (let i = 0; i < count; i++) {
        parts.push(i);
    }
    return parts.join('');
}

// GOOD: Timer-based checks
function _ready() {
    setInterval(this._checkRareCondition.bind(this), 1000);
}

// GOOD: Batch operations
let updatesPending = [];
function queueUpdate(value) {
    updatesPending.push(value);
    if (updatesPending.length === 1) {
        setTimeout(this._processUpdates.bind(this), 0);
    }
}

function _processUpdates() {
    // Process all updates at once
    for (const value of updatesPending) {
        // Do work
    }
    updatesPending = [];
}
```

### JavaScript-Specific Optimization Rules

1. **NEVER create objects without pooling** - Pool or die
2. **NEVER concatenate strings in loops** - Array.join()
3. **ALWAYS batch similar operations** - One update, not many
4. **NEVER check conditions every frame** - Use events and timers
```
