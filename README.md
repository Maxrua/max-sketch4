var x,y;
var m;
var a=1600;
var n;
class mover{
constructor(){
  createCanvas(800, 800);
  background(255,0,0);
  this.position = createVector(150, 100);
  this.velocity = createVector(0.5, 2);
  this.acceleration = createVector(-0.1, 0.01);
	this.topspeed = 50;
}
	/*background(255,0,0);
  position.add(velocity);
  if ((position.x > 150) || (position.x < 50)) {
    velocity.x = velocity.x * -1;
  }
  if ((position.y > 375) || (position.y < 50)) {
    velocity.y = velocity.y * -1;
  }*/
		applyForce(force){
		let f=p5.Vector.div(force, this.mass);
		this.acceleration.add(f);}
	update(){
	 // var mouse = createVector(mouseX, mouseY);
		//this.acceleration = p5.Vector.sub(mouse,this.position);
		 this.acceleration.setMag(0.2);
		this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);
		this.position.add(this.velocity);
	}
 display(){

	 background (150,0,0);
	 fill(175);
  strokeWeight(5);
  stroke(204,0,0);  
  ellipse(300+this.position.y,this.position.x+100, 100, 100);
  ellipse(500+this.position.y,this.position.x+100, 100, 100);
  fill(255);
  ellipse(300+this.position.y,this.position.x+100, 20, 20);
  ellipse(500+this.position.y,this.position.x+100, 20, 20);
  fill(204,0,0);
  triangle(225+this.position.y, 450-this.position.x, 375+this.position.y, 375+this.position.x, 375+this.position.y, 275+this.position.x);
  triangle(375+this.position.y, 375+this.position.x, 375+this.position.y, 275+this.position.x, 525+this.position.y, 450-this.position.x);
	 for (var i=0;i<=5*1600;i++) {
      stroke(random(0,175));
      x = random(0,a);
      y = random(0,a);
      line(x,y,x+random(0,20),y);
  }
  stroke(100,100);
  line(0,n,a,n);
  n++;
  if (n>a) {
    n=0;
  }
  stroke(100,100);
  line(0,m,a,m);
  m++;
  if (m>a) {
    m=0;}
 }
	 /*var v0 = createVector(300+this.position.y, this.position.x+100);
  
	var v1 = p5.Vector.random2D();
	
  drawArrow(v0, v1.mult(50), 'white');
 
}
 drawArrow(base, vec, myColor) {
  push();
  stroke(myColor);
  strokeWeight(4);
  fill(myColor);
  translate(base.x, base.y);
  line(0, 0, vec.x, vec.y);
  rotate(vec.heading());
  var arrowSize = 7;
  translate(vec.mag() - arrowSize, 0);
  triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
  pop();}
	*/

	checkEdges(){
	 if ((this.position.x > width/2) || (this.position.x < 0)) {
    this.velocity.x = this.velocity.x * -1;
  }
 if ((this.position.y > 300 ) || (this.position.y < 0)) {
    this.velocity.y = this.velocity.y * -1;}
}	
}
	 /* var v0 = createVector(300+position.y, position.x+100);
  
	var v1 = p5.Vector.random2D();
	
  drawArrow(v0, v1.mult(50), 'white');
 
}
  drawArrow(base, vec, myColor) {
  push();
  stroke(myColor);
  strokeWeight(4);
  fill(myColor);
  translate(base.x, base.y);
  line(0, 0, vec.x, vec.y);
  rotate(vec.heading());
  var arrowSize = 7;
  translate(vec.mag() - arrowSize, 0);
  triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
  pop();}*/
	
	
	
	
	
	
	
let Mover;

function setup() {
  createCanvas(800, 800);
  Mover = new mover();
}

function draw() {
  background(51);

 Mover.update();
  Mover.display();
  Mover.checkEdges();
}
	
