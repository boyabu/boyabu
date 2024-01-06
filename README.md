// Get the canvas element and 2d context
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

// Initial player position
let playerX = 50;
let playerY = canvas.height / 2;

// Update player position based on user input
function update() {
    // Example: Move player to the right when the right arrow key is pressed
    if (rightPressed) {
        playerX += 5;
    }

    // Add more logic for other directions or game mechanics

    // Example: Keep the player within the canvas bounds
    if (playerX < 0) {
        playerX = 0;
    }
    if (playerX > canvas.width - 20) {
        playerX = canvas.width - 20;
    }
}

// Draw the player on the canvas
function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear the canvas
    ctx.fillRect(playerX, playerY, 20, 20); // Draw a simple rectangle as the player
}

// Handle user input
let rightPressed = false;
document.addEventListener('keydown', keyDownHandler);
document.addEventListener('keyup', keyUpHandler);

function keyDownHandler(e) {
    if (e.key === 'ArrowRight') {
        rightPressed = true;
    }
}

function keyUpHandler(e) {
    if (e.key === 'ArrowRight') {
        rightPressed = false;
    }
}

// Game loop
function gameLoop() {
    update(); // Update game logic
    draw(); // Draw game elements

    requestAnimationFrame(gameLoop); // Repeat the game loop
}

// Start the game loop
gameLoop();
