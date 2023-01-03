# chenshuyue77
作业7
float x = 0, y = 0;
float stepSize = 5.0;
String letters = "happy new year!";
float fontSizeMin = 3;
float angleDistortion = 0.01;
int counter = 0;
 
PFont font;
void setup() {

  size(840, 880);
  background(255);
  smooth();
  cursor(CROSS);
 
  
  x = mouseX;
  y = mouseY;
 
  textAlign(LEFT);
  fill(0);
  
  font = createFont("DENG.TTF", 20);
  textFont(font);
}
 
void draw() {
  if (mousePressed) {
    

    float d = dist(x,y, mouseX,mouseY); 
    textSize(fontSizeMin+d/2);
    
    
    char newLetter = letters.charAt(counter);
   
    stepSize = textWidth(newLetter);
 
    if (d > stepSize) {
     
      float angle = atan2(mouseY-y, mouseX-x); 
 
      
      push();
         fill(random(255),random(255),random(255));
      translate(x, y);
      rotate(angle + random(angleDistortion));
      text(newLetter, 0, 0);
      pop();
      
      counter++;
      
      if (counter > letters.length()-1) 
        counter = 0;
      
     
      x = x + cos(angle) * stepSize;
      y = y + sin(angle) * stepSize; 
    }
  }
}
 
void mousePressed() {
  x = mouseX;
  y = mouseY;
}
 
void keyTyped() {
  //if (key == 's' || key == 'S') save("result.png");
}
 
void keyPressed() {
  // angleDistortion ctrls arrowkeys up/down 
  if (keyCode == DELETE || keyCode == BACKSPACE) background(255);
  if (keyCode == UP) angleDistortion += 0.1;
  if (keyCode == DOWN) angleDistortion -= 0.1; 
}
