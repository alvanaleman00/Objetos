Spot sp1, sp2, sp3;                
void setup() {
  size(400, 400);
  smooth();
  noStroke();
  sp1 = new Spot(10, 100, 80, 2.0);      
  sp2 = new Spot(205, 100, 20, 10.0);      
  sp3 = new Spot(325, 100, 60, 3.5);      
}

void draw() {
  fill(0, 15);
  rect(0, 0, width, height);
  fill(255);
  sp1.move();
  sp2.move();
  sp3.move();
  sp1.display();
  sp2.display();
  sp3.display();
}

class Spot {
  float x, y;           // X-coordinate, y-coordinate
  float diameter;       // Diameter of the circle
  float speed;          // Distance moved each frame
  int direction = 1;    // Motion Direction(1 is down, -1 is up)

  Spot(float xpos, float ypos, float dia, float sp) {  
        // Constructor
    x = xpos;
    y = ypos;
    diameter = dia;
    speed = sp;
  }

  void move() {
    y += (speed * direction);
    if ((y > (height - diameter / 2)) || (y < diameter / 2)) {
      direction *= -1;
    }
  }

  void display() {
    rect(x, y, diameter, diameter);
  }
}
