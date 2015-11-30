
//PROJECT 3 --- CST 112 EVENING
String title=  "CST112 PROJECT 3" ;
String news= "Click any ball to reset it to middle half of table.(r resets all, m= mouse walks across the screen)";
String author=  "Rebeca Janowicz";
String title1 =  " Score=";
String s=" Press b= drop bomb, r= reset balls, wall, table color, p= pink table! \n w= remove wall and q= exit";

Ball a,b,c,d,e,cue;

// BIRD, RAT
 Bird p; Rat r;
int pooltableR=23, pooltableG=85, pooltableB= 18;     // GREEN POOL TABLE 
float oregon = 50, texas= 500 , dakota= 250, maine = 650;    // TABLE PERIMETER 
float midwest= 350;
boolean wall = true;
boolean going = false;

int score;
int count = 0;


void setup() {
 size(700,600);
    p= new Bird ();
    r= new Rat ();
  //
    a=  new Ball();
    a.r=255;
    a.name=  "a";
    //
    b=  new Ball();  b.g=255;
    b.name=  "b";
    //
    c=  new Ball();
    c.b=255; 
    c.name=  "c";
    //
    d=  new Ball();
    d.g=255; d.r=255;
    d.name=  "d";    
    //
    e=  new Ball();
    e.r=38; e.g=250; e.b = 220;
    e.name=  "e";
   //  
    cue = new Ball();
    cue.r= 255; cue.g= 255; cue.b= 255;
    reset(); 
}
  void reset() {
    a.reset();
    b.reset();
    c.reset();
    d.reset();
    e.reset();
    cue.reset();
  //
    p.reset(); //p. drop();
    r.reset ();
  // Reseit table color to green
    pooltableR=23; pooltableG=85; pooltableB= 18;
    score= 0;
    cue.x= (oregon+maine)/4;     cue.y= (dakota+texas)/2;
    cue.dx= 0;          cue.dy= 0;

  }
 
//// NEXT FRAME:  scene, birds, balls.
void draw() {
      message();
      poolTable(oregon, texas, maine,dakota);
      balls();
      grass();
      clouds(); 
 // BIRD & RAT CODE
      p.display();
      p.move();
      r.display();
      r.move();
      count= count +1;
      textSize(12);
      text( s, 150,20 );
  
}
 // MESSAGES 
  void message() {
      fill(0);
      stroke(0);
      textSize(15);
      text( title, 200, 20 );
      text( news, 200, 40);
      text( author,10,540);
      textSize(20);
      text(score,width/2-10,height-525);
      text(title1,200,height-525);
  }
  
//SHOWING POOL TABLE   
   void poolTable(float oregon, float texas, float maine, float dakota)  {
      background(130,209,219);     
      rectMode(CORNERS);
      fill(pooltableR, pooltableG, pooltableB);
      strokeWeight(20);
      stroke(108,45,49);
      rect(oregon,texas,maine, dakota); 
      fill(255);
      
   if (wall== true){
      float midwest= (oregon+maine)/2;
      strokeWeight(20);
      stroke(108,45,49);
      line(midwest, texas, midwest, dakota);
   }
  }  
 
//// Move & show each ball
void balls() {
      collision( a, b );
      collision( a, c );
      collision( a, d );
      collision( a, e );
      collision( a, cue);
  //  collision (a, ratX);
      //
      collision( b, c );
      collision( b, d );
      collision( b, e );
      collision( b, cue);
     // collision (b, ratX);
      
      //
      collision( c, d );
      collision( c, e );
      collision( c, cue);
     // collision (c, ratX);
      //
      collision( d, e );
      collision( d, cue);
      //
      collision( e, cue);
  
      //
      a.move();   a.show();
      b.move();   b.show();
      c.move();   c.show();
      d.move();   d.show();
      e.move();   e.show ();
      cue.move(); cue.show();
      
}

//// Elastic collisions.
void collision( Ball p, Ball q ) {
  if ( p.hit( q.x,q.y ) ) {
    float tmp;
      tmp=p.dx;  p.dx=q.dx;  q.dx=tmp;      // Swap the velocities.
      tmp=p.dy;  p.dy=q.dy;  q.dy=tmp;
      score += 1;
      
// might have to delete
//  p.move();  p.move();   p.move();
//  q.move();  q.move();   q.move();
  }
}
  
class Ball {
  float x,y, dx,dy;
  int r,g,b;
  String name="";
  
  void show() {
    fill(r,g,b);
    noStroke();
    ellipse( x,y, 30,30 );
    fill(0);
    textSize(12);
    text( name, x-5,y );
  }
  void move() {
    if (wall == true){
       x += dx; 
     if (x < midwest + 20 || x > maine) dx *=-1; 
     
       y += dy; 
     if (y > texas  || y < dakota)  dy *= -1;
    }
 
// REMOVE WALL AND BALLS BOUNCE THROGHOUT  TABLE
   if (wall == !true){
       x += dx; 
     if (x < oregon || x > maine) dx *=-1; 
     
       y += dy; 
     if (y > texas  || y < dakota)  dy *= -1;
   }
  }
 void reset() {
   if  (wall = true) {
  //  a.reset(); b.reset(); c.reset(); d.reset(); e.reset(); cue.reset();
         
}
    x= random(midwest+20, maine); y= random(dakota, texas);
  dx=  random(1,3);   dy=  random(1,3);
  }
  
  // BALL COLLISIONS
  boolean hit( float x, float y ) {
    if (dist( x,y, this.x,this.y ) < 30 ) return true;
    else return false;
  }  
}
 
