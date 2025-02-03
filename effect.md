# Particle Effects Documentation

## Overview
This documentation provides a comprehensive guide to creating and manipulating particle effects using various emitters and settings. The system allows for the creation of complex visual effects by controlling particle behavior, appearance, and interaction with the environment.

## Effect Settings

### `<effect>`
- **useentityeffectscale**: `true, false` (0, 1)  
  Should be used for global effects applied to multiple heroes (e.g., `state.effect`, `impact.effect`).
- **deferred**: `true, false` (0, 1)  
  Allows sprites to fade correctly.
- **persistent**: `true, false` (0, 1)  
  Allows emitters to finish emitting even after the gadget/entity is terminated. Note: If persistent is set to true, ensure all emitters have a life or count.

## Particle System

### `<particlesystem>`
- **name**: Used to name your particle systems. Typically named `system0` or `system1`, but any name can be used. Ensure it is called correctly in the `spawnparticlesystem` tag.
- **space**: Set to `world` or `entity`. If set to `entity`, the emitter stays with the hero. Set to `world` if you want particles to drag or be left behind.
- **scale**: Can be set to any value (e.g., 1, 50, 0.2). It's cleaner to set it to 1.

## Particle

### `<particle>`
- **color**: Three numbers representing RGB (e.g., `color="1 1 1"`).
- **alpha**: Ranges from 0-1 (e.g., `alpha=".5"` means 50% transparency).
- **size**: Used to set the sprite size. Use `startsize`, `midsize`, and `endsize` for variety.
- **width**: Changes the width of the sprite, leaving the height unchanged.
- **height**: Changes the height of the sprite, leaving the width unchanged.
- **scale**: Can be set to any value (e.g., 1, 50, 0.5). Use `startscale`, `midscale`, and `endscale` for variety.
- **pitch**: Rotates the sprite along the X-axis. Typically used with `lockup` and `lockright` set to true, and pitch set to 90 to make the sprite flat.
- **yaw**: Rotates the sprite along the Z-axis.
- **roll**: Rotates the sprite along the Y-axis. Speed can be added to `yaw`, `pitch`, and `roll` to make the sprite spin.
- **frame**: Used for animated sprites (e.g., `startframe="0"`, `endframe="1"`). `framespeed` controls the animation speed.
- **param**: Used for refraction sprites. Sets the strength of refraction (e.g., `param=".1"` to `param="1"`).
- **stickiness**: Similar to `anchor`. Typically, use `anchor` instead.
- **anchor**: Keeps the sprite anchored to the bone it is called on.
- **widthdistort**: Distorts the width only.
- **heightdistort**: Distorts the height only.
- **scaleu**: Scales along the U in UV.
- **scalev**: Scales along the V in UV.
- **offsetu**: Offsets the sprite along the U direction.
- **offsetv**: Offsets the sprite along the V direction.
- **weight**: Rarely used; functionality uncertain.
- **lockup**: `true, false` (0, 1) Locks the sprite up.
- **lockright**: `true, false` (0, 1) Locks the sprite right.
- **turn**: `true, false` (0, 1) Allows sprites to turn with the entity.
- **flare**: `true, false` (0, 1)
- **emitter**: Calls an emitter inside another emitter by name.

**Note**: Most settings in the `<particle>` tag can use `start`, `mid`, and `end` settings (e.g., `startcolor="1 1 1"`, `midcolor="1 0 1"`, `endcolor="1 0 0"`). Control when the mid setting hits with `midcolorpos`.

## Emitters

### `<simpleemitter>`
- **owner**: Used to add emitters to models by name.
- **life**: Lifetime in milliseconds (e.g., `life="5000"` for 5 seconds).
- **count**: Controls the number of sprites emitted (e.g., `count="5"` emits 5 sprites).
- **timenudge**: Older setting; use `delay` instead.
- **delay**: Delays the emitting of sprites in milliseconds (e.g., `delay="2000"` for 2 seconds).
- **loop**: `true, false` (0, 1) Loops the emitter.
- **spawnrate**: Number of particles emitted per second (e.g., `spawnrate="25"` emits 25 sprites per second).
- **particlelife**: Lifetime of particles in milliseconds.
- **particledirectionspace**: `global` or `local`. Local uses the bone's local axis.
- **gravity**: Strength of gravity. Negative values go up, positive values go down.
- **speed**: Speed at which particles move.
- **acceleration**: Particles pick up speed over time.
- **minangle**, **maxangle**: Creates an emission window in degrees.
- **inheritvelocity**: Emitter inherits the velocity of an object.
- **material**: Path to the sprite material (e.g., `material="/shared/effects/materials/mySprite.material"`).
- **direction**: Direction in X, Y, Z (e.g., `direction="0 0 1"`).
- **directionalspace**: `global`, `local`, or `world`.
- **drag**: Slows down particles as if moving through a thick substance.
- **friction**: Decelerates particles over time.
- **bone**: Emits from a specific bone.
- **position**: Position in X, Y, Z (e.g., `position="0 0 50"`).
- **offsetsphere**: Emits from within a sphere (e.g., `offsetsphere="100 100 100"`).
- **offsetcube**: Emits from within a cube.
- **offsetdirection**: Adds depth to the emitter.
- **offsetradial**: Emits along the circumference of a circle.
- **offsetradialangle**: Creates a cone shape from the origin.
- **collide**: `true, false` (0, 1) Particles collide with the ground.
- **subframepose**: `true, false` (0, 1) Used with trail emitters.

