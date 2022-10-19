---
title: Tutorials
hide: 
  -navigation
---

# Overview

## Scene Generation with Blender
    Not yet ready. 

## Platforms
![type:video](./content/platform_design.mp4)![type:video](./content/platform_design2.mp4)

Now that the scene is generated, it is time to add some sensors, but before that, we must specify platform objects. Platform objects are the parent objects where sensors are embedded, e.g. vehicles, drones, etc. It could be a fixed object with no trajectory(i.e. static), a dynamic object with a trajectory imported from outside or an actor(dynamic object inside the scene). Regardless, a platform with a known trajectory must be created before creating any sensors.

## Sensors 
[slide-22-image.jpg]
With platform/platforms ready, sensors could now be created. The process is very similar to creating platforms; a location and orientation with respect to the platform must be provided. For e.g., if the sensor is placed at the platform's centre, the location must be (0, 0, 0). Remaining parameters like PRF, Scanning frequency, Channels, etc., are generic to the lidars sensors and can be copied as it is from the specification manual of the sensor.

## Cameras 
[slide-23-image.jpg]
Adding a camera sensor is just the same as adding a lidar sensor with camera-specific parameters like focal length, iso, etc.

## Limulate! 
[slide-25-image.jpg]
This is where the magic happens. But before that note, a standard dynamic model in  Blender runs at 30fps, but the laser works on 2k-800k Hz. Rendering a simulation at such low fps will throw out almost all the information and will be useless. Hence, the animation is scaled to level it to the sensors.

[slide-17-image.jpg]

The remaining part is straightforward. A laser is created at each frame for every sensor, and intersection with model objects is computed using ray casting. If the calculated distance exceeds the sensor max range, it is discarded; otherwise, we label the attribute and store the location of the intersection point in our point cloud.

## Test Platform 