// BIRD
class Bird {
  float birdX, birdY, birdDX, birdDY, bombY, bombDY, gravity;
Bird () {
     birdX = 30; birdY = 30; birdDX = 1; birdDY = 1;
     bombY=0; bombDY = 0; gravity = 9.81/60;
     
}
// DISPLAY BIRD
void display () {
     stroke(0);
     fill(240,34,61);
     stroke(0);
     ellipse(birdX, birdY, 60,10);
     fill(183,31,34);
     
   if(count/30%2 == 0) {
      triangle(birdX, birdY+5, birdX-10, birdY-20, birdX+15, birdY+5);
      triangle(birdX, birdY-5, birdX-10, birdY-20, birdX+15, birdY-5);
   }else { 
      triangle(birdX, birdY+5, birdX-10, birdY+30, birdX+15, birdY+5);
      triangle(birdX, birdY-5, birdX-10, birdY+30, birdX+15, birdY-5);
     }
     
      fill(234,171,107);
      triangle(birdX+30, birdY+2, birdX+40, birdY, birdX+30, birdY-2); 
      
 // display bomb    
     if (bombDY>0) {
      fill(255,0,0);
      ellipse( birdX,bombY, 30,70 );
    }
}
 // MOVE BIRD
 void move() {
  // birdX = birdX + birdDX;
    if(birdX > width) { reset(); }
  
   birdY=  birdY+birdDY;
    if (birdY > 20 && birdY <100) {
      birdDY=  -birdDY * random(0.5,1);             // Bounce up and down across the sky
    }
     birdX = birdX + birdDX;
     // bomb 
     if (bombDY>0) {
      bombDY += gravity;
      bombY += bombDY;
      if (bombY>height) {
        bombY=0;
        bombDY=0;                              // Bomb is gone!
      }
    }
  }

  void drop() {
    bombY=  birdY+10;
    bombDY=  gravity;
    }
  void reset() {
      birdX=0;
      birdY=  random( 20,100 );
      birdDX=  random( 1,2 );
      bombDY=0;
  }
boolean hit( float birdX, float birdY ) {
    if (  dist( birdX,birdY, 10,10) < 30 ) return true;
    else return false;
  }

 } 
// RAT 
  class Rat {
    float ratX;
    float ratY;
    float ratDX;
    float ratDY;
  Rat(){
      
    ratX = random(oregon, maine); 
    ratY = random(450,500);
    ratDX = random( 1,3);
   // ratDY = 3;
    
   
}
 void display () {  
 // if (ratX > oregon) {
      strokeWeight(1);
      stroke(0);
      fill(155);  // ear and body's fill
      ellipse(ratX,ratY-10,40,30 );                // rat's body
      ellipse(ratX+10,ratY-27,15,15);             // ear
      fill(95,62,21);                            // tail color
      ellipse(ratX-25,ratY-15,10,1);              // tail
      fill(95,62,21);                            // ear color
      fill(0);                                   // eye, nose color
      ellipse(ratX+10,ratY-15,5,3);              // eye
      ellipse(ratX+20,ratY-5,5,5);              // nose
// }

// RAT LEGS
   float leg1=ratX+10, leg2=ratX-15;
   strokeWeight(5);
   stroke(0); 
   if (count/30 % 2 == 0) {
      line(leg1,ratY, leg1,ratY+10);
      line(leg2,ratY, leg2,ratY+10);
   }else{                                
      line(leg1,ratY, leg1-5,ratY+10);
      line(leg2,ratY, leg2-5,ratY+10);
   }
   strokeWeight(1);
 }


void move(){
  //Rat walks across the pool table
  
      ratX = ratX + ratDX; 
   if ( ratX > maine) { reset (); }
   
  // Rat should bounce     
      ratY += ratDY;
  if ((ratY > 400 || ratY < 500)){
      ratDY=  -ratDY * random(0.5,1.5) ; 
    }
 
  } 
  void reset () {
    ratX = 50; 
    ratY = random(400,500);
    ratDX= 1;
  } 
 } 
 /* if ( dist(a.x,a.y, ratX,ratY) < 10) { ratX += 15; a.dx=0; a.dy=0; score -= 10; }
  if ( dist(b.x,b.y, ratX,ratY) < 10) { ratX += 15; b.dx=0; b.dy=0; score -= 10; }
  if ( dist(c.x,c.y, ratX,ratY) < 10) { ratX += 15; c.dx=0; c.dy=0; score -= 10; }
  if ( dist(d.x,d.y, ratX,ratY) < 10) { ratX += 15; d.dx=0; d.dy=0; score -= 10; }
  if ( dist(e.x,e.y, ratX,ratY) < 10) { ratX += 15; e.dx=0; e.dy=0; score -= 10; }
  if ( dist(cue.x,cue.y, ratX,ratY) < 10) { ratX += 15; cue.dx=0; cue.dy=0; score -= 10; }
*/
 // CLOUDS
 void clouds () {
   for ( int cloud = 0; cloud < width; cloud += 150) 
   {    noStroke();
        fill(225);
        ellipse(cloud+20, 130, 40,45);
        ellipse(cloud+10, 150, 80,35);
        ellipse(cloud+30, 150, 70,50);  }
 }
  
 //Grass 
void grass() { 
   stroke(14,118,20);
   strokeWeight(3);
   
 int grassX = 0;

  while(grassX < width) {
    if (count/45 % 2== 0) {
      line(grassX+10,600,grassX,height-50) ;
    }else {
       line(grassX-10,600,grassX,height-50);
    }
        grassX = grassX+10; 
   }
 }
//// HANDLERS:  keys & clicks.
void keyPressed() {
   if (key == 'b') { p.drop();  }
   if (key == 'r') { reset();}
   if (key == 'w') { wall=!true;}
   if (key == 'q') { exit();  }
   if (key == 'p') { pooltableR=252;  pooltableG=176; pooltableB= 235; }
   /*if ( key =='m' ){ going = true ; 
   } else { going = false; }*/
 }
