
# Platformer Game Instructions

This guide walks through the full setup and logic behind a JavaScript canvas-based platformer game with checkpoints, platforms, and responsive design.

## 🧱 Step-by-Step Guide

### 🧑‍💻 Initial Setup

#### Step 1
```js
const startBtn = document.getElementById("start-btn");
const canvas = document.getElementById("canvas");
```

#### Step 2
```js
const startScreen = document.querySelector(".start-screen");
const checkpointScreen = document.querySelector(".checkpoint-screen");
```

#### Step 3
```js
const checkpointMessage = document.querySelector(".checkpoint-screen > p");
```

#### Step 4
```js
const ctx = canvas.getContext("2d");
```

#### Step 5–7
```js
canvas.width = innerWidth;
canvas.height = innerHeight;
```

#### Step 8
```js
const gravity = 0.5;
```

#### Step 9
```js
let isCheckpointCollisionDetectionActive = true;
```

#### Step 10–11
```js
const proportionalSize = size =>
  innerHeight < 500 ? Math.ceil((size / 500) * innerHeight) : size;
```

## 🧍‍♂️ Player Class

### Step 12–34
```js
class Player {
  constructor() {
    this.position = { x: proportionalSize(10), y: proportionalSize(400) };
    this.velocity = { x: 0, y: 0 };
    this.width = proportionalSize(40);
    this.height = proportionalSize(40);
  }

  draw() {
    ctx.fillStyle = "#99c9ff";
    ctx.fillRect(this.position.x, this.position.y, this.width, this.height);
  }

  update() {
    this.draw();
    this.position.x += this.velocity.x;
    this.position.y += this.velocity.y;

    if (this.position.y + this.height + this.velocity.y <= canvas.height) {
      if (this.position.y < 0) this.position.y = 0;
      this.velocity.y += gravity;
    } else {
      this.velocity.y = 0;
    }

    if (this.position.x < 0) this.position.x = 0;
    if (this.position.x >= canvas.width - this.width * 2) {
      this.position.x = canvas.width - this.width * 2;
    }
  }
}
```

## 🎮 Game Start and Animation

### Step 35–39
```js
const player = new Player();

const startGame = () => {
  canvas.style.display = "block";
  startScreen.style.display = "none";
  animate();
};

startBtn.addEventListener("click", startGame);
```

### Step 40–43
```js
const animate = () => {
  requestAnimationFrame(animate);
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  player.update();
};
```

## ⌨️ Keyboard Controls

### Step 44–49
```js
const keys = {
  rightKey: { pressed: false },
  leftKey: { pressed: false }
};
```

### Step 50–58
```js
const movePlayer = (key, xVelocity, isPressed) => {
  if (!isCheckpointCollisionDetectionActive) {
    player.velocity.x = 0;
    player.velocity.y = 0;
    return;
  }

  switch (key) {
    case "ArrowLeft":
      keys.leftKey.pressed = isPressed;
      if (xVelocity === 0) player.velocity.x = xVelocity;
      player.velocity.x -= xVelocity;
      break;
    case "ArrowUp":
    case " ":
    case "Spacebar":
      player.velocity.y -= 8;
      break;
    case "ArrowRight":
      keys.rightKey.pressed = isPressed;
      if (xVelocity === 0) player.velocity.x = xVelocity;
      player.velocity.x += xVelocity;
      break;
  }
};
```

### Step 59–62
```js
window.addEventListener("keydown", ({ key }) => {
  movePlayer(key, 8, true);
});

window.addEventListener("keyup", ({ key }) => {
  movePlayer(key, 0, false);
});
```

## 🟩 Platforms

### Step 64–76
```js
class Platform {
  constructor(x, y) {
    this.position = { x, y };
    this.width = 200;
    this.height = proportionalSize(40);
  }

  draw() {
    ctx.fillStyle = "#acd157";
    ctx.fillRect(this.position.x, this.position.y, this.width, this.height);
  }
}

const platformPositions = [
  { x: 500, y: proportionalSize(450) },
  { x: 700, y: proportionalSize(400) },
  { x: 850, y: proportionalSize(350) },
  { x: 900, y: proportionalSize(350) },
  { x: 1050, y: proportionalSize(150) },
  { x: 2500, y: proportionalSize(450) },
  { x: 2900, y: proportionalSize(400) },
  { x: 3150, y: proportionalSize(350) },
  { x: 3900, y: proportionalSize(450) },
  { x: 4200, y: proportionalSize(400) },
  { x: 4400, y: proportionalSize(200) },
  { x: 4700, y: proportionalSize(150) }
];

const platforms = platformPositions.map(p => new Platform(p.x, p.y));
```

### Step 77–80
```js
platforms.forEach(platform => platform.draw());

if (keys.rightKey.pressed && isCheckpointCollisionDetectionActive) {
  platforms.forEach(platform => platform.position.x -= 5);
} else if (keys.leftKey.pressed && isCheckpointCollisionDetectionActive) {
  platforms.forEach(platform => platform.position.x += 5);
}
```

## 🏁 Checkpoints

### Step 93–99
```js
class CheckPoint {
  constructor(x, y, z) {
    this.position = { x, y };
    this.width = proportionalSize(40);
    this.height = proportionalSize(70);
    this.claimed = false;
  }

  draw() {
    ctx.fillStyle = "#f1be32";
    ctx.fillRect(this.position.x, this.position.y, this.width, this.height);
  }

  claim() {
    this.width = 0;
    this.height = 0;
    this.position.y = Infinity;
    this.claimed = true;
  }
}
```

### Step 100–101
```js
const checkpointPositions = [
  { x: 1170, y: proportionalSize(80), z: 1 },
  { x: 2900, y: proportionalSize(330), z: 2 },
  { x: 4800, y: proportionalSize(80), z: 3 }
];

const checkpoints = checkpointPositions.map(cp => new CheckPoint(cp.x, cp.y, cp.z));
```

### Step 105–108
```js
const showCheckpointScreen = (msg) => {
  checkpointScreen.style.display = "block";
  checkpointMessage.textContent = msg;

  if (isCheckpointCollisionDetectionActive) {
    setTimeout(() => {
      checkpointScreen.style.display = "none";
    }, 2000);
  }
};
```

---

## ✅ Completion

🎉 Congratulations! You’ve now built a complete platformer game with:
- Jumping and movement
- Platform collision
- Checkpoint progression
- Responsive layout using canvas
