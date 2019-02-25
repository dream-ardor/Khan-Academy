## Challenge: Fire starter

**Add an initial system**

This program creates new particle systems once the user clicks, and you're going to make those systems look like fire in this challenge. However, it'll be a lot easier to see your changes if your program starts off with at least one system, so you don't have to keep clicking. Do that now.

## Solution
```js
angleMode = "radians";

var Particle = function(position) {
this.acceleration = new PVector(0, -0.06);
this.velocity = new PVector(random(1, 1), random(-9, 0));
this.position = position.get();
this.timeToLive = 100;
};

Particle.prototype.run = function() {
this.update();
this.display();
};

Particle.prototype.update = function(){
this.velocity.add(this.acceleration);
this.position.add(this.velocity);
this.timeToLive -= 2;
};

Particle.prototype.display = function() {
colorMode(HSB);
noStroke();
var hue = constrain((100 - this.timeToLive)/2,0,40);
fill(hue, 255, 255, this.timeToLive);
ellipse(this.position.x, this.position.y, 12, 12);
};

Particle.prototype.isDead = function() {
if (this.timeToLive < 0) {
return true;
} else {
return false;
}
};

var ParticleSystem = function(position) {
this.origin = position.get();
this.particles = [];
};

ParticleSystem.prototype.addParticle = function() {
this.particles.push(new Particle(this.origin));
};

ParticleSystem.prototype.run = function() {
for (var i = this.particles.length-1; i >= 0; i--) {
var p = this.particles[i];

var p = this.particles[i];

try { // Let's try, but don't freak out if it fails
p.run(); // Trying to run particle
} catch (e) { // Dammit, something went wrong
throw ({ // Hack Oh Noes and tell the user
message: "Make sure the values you pass to the fill() function are always positive. " + e
});
}

if (p.isDead()) {
this.particles.splice(i, 1);
}
}
};

// We start off with an empty systems array
var systems = [];
systems.push(new ParticleSystem(new PVector(width/2, height/2)));
// We fill up the leaves array with positions
var leaves = [];
for (var i = 0; i < 100; i++) {
leaves.push(new PVector(random(0, width), random(0, height)));
}

mouseClicked = function() {
systems.push(new ParticleSystem(new PVector(mouseX, mouseY)));
};

draw = function() {
colorMode(RGB);
background(66, 57, 11);

for (var i = 0; i < leaves.length; i++) {
image(getImage("avatars/leaf-orange"), leaves[i].x, leaves[i].y, 30, 30);
}
for (var i = 0; i < systems.length; i++){
systems[i].addParticle();
systems[i].run();
}
};
mouseDragged = function () {
systems.push(new ParticleSystem(new PVector(mouseX, mouseY)));
};
```