### `<orbiteremitter>`
- Similar to `<simpleemitter>` but with additional settings for orbiting particles.
- **orbit**: Speed of orbiting particles. Positive values rotate counter-clockwise, negative values rotate clockwise.

### `<trackeremitter>`
- Similar to `<simpleemitter>` but with additional settings for tracking particles.
- **tracktype**: `distance`, `angular`, `gravity`, `cgravity`, `target`, `lerp`.
- **trackspeed**: Typically set to 1.
- **distancelife**: `true, false` (0, 1) Particles die upon reaching the target.

### `<meshemitter>`
- **mesh**: Name of the mesh the emitter emits from.
- Similar to `<simpleemitter>` but emits from a mesh.

### `<skeletonemitter>`
- Similar to `<simpleemitter>` but emits from a skeleton.

### `<twopointtrailemitter>`
- Similar to `<simpleemitter>` but with two points for trail effects.
- **bone_a**, **bone_b**: Bones for the trail points.
- **position_a**, **position_b**: Positions for the trail points.
- **texpostime**: Should match `particlelife`.
- **texposscale**: Typically set to 0.
- **texstretchscale**: Typically set to 1.

### `<trailemitter>`
- Similar to `<twopointtrailemitter>` but with a single trail point.
- **bone**: Bone for the trail point.
- **position**: Position for the trail point.

## Light

### `<light>`
- **owner**: Adds lights to models by name.
- **life**: Lifetime in milliseconds.
- **delay**: Delays the light from showing up.
- **loop**: `true, false` (0, 1) Loops the light.
- **bone**: Bone the light is attached to.
- **position**: Position in X, Y, Z.
- **color**: RGB values (e.g., `color="1 1 1"`).
- **falloffstart**, **falloffend**: Controls light falloff.

**Note**: Only 4 lights can be active on the screen at once.

## Beam

### `<beam>`
- **owner_a**, **owner_b**: Ends of the beam.
- **bone_a**, **bone_b**: Bones for the beam ends.
- **position_a**, **position_b**: Positions for the beam ends.
- **life**: Lifetime in milliseconds.
- **delay**: Delays the beam from showing up.
- **loop**: `true, false` (0, 1) Loops the beam.
- **color**: RGB values.
- **alpha**: Transparency (0-1).
- **size**: Controls the size of the beam.
- **tile**: Repeats the sprite along the beam.
- **frame**: Used for animated sprites.
- **param**: Used for refraction sprites.
- **material**: Path to the sprite material.

## Ground Sprite

### `<groundsprite>`
- **owner**: Adds ground sprites to models by name.
- **bone**: Bone the ground sprite is attached to.
- **position**: Position in X, Y (Z is insignificant).
- **life**: Lifetime in milliseconds.
- **delay**: Delays the ground sprite from showing up.
- **loop**: `true, false` (0, 1) Loops the ground sprite.
- **color**: RGB values.
- **alpha**: Transparency (0-1).
- **size**: Controls the size of the ground sprite.
- **width**: Changes the width of the ground sprite.
- **height**: Changes the height of the ground sprite.
- **scale**: Controls the scale of the ground sprite.
- **frame**: Used for animated ground sprites.
- **param**: Used for refraction sprites.
- **material**: Path to the sprite material.

**Note**: Ground sprites are resource-intensive, especially when large or stacked.

## Billboard

### `<billboard>`
- **owner**: Adds billboards to models by name.
- **life**: Lifetime in milliseconds.
- **delay**: Delays the billboard from showing up.
- **loop**: `true, false` (0, 1) Loops the billboard.
- **bone**: Bone the billboard is attached to.
- **position**: Position in X, Y, Z.
- **color**: RGB values.
- **alpha**: Transparency (0-1).
- **pitch**, **yaw**, **roll**: Rotates the billboard.
- **size**: Controls the size of the billboard.
- **width**: Changes the width of the billboard.
- **height**: Changes the height of the billboard.
- **scale**: Controls the scale of the billboard.
- **frame**: Used for animated billboards.
- **param**: Used for refraction sprites.
- **depthbias**: Adjusts the sprite's distance from the camera.
- **lockup**, **lockright**: Locks the sprite's orientation.
- **turn**: Allows sprites to turn with the entity.
- **flare**: `true, false` (0, 1)
- **material**: Path to the sprite material.
- **directionalspace**: `global`, `local`, or `world`.

## Model

### `<model>`
- **name**: Names the model.
- **owner**: Adds models to other models by name.
- **life**: Lifetime in milliseconds.
- **delay**: Delays the model from showing up.
- **loop**: `true, false` (0, 1) Loops the model.
- **directionalspace**: `global`, `local`, or `world`.
- **bone**: Bone the model is attached to.
- **position**: Position in X, Y, Z.
- **color**: RGB values.
- **alpha**: Transparency (0-1).
- **pitch**, **yaw**, **roll**: Rotates the model.
- **scale**: Controls the scale of the model.
- **model**: Path to the model (e.g., `model="model/model.mdf"`).

---
