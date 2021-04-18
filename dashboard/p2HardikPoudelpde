// Author: Hardik Poudel
// Class: Human Computer Interaction Spring 2021
// Date: 04/18/2021

// This is a program written in processing to create a car dashboard. 


// Global variables.
int sX = 300;
int sY = 400;
float s = -0.4;
int rd = 150;
float acc = 0.006;
int speed = 0;
float dist = 0;
int rX = 800;
int rY = 400;
float r = 0;
float rpm = 0.1;
int c = 0;
float level = 1;
float templevel = 8;

PImage checkeng, engtemp, oil, tire, traction, fuel, engtt, cruise, light, lowfuel, cardoor, emer;

boolean powerOn = false;
boolean right = false;
boolean left = false;
boolean cruisectr = false;
boolean hazard = false;
boolean headlight = false;


void setup(){  
  size(1100,800);
  checkeng = loadImage("checkeng.png");
  engtemp = loadImage("engtemp.png");
  oil = loadImage("oil.png");
  tire = loadImage("tire.png");
  traction = loadImage("traction.png");
  fuel = loadImage("fuel.png");
  engtt = loadImage("engtt.png");
  cruise = loadImage("cruise.png");
  light = loadImage("headlight.png");
  lowfuel = loadImage("lowfuel.png");
  cardoor = loadImage("cardoor.png");
  emer = loadImage("hazard.png");
}

void draw(){
  if(headlight){
    background(#c3b554);
  }else{
    background(0);
  }
  stroke(#3E64A2);
  fill(2);
  strokeWeight(5);
  
  // control buttons
  rect(13,66,1083,547);
  triangle(491,636,493,760,575,696);
  triangle(60,703,142,638,139,764);
  rect(684,666,104,58);
  circle(318,698,100);
  rect(948,667,104,58);
 
  
  // Tachometer and speedometer
  arc(300, 400, 300, 300, PI-0.5, 2*PI+0.5, CHORD);
  arc(800, 400, 300, 300, PI-0.5, 2*PI+0.5, CHORD);
  
  
  image(checkeng, 284,549,56,50);
  image(oil, 572,549,58,49);
  image(tire, 706,547,60,48);
  image(traction, 832,547,50,50);
  image(fuel, 997,336,50,50);
  image(engtt, 63,332,54,46);
  image(cardoor, 744,175,50,50);
  image(emer, 293,671,50,50);
  if(cruisectr){
    image(cruise, 599, 175, 50,50);
  }
  if(headlight){
    image(light, 325,185,58,43);
  }
  
  
  fill(99);
  speed = int(s*60)+24;
  rect(475,270,155,205);
  fill(255);
  textSize(11);
  text("Outside temperature: 60°F", 481,296);
  textSize(72);
  text(speed , 500,393);
  textSize(11);
  text("MPH", 593,420);
  textSize(16);
  text(int(dist) + "Miles", 533,453);
  textSize(11);
  
  text("Turn left", 81,706);
   text("Turn right", 500,702);
   text("Cruise", 718,698);
   text("RPM", 792,343);
   text("Speed MPH", 271,343);
   text("Head lights", 969,699);
 
  // Fuel and temp
  strokeWeight(4);
  for(int i = 1; i < 10; i++){
    if(i < 4){
      
      stroke(#f74a06);
      
    }else if(i >= 4 && i < 7){
      stroke(#1fc23a);
     
    }else{
      stroke(#3599e0);
      
    }
    if(i < int(templevel)){
      fill(0);
    }else{
      fill(255);
    }
    
    rect(36,255+(i*20),20,20);
    
  }
  for(int i = 1; i < 10; i++){
    if(i < 5){
      stroke(#2ab43d);
    }else if(i >= 5 && i < 8){
      stroke(#F78B05);
    }else{
      stroke(#F70505);
    }
    if(i < int(level)){
      fill(0);
    }else{
      fill(255);
    }
  rect(1058,255+(i*20), 20,20);
  }
  fill(255);
  stroke(#f7161b);
  strokeWeight(6);
  //speedometer
  if(mousePressed && cruisectr == false){
    if(s< 3.4){
      s = s+ acc;
    }
  }else{
    if(s > -0.4 && cruisectr == false){
      s -= acc;
    }
  }
  line( sX - cos(s) *rd , sY - sin(s) *rd, sX, sY); // tachometer pointer
  
   // tachometer
  if(mousePressed && cruisectr == false){
    if(r< 3.4 ){
      r = r+ rpm;
    }
  }else{
    if(r > -0.4 && cruisectr == false){
      r -= rpm;
    }
  }
  line( rX - cos(r) *rd , rY - sin(r) *rd, rX, rY); // rpm pointer
  if(int(dist) > 0 && int(dist) %3 == 0){
    level += 0.009;
    templevel -= 0.009;
  }
  if(int(level) > 7){
    text("Fuel low. Please refuel", 489,100);
    image(lowfuel, 467,180,50,50);
  }
  
  if(int(level) > 8){
    noStroke();
    fill(0);
    rect(452,81,173,24);
    fill(255);
    text("Fuel tank empty. Please refuel", 460,96);
    cruisectr = false;
  }
  

  if(int(templevel) < 4){
    image(engtemp, 428,549,59,50);
    text("Engine temperature very high. Please cool down.", 425,126);
  }
  
  
  stroke(#5DD821);
   leftSide(left);
   rightSide(right);
   c++;
  if(c >100){
    c = 0;
  }
   
  fill(67);
  stroke(#7f6b48);
  float st = 2.7;
 for(int i = 0; i < 5; i++){
   fill(222);
   textSize(16);
  text(i*60, 286+cos(i+st)*129, 399+sin(i+st)*124); 
 }
 for(int i = 0; i < 5; i++){
   fill(222);
   textSize(16);
  text(i*1000, 781+cos(i+st)*119, 399+sin(i+st)*124); 
 }
 if(speed > 0){
   dist += 0.009;
 }
}

void mousePressed(){
   if(mouseX > 490 && mouseX < 575 && mouseY > 635 && mouseY < 765){
     right ^= true;
   }
   if(mouseX > 60 && mouseX < 145 && mouseY > 640 && mouseY < 775){
     left ^= true;
   }
   if(mouseX > 685 && mouseX < 790 && mouseY > 670 && mouseY < 730){
     cruisectr ^= true;
   }
   if(mouseX > 270 && mouseX < 370 && mouseY > 650 && mouseY < 755){
     right ^= true;
     left ^= true;
   }
   if(mouseX > 950 && mouseX < 1055 && mouseY > 670 && mouseY < 730){
     headlight ^= true;
   }
}

void leftSide(boolean left){
   if(left && c < 50){
    fill(#5DD821);
  }else{
    fill(#585A57);
  }
  rect(151,100,35,25);
  triangle(120, 111, 154, 86, 153, 137);
}

void rightSide(boolean right){
  if(right  && c <50){
    fill(#5DD821);
  }else{
    fill(#585A57);
  }
  rect(950,99,35,25);
  triangle(1020, 112, 984, 86, 983, 137);
}
