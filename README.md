float x;
float y; 
// Diameter of the oval
float diameter = 100;
color[] colors = new color[4]; 

void setup() {
  size(400, 400);
  // Start oval in center
  x = width / 2; 
  y = height / 2; 

  // Define four different fill colors for the areas
  // Red (Top-left)
  colors[0] = color(200, 0, 0); 
  // Green (Top-right)
  colors[1] = color(0, 100, 0); 
  // Blue (Bottom-left)
  colors[2] = color(0, 0, 100); 
  // Orange (Bottom-right)
  colors[3] = color(255, 150, 0);
 
}

void draw() {
  // Set dark background
  background(50); 

  // Determine the region based on the oval's position (doesn't work without??)
  int region = 0; 

  if (x > width / 2) {
    // Top-right region
    region = 1; 
  }

  if (y > height / 2) {
    // Bottom-left or Bottom-right region
    region += 2; 
  }

  // Changes the fill color based on the current position
  fill(colors[region]);

  // Check if the mouse is inside the oval
  if (mouseX > x - diameter / 2 && mouseX < x + diameter / 2 &&
    mouseY > y - diameter / 2 && mouseY < y + diameter / 2) {
    // Move the oval with mouse when it's inside
    x = mouseX;
    y = mouseY;
  }

  ellipse(x, y, diameter, diameter);
}
//This code divides the canvas into four regions:
//top-left, top-right, bottom-left, and bottom-right. The oval's color changes based on its position within these regions. 
//If the mouse is inside the oval, you can drag it to move around. 
