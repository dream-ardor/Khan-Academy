## Challenge: Magical cauldron

Add smoke!

This program animates a standard particle system emerging out of a cauldron. We want different sorts of particles to come out of the cauldron, though, starting with a smokey particle. Create a Smoke object that inherits from Particle, but looks more like colored smoke.

Add stars!

Now, make a new kind of particle come out of the cauldron - stars! Like you did for the Smoke, you should inherit from the Particle object, but change the display. You can just use the star image from our image library, to avoid having to draw a star yourself.

Show stars and smoke

Now, we want the particle system to emit both smoke and stars, about equally. Use the random probability technique to decide which particle type to add, when addParticle is called.

Different sized stars!

Make your star particles more interesting by varying their size- generate a random size for each, and use that to draw the star. Be reasonable now!

## Solution
```js
angleMode = "radians";

var Particle = function(position) {
    this.acceleration = new PVector(0, -0.05);
    this.velocity = new PVector(random(-1, 1), random(0, -1));
    this.position = position.get();
    this.timeToLive = 255.0;
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
    stroke(0, 0, 0, this.timeToLive);
    strokeWeight(2);
    fill(255, 0, 0, this.timeToLive);
    ellipse(this.position.x, this.position.y, 12, 12);
};

Particle.prototype.isDead = function(){
    if (this.timeToLive < 0) {
        return true;
    } else {
        return false;
    }
};

var Smoke = function(position){
    Particle.call(this, position);
};

//creating smoke object with same prototypes as particle
Smoke.prototype = Object.create(Particle.prototype);
Smoke.constructor = Smoke;

//displaying smoke
Smoke.prototype.display = function(){
    noStroke();
    fill(60, 61, 61, this.timeToLive);
    ellipse(this.position.x, this.position.y, 17, 17);
};

var Star = function(position){
    Particle.call(this, position);
    this.size = random(6,9);
 
};

Star.prototype = Object.create(Particle.prototype);

Star.prototype.display = function(){
    var m = getImage("cute/Star");
    image(getImage("cute/Star"), this.position.x, this.position.y, (this.size * m.width) / 60, (this.size * m.height) / 80);
};

var ParticleSystem = function(position) {
    this.origin = position.get();
    this.particles = [];
};

//randomly adding smoke and star particles
ParticleSystem.prototype.addParticle = function() {
    var r = random(1);
    if (r < 0.5){
        //add smoke particles
        this.particles.push(new Smoke(this.origin));
    }
    else {
        //add star particles
        this.particles.push(new Star(this.origin));
    }
};

ParticleSystem.prototype.run = function(){
	for (var i = this.particles.length-1; i >= 0; i--) {
    var p = this.particles[i];
    p.run();
    if (p.isDead()) {
        this.particles.splice(i, 1);
    }
  }
};

var particleSystem = new ParticleSystem(new PVector(width/2, 280));

draw = function() {
    background(72, 7, 105);
    particleSystem.addParticle();
    particleSystem.run();
  
    // The magical cauldron
    fill(36, 36, 36);
    var cauldronX1 = 150;
    var cauldronX2 = 250;
    var cauldronY = 285;
    bezier(cauldronX1, cauldronY,
           cauldronX1-100, cauldronY+145,
           cauldronX2+100, cauldronY+145,
           cauldronX2, cauldronY);
};
```
