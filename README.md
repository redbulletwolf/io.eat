<!DOCTYPE html>
<html>
  <head>
    <title>IO Game</title>
    <style>
      canvas {
        border: 1px solid black;
      }
    </style>
  </head>
  <body>
    <canvas id="gameCanvas" width="800" height="600"></canvas>

    <script>
      // Get the canvas element and its 2D rendering context
      const canvas = document.getElementById('gameCanvas');
      const ctx = canvas.getContext('2d');

      // Player object
      const player = {
        x: 400,
        y: 300,
        radius: 10,
        color: 'blue',
      };

      // Update function
      function update() {
        // Clear the canvas
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        // Draw the player
        ctx.beginPath();
        ctx.arc(player.x, player.y, player.radius, 0, 2 * Math.PI);
        ctx.fillStyle = player.color;
        ctx.fill();
        ctx.closePath();
      }

      // Function to handle mouse movement
      function handleMouseMove(event) {
        const rect = canvas.getBoundingClientRect();
        player.x = event.clientX - rect.left;
        player.y = event.clientY - rect.top;
      }

      // Event listener for mouse movement
      canvas.addEventListener('mousemove', handleMouseMove);

      // Game loop
      function gameLoop() {
        update();
        requestAnimationFrame(gameLoop);
      }

      // Start the game loop
      gameLoop();
    </script>
  </body>
</html>
