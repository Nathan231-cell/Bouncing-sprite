<canvas id="bouncyCanvas" width="500" height="400" style="border:1px solid black"></canvas>

<script>
  const canvas = document.getElementById('bouncyCanvas');
  const ctx = canvas.getContext('2d');
  
  let x = 100, y = 100; // Starting position
  let dx = 4, dy = 4;   // Speed
  let radius = 20;
  let color = "red";    // Initial color

  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height); // Clear screen
    
    // Draw the sprite
    ctx.beginPath();
    ctx.arc(x, y, radius, 0, Math.PI * 2);
    ctx.fillStyle = color;
    ctx.fill();
    ctx.closePath();

    // Wall Collision + Color Change Logic
    if (x + dx > canvas.width - radius || x + dx < radius) {
      dx = -dx;
      color = `hsl(${Math.random() * 360}, 100%, 50%)`; // Change to random color
    }
    if (y + dy > canvas.height - radius || y + dy < radius) {
      dy = -dy;
      color = `hsl(${Math.random() * 360}, 100%, 50%)`; // Change to random color
    }

    x += dx;
    y += dy;
    requestAnimationFrame(draw); // Loop the animation
  }
  draw();
</script>
